In the following guide we will be configuring a basic website using an NGINX webserver and hosting it on Azure

## Outline
1. Creating a Virtual Machine on Azure
2. Loading dependencies from the command line
3. Configuring NGINX
4. Hosting a site
After these four steps we will have a basic and servicable static site that we can host whatever we choose on.

## Creating a Virtual Machine on Azure
Firstly, we need to open the Azure portal, the webapp from which you can control and manage all of your resources. For the purposes of this guide, we will assume you already have login credentials you can use. If not, speak to your institution or organisation and arrange to have a *non-critical*  azure account and subscription created for you. All this means is that as you are learning you will not accidentally interfere with any important resources.

> [!Hint] Resources in Azure
> You may see the term "resource" referred to throughout this guide. This is a simple term that Azure uses that simply refers to any deployable service or object in Azure.

Once on our homepage, click on "virtual machines" at the top of the page.
![[Pasted image 20230216171555.png]]
In the top left, select "create" and from the drop down click "Azure Virtual Machine". This will then take you to a configuration page with many many menus, not to worry however, most of these are not relevant to us for the time being. On the first page, change these following settings:

**Resource Group.** Click on create new and then enter a name, like "myTestingGroup". All a resource group is, is a way to collect similar or associated resources into one easily manageable place.
**Virtual Machine Name.** Simply type in any name that you would like for your machine, "myFirstVM" will do fine if you can't choose.
**Region.** This decides where your machine will actually be located physically, however, its only practical impact for us is the cost and latency. For this reason, EastUS is the best choice, as the latency is tolerable and it has the cheapest servers.
**Availability Options.** This is all about the reliability of your resource. We're only testing, so select "No Infrastructure Redundancy Required".
**Image.** While you probably won't have to change anything, make sure it is selected on "Ubuntu Server 20.04 LTS - x64 Gen2"
**Size.** This decides the actual hardware capabilities of our VM. Select "Standard_B1ls - 1vcpu, 0.5GiB memory". This is the cheapest server possible, but it is more than enough for our demo site.
**Authentication Type.** This time around, we are going to be using a Password, however, typically if you were to SSH into a VM you would want to use the "SSH Public Key" option.
