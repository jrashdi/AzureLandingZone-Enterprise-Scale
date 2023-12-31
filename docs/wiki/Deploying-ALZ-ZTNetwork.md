## Azure landing zone portal accelerator deployment with Zero Trust network principles

This section describes how to deploy the Azure landing zone portal accelerator with a jump start on Zero Trust Networking Principles for Azure landing zones. For more information on Zero Trust security model and principles visit [Embrace proactive security with Zero Trust](/security/business/zero-trust). Let's review the [Zero Trust aligned networking](/security/zero-trust/deploy/networks) configurations in the [Azure landing zone portal accelerator](/azure/cloud-adoption-framework/ready/landing-zone/#azure-landing-zone-portal-accelerator).

## Deploy networking topology and Connectivity

On the "Network Topology and Connectivity" section of the Azure landing zone portal accelerator select "Hub and spoke with Azure Firewall" radio button. Next, Select the platform connectivity subscription from the drop down. Confirm or update the address space and first networking hub region, in this case East US.

![image](https://user-images.githubusercontent.com/8091766/228360733-9713f5ff-dd53-4995-b309-220442f978b5.png)

Hub and spoke is the primary topology option for Zero Trust Organizations.  These deployments should have traffic coming in to Azure, going between spokes, or leaving Azure be inspected and only permitted when explicitly allowed. Spoke networks should be segmented into smaller islands with their own ingress and egress controls in minimize "blast radius". 

## Enable Threat protection

In the next section you will want to leave the defaults to "Enable DDoS Network Protection" and "Deploy Azure Firewall" as these are pivotal requirements for threat protection. It's also recommended to select at least two availability zones for Azure Firewall, but ideally all 3, if the region has availability zone support.  

![image](https://user-images.githubusercontent.com/8091766/228363102-af09f069-c5f1-4be0-91e8-1050dc994bf9.png)

These selections help to segment and enforce external and internal boundaries. 

## Protect the Identity subscription

On the "Identity" section, ensure the default (Yes) is selected on "Prevent inbound RDP from internet" and "Ensure subnets are associated with NSG".

![image](https://user-images.githubusercontent.com/8091766/228366016-4eee4817-3885-491b-a064-7fdbaae9dc80.png)

Here we are enforcing network protection on resources in the identity subscription (like domain controllers) and what protocols can reach them with Network Security Groups.  The current deployment enforces NSGs, but does not have explicit allows, which would be managed post-deployment.

## Secure Application landing zones

On the "landing zones configuration" section ensure the default (Yes) is selected on:

"Enable DDoS Network Protection"

"Prevent usage of Public Endpoints for Azure PaaS services in the corp connected landing zones"

![image](https://user-images.githubusercontent.com/8091766/228368266-c9410af1-ab13-4de5-88fe-af74303edb81.png)

"Ensure subnets are associated with NSG"

"Prevent inbound RDP from internet"

![image](https://user-images.githubusercontent.com/8091766/228367470-7a46ea93-b57c-4586-946f-a89561e4eabb.png)

"Ensure secure connections (HTTPS) to storage accounts"

![image](https://user-images.githubusercontent.com/8091766/228367531-73377d39-f37d-4e9f-bab1-9f8de35b4702.png)

These configurations ensure that the spokes of our network hosting applications create service boundaries and protect them.
