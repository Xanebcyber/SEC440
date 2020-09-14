#What was done

The project began with the creation of two redundant firewalls which ran using a vrrp setup that allowed for the systems to continue working even if one of the two routing systems fell offline.
The net step was port forwarding using the nat destination commands to push all port 80 traffic into the network onto the web01 index.html page.
Once that was done, I was able to push forward the ssh and get everything up to the Multifactor authentication figured out on the system. 
I disabled SSH on web01 accidentally

#What were the challenges?

The challenges on the project occurred when I began to mess around with the vyos port forwarding on the vrrp setup as the network was unable to properly port forward the web server traffic at first.
Upon restarting services, the system began to work again. 
Finally,The MFA setup disabled ssh communication with the web01 server rendering the ssh port useless for the time being. I am still working on it.

#What was learned?

Begin working far in advance on an project.
Begin to logically structure the way that I approach issues and learn to restart services whenever they are augmented. 
