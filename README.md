# AppDynamic ACI Integration Use Case

AppDynamic ACI Integration enables different Use Cases for Intent-based Multi-Cloud Automation


## Use Case 1: Address operations and maintenance interoperability between different departments and quickly locate faults

As a network engineer, have you ever experienced the phenomenon of "phantom packet loss"? That is, between two subnets, some hosts can successfully ping each other, while some cannot; for the same pair of hosts, some applications can connect, while some cannot. Developers, system engineers and network engineers checked again and again, but couldn’t figure out the cause. Finally, it takes dozens of hours to find the problem, but the help desk is already inundated with user complaints. We do have powerful monitoring and diagnostic tools, but they are siloed within their sub-system, and the deterioration of user experience is rarely caused by a single system failure as shown in the following figure: 

Figure1: Single sub-system failure ruins end user experience <br>

Like the picture shown below, deterioration of the user experience is more likely caused by multiple sub-systems’ interrelated failures, mis-configure or mismatch errors. Perhaps Application Performance Monitoring tools like AppDynamics can discover problem through end-to-end journey's monitoring, but they often act as tools in the hands of software developers or admins, and their silo with operation engineers is an old and well-known topic.
 
Figure2: Multiple sub-systems’ interrelated failures, mis-configure or mismatch errors cause poor end user experience <br>

This kind of estrangement within IT department is exactly what leads to a poor user experience of our IT Services. Don't get me wrong, I mean the interpersonal relationship between departments in these enterprises is still good, but human beings always have limited energy and knowledge, and it’s normal for them not to pay more attention to those not their own fields. Humans can't do it, but tools can. There is a language for communication between tools. The communication is in rich content, full speed and real-time. The key is what to communicate and who to communicate, and these can be told by human beings. Tools with the ability to communicate with each other finally solve the user experience degradation problem by integrating siloed systems as a whole.

The language of the tool is API and communicating with it through API is what we call Software Define. Tools can use it to communicate with each other, and humans can also use it to communicate with tools. This is why we need Software Defined Everything. Now let's come back to our "phantom packet loss" problem. Tools that can implement end-to-end journey health monitoring, such as AppDynamics, will see a decline in end user experience first, but its expertise is not in infrastructure troubleshooting. Therefore, it collects what it knows in detail from an application perspective -- namely, nodes IP addresses and TCP Port Numbers of related tiers with transaction issues --  and hands over to more specialized tools, such as ACI's Troubleshooting Wizard tools box, in API, a language they understand. The Troubleshooting Wizard then uses the information for extremely intensive data collection and diagnostics, which is impossible for daily operations because without precise contexts there is too much resource consumption for whole network diagnostics. The Troubleshooting Wizard shows that there is no problem with communication between all leaf switches, but random packet loss occurs at many ESXi hosts with dual NICs. So we start to focus on virtual networks within hypervisors, which is a headache for both host system engineers and network engineers. The answer comes in a minute or two: It turns out that, the host system engineers and network engineers have different ideas about dual-active NICs’ load balancing. The former thinks it should be per-VM based load balancing, while the latter thinks it’s Ethernet PortChannel's per-flow based load balancing. Depending on the fabric’s flow hash, the outgoing traffic from a VM does not necessarily return to the same VM because host system engineers assign different VMs to different uplink NIC, directly resulting in random packet loss for varies flows. It used to take the whole day for admins to troubleshoot while with communicated tools the same group of admins solve the problem in one or two minutes. A full video demo of the case can be found at the link below.


https://cisco.box.com/s/juitqwnl5rhl3qlqfegnypilb9w3wbcn


##Use Case 2: Extract application structure layers for security microsegmentation or policy automation

See the script get-app-structure.py

