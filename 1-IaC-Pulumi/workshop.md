# Intro to IaC with Pulumi: Workshop Instructions

Before starting this workshop, be sure to double-check [the prerequisites](prerequisites.md).

1. Create an empty directory in which to work, and then switch into this directory.
2. Run `pulumi new` to create a Pulumi project in this new directory. A Pulumi project corresponds to a directory with the files necessary to run a Pulumi program.
3. From the list of templates, select the AWS-YAML template. With the list of templates displayed from running `pulumi new`, type "yaml" and then use the arrow keys to select the desired template. This will create a minimal YAML document for use with Pulumi. When prompted, enter the AWS region you'd like to use ("us-west-2" will produce the lowest latency for Denver participants).
4. Open the YAML document in your editor. First, we'll add some code to create a VPC (replace everything under the `resources` key):
    ```yaml
    vpc:
      properties:
        cidrBlock: ${vpcNetworkCidr}
        enableDnsHostnames: true
      type: awsx:ec2:Vpc
    ```
5. We're referencing a value (`vpcNetworkCidr`), but we haven't defined it yet. Add this under a `config` key, adding the `config` key as needed:
    ```yaml
    vpcNetworkCidr:
      type: string
      default: 10.0.0.0/16
    ```
6. We haven't yet told Pulumi to _export_ any values when it's done running. Add this under the `outputs` key, replacing everything that's already there:
    ```yaml
    vpcId: ${vpc.vpcId}
    ```
7. Run `pulumi up`. The Pulumi engine will evaluate your YAML document and display a summary of what actions will be taken. Select Yes to proceed with the previewed actions.
8. After Pulumi has finished running (it will take about 3 minutes; the longest part is the NAT Gateways), run `pulumi stack`. This will show you all the resources created, the outputs (values exported from the program), and the URL to your stack on the Pulumi Service.
9. Open the URL displayed by the `pulumi stack` command and log in to the Pulumi Service. Here you can see the same information, but in a web-based format. The service also shows you history (although there really isn't any yet).
10. Back in your Pulumi YAML document, add this to the `resources` section:
    ```yaml
    cluster:
      properties:
        desiredCapacity: 3
        instanceType: t3.medium
        maxSize: 6
        minSize: 3
        nodeAssociatePublicIpAddress: false
        privateSubnetIds: ${vpc.privateSubnetIds}
        publicSubnetIds: ${vpc.publicSubnetIds}
        vpcId: ${vpc.vpcId}
      type: eks:Cluster
    ```
11. Add this to your `outputs`:
    ```yaml
    kubeconfig: ${cluster.kubeconfig}
    ```
12. Now run `pulumi up` again. This time, the preview won't indicate any changes to the VPC or related components, because they've already been created, and we haven't defined any changes to them. Select Yes to proceed.
13. When Pulumi is finished running (this will take a while, about 10 minutes), then run `pulumi stack` again to see all the new resources created.
14. Flip to your browser window where the Pulumi Service is running and refresh the page. You'll see the new resources, and you'll also see some of the history start to populate. This allows you to see changes to the state of your resources over time.
15. Run `pulumi stack output` to show _only_ the outputs.
16. If you have `kubectl` installed, you can access the Kubernetes cluster we just created by first getting the Kubeconfig created by Pulumi. Do this by running `pulumi stack output kubeconfig > cluster`.
17. Then run `KUBECONFIG=cluster kubectl get nodes`. You'll see a listing of three nodes returned.
18. Make a backup copy of your `Pulumi.yaml` file.
19. Run `pulumi convert --language typescript`. Pulumi will automatically convert your Pulumi YAML document into a TypeScript program.
20. Run `npm install` to install the TypeScript dependencies.
21. Run `pulumi up`. Pulumi will indicate that a couple of resources need to be updated, but for the most part all of your resources will remain intact. This illustrates Pulumi's language-independent engine.
22. Run step 17 again; `kubectl` will still work, and the same three nodes will be listed.
