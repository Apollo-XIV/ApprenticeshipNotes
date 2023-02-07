To create and use Azure services you need an azure subscription. One Azure account can be made to provide multiple subscriptions for different departments. From each of those subscriptions you can create and distribute resources.

## Azure Free Account
Azure allows free access to the Azure suite in the form of a free account on the following basis:
- Free access to popular Azure products for 12 months
- A credit to use for the first 30 days
- Access to over 25 products that are always free.
The free account provides a gateway for people to explore Azure and decide if it's right for their business.

# Subscriptions
Subscriptions, like resource groups, are a way to organise and distribute billing, resource groups, and scale. Each subscription is paid seperately, allowing you to keep track of your expenditure at a larger scale. A subscription is required in order to provision resources. An account may have multiple, however, only one subscription is strictly required. There are two types of subscription boundaries:
- **Billing Boundaries:** This allows you to define different billing types between subscriptions, with each invoiced seperately.
- **Access Control Boundaries:** This allows you to seperate which accounts can access resources by which subscriptions they are granted access to.
## Creating Additional Subscriptions
You may create additional subscriptions for the following reasons:
 - **Managing Environments:** You may choose todo this to have additional developement environments, for increased security, or to seperate data for compliance reasons.
 - **Organisational Structures:** Departments within an organisation may want to divide their subscriptions among teams instead to better allow for cost management.
 - **Billing:** Costs between subscriptions may need to be divided further for better invoicing and cost division.
## Azure Management Groups
The last piece of management is Management Groups. These allow you to divide resource groups into different projects or applications being developed into different groups to allow for easier management of projects and development.
![[Pasted image 20230203151118.png]]
Unlike [[1. Intro to Microsoft Azure#Resources & Resource Groups|Resource Groups]], management groups can be nested up to 6 times, allowing for a high degree of organisation.