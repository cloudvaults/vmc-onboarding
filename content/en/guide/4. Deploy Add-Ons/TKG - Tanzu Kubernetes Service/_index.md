---
title: "TKG - Tanzu Kubernetes Service"
linkTitle: "TKG - Tanzu Kubernetes Service"
weight: 3
date: 2022-03-28
description: >
  How to Activate and install Tanzu Kubernetes for VMware Cloud on AWS 
---

## Introduction

VMware recently added a service to VMware Cloud on AWS that allows you to run container workloads on the same hosts and infrastructure as your VM's. This new service is easy to install and uses the latest industry standard distribution of Kubernetes.

## What is Tanzu Kubernetes Grid Serivce?

A service architecture built into VMC on AWS that alllows you to easily deploy, manange and upgrade Kubernetes clusters on vSphere. Installation takes minutes vs. hours deploying Kubernetes from source code. 

## Before you begin you will need 3 free CIDR blocks for the installation
For more information please watch the following video: 
<iframe width="560" height="315" src="https://www.youtube.com/embed/SEUhlr0TzUc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Tanzu Service Activation

### 1. On a fully deployed and configured SDDC, click to Activate the Tanzu Kubernetes Service

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/once-the-sddc-is-deployed-and-setup--login-and-click-to-activate-tanzu-kubernetes-service.jpg)


 
### 2. Enter CIDR blocks as shown
1.	Enter a namespace Network CIDR, this should be an available CIDR block that is not used already on-prem or in the SDDC
2.	Enter an Ingress CIDR, this should be an available CIDR block that is not used already on-prem on in the SDDC
3.	Enter an Egress CIDR, this should be an available CIDR block that is not used already on-prem on in the SDDC
4.	Click to Validate and Proceed

Leave the Service CIDR as default

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/enter-cidr-blocks-as-shown.jpg)


 
### 3. Click to Activate Tanzu Kubernetes Grid
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/if-all-passes--click-to-activate-tanzu-kubernetes-grid.jpg) 

{{< notice info >}}
**Please Note!**\
If you get any errors that a CIDR block is not valid, please ensure that it is not an address that is already in use on the management network. 
{{< /notice >}}
 


### 4. You will now see the status of the SDDC change to Activating Tanzu Kubernetes Grid
It should take about 15-20 min. This might be a good time to go grab another cup of coffee. 

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/you-should-now-see-status-activating-tanzu-kubernetes-grid.jpg) 

{{< notice info >}}
**Note!**\
If you see a notice that Tanzu Kubernetes Activation has failed go back to step 4 and try again. If it fails a third time you can try to delete the SDDC and deploy again or open a ticket with Support to investigate.
{{< /notice >}}

### 5. In a few minutes, check vCenter as shown below and you will see the supervisor cluster provisioning
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/in-vcenter-you-should-also-see-the-supervisor-cluster-provisioning-.jpg) 

### 6. When activation is complete, go to Workload Management in vCenter
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/once-complete--go-to-workload-management.jpg)
### 7. Click create Namespace
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/click-create-namesapce.jpg)
 
### 8. Enter a name for your namespace
1.	Enter a valid namespace name,  all namespace names must be valid RFC 1123 DNS labels.
2.	Click create
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/enter-a-name-for-your-namespace.jpg)


{{< notice warning >}}
**Please Note!**\
If you want to add a description there is a known bug if you use a ! in the text for the description and later in step 37 of this guide your TKC cluster deployment will fail. 
{{< /notice >}}
 
### 9. Configure each of the tiles starting with the Permissions tile
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/configure-each-of-the-tiles-.jpg)
### 10. Add cloudadmin from vmc.local as Owner
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/add-cloudadmin-from-vmclocal-as-owner.jpg)
### 11. Click Add Storage
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/click-add-storage.jpg)
### 12. Select the VMC Workload Storage Policy
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/select-the-vmc-workload-storage-policy.jpg)
### 13. Click to add VM Class
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/click-to-add-vm-class.jpg)
### 14. Click to select all and click Ok
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/click-to-select-all-and-click-ok-.jpg)
### 15. Copy the url to the supervisor cluster
Click and copy this link to notepad, we will use it later during the install 
It should looks something like this: 

https://k8s.Cluster-1.vcenter.sddc-10-180-21-15.vmwarevmc.com

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-grab-the-url-to-the-supervisor-cluster.jpg)
 
### 16. Go back to Inventory
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-go-back-to-inventory-.jpg)
### 17. To complete the next steps, we will need to deploy a Linux based workstation to complete the deployment as well as deploy a test application
1.	Right click on Cluster-1
2. click Deploy OVF Template

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-we-will-need-to-deploy-a-linux-based-workstation-to-complete-the-depmloyment-as-well-as-deploy-a.jpg)

### 18. Enter the following URL and click Next
<pre>https://packages.vmware.com/photon/4.0/Rev2/ova/photon-ova-4.0-c001795b80.ova</pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/enter-the-following-url-and-click-next-.jpg)


### 19. Click Yes
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/click-ok-.jpg)

### 20. Enter a name
1.	Enter a name for your jumphost
2.	Select the workloads folder
3.	Click next
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/enter-name--select-workloads-folder-and-click-next-.jpg)

### 21. Select Compute-ResourcePool and click Next
1.	Select the Compute Resource Pool
2.	Click next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/select-compute-resourcepool-and-click-next-.jpg)

 
### 22. Click Next
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/click-next-.jpg)
 
### 23. Accept and click next
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/accept-and-click-next.jpg)
### 24. Choose WorkloadDatastore
1.	Choose the Workloads Datastore
2.	Click next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/choose-workloaddatastore-and-click-next-.jpg)

 
### 25. Select Networks
1.	Select an available and accessible SDDC network
2.	Click next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/select-an-available-sddc-network-and-click-next.jpg)

 
### 26. Click Finish
 ![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/click-finish.jpg)
### 27. When the new VM is provisioned, power it on and and ssh to it
User: root

Password: changeme

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/once-the-new-vm-is-provisioned-go-ahead-and-ssh-to-it-.jpg)

 
### 28. To complete the installation we will need to install a couple services, enter the following and press enter
<pre>tdnf install -y wget unzip</pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-download-a-couple-things-we-will-need--enter-the-following-and-press-enter.jpg)


 
### 29. Download the command line tools from vCenter, make sure the item below in red is changed to your supervisor cluster address that you copied earlier
<pre>wget https://<font color="red">k8s.cluster-1.vcenter.sddc-10-180-20-102.vmwarevmc.com</font>/wcp/plugin/linux-amd64/vsphere-plugin.zip</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-grab-the-command-line-tools--make-sure-the-item-below-in-red-is-changed-to-your-supervisor.jpg)


 
### 30.  Upzip that file by typing the following and press enter
<pre>unzip vsphere-plugin.zip -d /usr/</pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-upzip-that-file-tyoe-the-following-and-press-enter.jpg)


 
### 31. Login to the supervisor cluster by entering the following and changing the item in red to your cluster name we used earlier and press enter, enter the password for cloudadmin to complete the login
<pre>kubectl vsphere login --vsphere-username cloudadmin@vmc.local --server=<font color="red">k8s.cluster-1.vcenter.sddc-10-180-21-15.vmwarevmc.com</font></pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-login-to-the-supervisor-cluster--enter-the-following-changing-the-item-in-red-to-your-clus.jpg)


 
### 32. Change to the namespace you created earlier in vCenter, type the following, change the item in red to your namespace name and press enter
<pre>kubectl config use-context <font color="red">rkelly</font></pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-change-to-the-namespace-we-created-in-vcenter--type-the-following--change-the-item-in-red-.jpg)


 
### 33. Leave the ssh session open and switch over to Tanzu Mission Control to deploy the TKC cluster
1.	Click the waffle tab
2.	Click VMWare Tanzu Mission Control

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-we-are-ready-to-switch-over-to-tanzu-mission-control-to-deploy-the-tkc-cluster.jpg)

 
### 34. Add your SDDC to Tanzu Mission Control
1.	Select Administration
2.	Select Management Clusters
3.	Click Register Management Cluster
4.	Select vSphere with Tanzu

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/let-s-add-your-sddc-to-tanzu-mission-control-.jpg)

 
### 35. Enter a name for the new Management Cluster
1.	Enter the SDDC name
2.	change to default
3.	Click Next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/enter-a-name-for-the-new-management-cluster.jpg)
 
### 36. Accept defaults
Click next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/accept-defaults.png)

 
### 37. Copy the registration link to notepad, you will use it in the next steps
Once copied click View Management Cluster

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/copy-the-registration-link-to-notepad--we-will-use-it-in-the-next-steps.jpg)

 
### 38. Go back to your Linux machine we configured earlier and type the following and press enter
<pre>kubectl get ns</pre>
Copy the svc-tmc-## to your notepad, you will use this in the next step

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/go-back-to-your-linux-machine-we-configured-earlier-and-type-the-following-and-press-enter.jpg)

 
 
### 39. Create a new Tanzu Mission Control registration yaml file by typing the following and pressing enter
<pre>vi tmc-registration.yaml</pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/create-a-new-tanzu-mission-control-registration-yaml-file-by-typing-the-following-and-pressing-enter.jpg)


 
### 40. Press i and then paste the following into the file changing items in Red to the names we copied to your notepad earlier, press esc key then hold shift and pres z z to save it
<pre><code>apiVersion: installers.tmc.cloud.vmware.com/v1alpha1
kind: AgentInstall
metadata:
  name: tmc-agent-installer-config
  namespace: <font color="red">TMC-NAMESPACE</font>
spec:
  operation: INSTALL
  registrationLink: <font color="red">TMC-REGISTRATION-URL</font></code></pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/press-i-and-paste-the-following-into-the-file-changing-the-items-in-red-to-the-items-we-copied-to-yo.jpg)


 
### 41. Type the following and press enter
<pre>kubectl create -f tmc-registration.yaml</pre>

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-type-the-following-and-press-enter.jpg)


 
### 42. Go back to Tanzu Mission Control and after a few minutes you should see your Supervisor cluster ready
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-go-back-to-tanzu-mission-control-and-after-a-few-minutes-you-should-see-your-supervisor-cluster-.jpg)
 
### 43. You are now ready to deploy your TKC cluster so you can deploy containers
1.	Select Clusters
2.	Click Create Cluster

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/we-are-now-ready-to-deploy-or-tkc-cluster-so-we-can-deploy-conatiners.jpg)

 
### 44. Select your Management Cluster we just configured
1.	Select the Supervisor Cluster we just configured
2.	Click Continue to Create Cluster

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/select-your-management-cluster-we-just-configured.jpg)

 
### 45. Select your namespace as Provisioner and click next
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/select-your-namespace-as-provisioner-and-click-next.jpg)
 
### 46. Enter a name for the new cluster
1.	Enter a cluster name using yournamespace-tkc1  for example rkelly-tkc1
2.	Select Default for Cluster Group
3.	Click next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/enter-a-name-for-the-new-cluster.jpg)

 
### 47. Keep all defaults here but select a storage class
1.	Select the Workload-Storage Policy
2.	Click Next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/keep-all-defaults-here-but-select-a-storage-class-.jpg)

 
### 48. Select Control Plane size
1.	Choose Single Node
2.	Choose the instance type
3.	Click Next

![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/select-control-plane-size-and-click-next.jpg)

 
### 49. Keep defaults and click Create Cluster
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/keep-defaults-and-click-create-cluster.jpg)
 
### 50. It takes several minutes but if you go to your namespace in vCenter you should see it start to deploy the cluster
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/it-takes-several-minutes-but-if-you-go-to-your-namespace-in-vcenter-you-should-see-it-start-to-deplo.jpg)

{{< notice info >}}
**Note!**\
If it does not start to deploy or does not deploy after 20 minutes go back to Tanzu Mission Control and deactivate the cluster and try agin. If it still does not deploy please review the previous steps for accuracy or contact Support for help. 
{{< /notice >}}
 
### 51. Once complete you will see it as healthy in Tanzu Mission Control
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/once-complete-you-should-see-it-as-healthy-in-tanzu-mission-control-.jpg)
 
### 52. Go back to your Linux machine and deploy a container. 
First, you need to login again and specify the TKC cluster you just created, enter the following after you edit the items in red to your environment and press enter, then enter the cloudadmin@vmc.local password when prompted 

<pre><code>kubectl-vsphere login --server=<font color="red">k8s.cluster-1.vcenter.sddc-10-182-162-186.vmwarevmc.com -u cloudadmin@vmc.local</font> \
--tanzu-kubernetes-cluster-name <font color="red">rkelly-tkc1</font> \
--tanzu-kubernetes-cluster-namespace <font color="red">rkelly</font></code></pre>



![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-go-back-to-your-linux-machine-and-deploy-a-container-first-we-need-to-login-again-and-spec.jpg)


 
### 53. Change context to the TKC cluster, again making sure you change the item in red to your TKC cluster name
<pre>kubectl config use-context rkelly-tkc1</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-change-context-to-the-tkc-cluster-again-change-the-item-in-red-to-your-tkc-cluster-name.jpg)


 
### 54. Create a new name space in the cluster, type the following and press enter
<pre>kubectl create ns poc</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-create-a-new-name-space-in-the-cluster--type-the-following-and-press-enter.jpg)


 
### 55. List the namespaces with the following command
<pre>kubectl get ns</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-list-the-namespaces-with-the-following-command.jpg)


 
### 56. Change to that namespace with the following command
<pre>kubectl config set-context --current --namespace=poc</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-change-to-that-namespace-with-the-folloing-command.jpg)


 
### 57. Before we deploy a container we need to disable some old Kubernetes security features with the following command
<pre>kubectl apply -f https://raw.githubusercontent.com/vmtocloud/tanzuonvmc/main/disable-psp.yaml</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-before-we-deploy-a-container-we-need-to-disable-some-old-kubernetes-security-features-with-the-f.jpg)


 
### 58. Deploy a container with the following command
<pre>kubectl create deployment --image=public.ecr.aws/m0z6y2h1/nginx:latest nginx --port=80</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-we-can-deploy-a-container-with-the-following-command.jpg)


 
### 59. Check the status of the deployment with the following command
<pre>kubectl get deployments</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-check-the-status-of-the-deployment-with-the-following-command.jpg)


 
### 60. When you get a Ready status , expose the deployment so you can access the container application with the following command
<pre>kubectl expose deployment nginx --type=LoadBalancer --name=nginx-service</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/it-looks-good-so-now-let-s-expose-the-deployment-so-we-can-open-the-web-page-with-the-following-comm.jpg)


 
### 61. Get the IP address of the Web Server of this container with the following command
<pre>kubectl describe services nginx-service</pre>
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-get-the-ip-address-of-the-web-server-of-this-container-with-the-following-command.jpg)

Copy that IP to the clipboard for the next step

 
### 62. Check that the site is up by typing the following command changing the Item in red to your Load Balancer ingress IP you copied earlier
<pre>wget http://<font color="red">10.10.2.6</font></pre> 
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/now-let-s-check-it-is-up-by-typing-the-follwoing-command-with-that-load-balancer-ingress-ip.jpg)


 
### 63. You can also open a web browser to the same url to test it.
![NewActivation](https://vmc-onboarding-images.s3.us-west-2.amazonaws.com/4.Deploy-add-ons/tkg/you-can-also-open-a-web-browser-to-the-same-url-to-test-it-.jpg)
 


