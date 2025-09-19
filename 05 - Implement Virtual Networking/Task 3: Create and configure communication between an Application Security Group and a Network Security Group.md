Task 3: Create and configure communication between an Application Security Group and a Network Security Group
In this task, we create an Application Security Group and a Network Security Group. The NSG will have an inbound security rule that allows traffic from the ASG. The NSG will also have an outbound rule that denies access to the internet.

Create the Application Security Group (ASG)
In the Azure portal, search for and select Application security groups.

Click Create and provide the basic information.

Setting	Value
Subscription	your subscription
Resource group	az104-rg4
Name	asg-web
Region	East US
Click Review + create and then after the validation click Create.

Note: At this point, you would associate the ASG with virtual machine(s). These machines will be affected by the inbound NSG rule you create in the next task.

Create the Network Security Group and associate it with CoreServicesVnet
In the Azure portal, search for and select Network security groups.
Note: You can also locate this resource using the Azure portal menu (icon top left). Select Create a resource and then in the Networking blade, select Network security group.

Select + Create and provide information on the Basics tab.

Setting	Value
Subscription	your subscription
Resource group	az104-rg4
Name	myNSGSecure
Region	East US
Click Review + create and then after the validation click Create.

After the NSG is deployed, click Go to resource.

Under Settings click Subnets and then Associate.

Setting	Value
Virtual network	CoreServicesVnet (az104-rg4)
Subnet	SharedServicesSubnet
Click OK to save the association.

Configure an inbound security rule to allow ASG traffic
Continue working with your NSG. In the Settings area, select Inbound security rules.

Review the default inbound rules. Notice that only other virtual networks and load balancers are allowed access.

Select + Add.

On the Add inbound security rule blade, use the following information to add an inbound port rule. This rule allows ASG traffic. When you are finished, select Add.

Setting	Value
Source	Application security group
Source application security groups	asg-web
Source port ranges	*
Destination	Any
Service	Custom (notice your other choices)
Destination port ranges	80,443
Protocol	TCP
Action	Allow
Priority	100
Name	AllowASG
Configure an outbound NSG rule that denies Internet access
After creating your inbound NSG rule, select Outbound security rules.

Notice the AllowInternetOutboundRule rule. Also notice the rule cannot be deleted and the priority is 65001.

Select + Add and then configure an outbound rule that denies access to the internet. When you are finished, select Add.

Setting	Value
Source	Any
Source port ranges	*
Destination	Service tag
Destination service tag	Internet
Service	Custom
Destination port ranges	*
Protocol	Any
Action	Deny
Priority	4096
Name	DenyInternetOutbound
Task 4: Configure public and private Azure DNS zones
