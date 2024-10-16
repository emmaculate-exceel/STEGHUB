# Load balancer solution apache 101



#### load balancing using apache2
---
![SupportApache-small](https://github.com/user-attachments/assets/e5351480-7499-4481-9c0b-fa8577ce5e55)
---

+ Vertical scaling: When you just one server and load increases you get to serve more client, in this case you have to add more CPU and RAM or complety replace the server with a much powerful one this is what we call Vertical scaling. This approach has limitations though and the limitation is at some point you can the the maximum capacity of your CPU or RAM that is installed on the server .


+ Horizontal scaling: This is another approach used to handle increase in data traffic , distributing loads across multiple servers . This approach is much more common and can be applied almost seamlessly and almost indefinitely .


NOTE : Horizontal scaling adopt to current load by adding (scale out), or removing (scale in) Web servers. adjustment of numbers of servers can be done manually or automatically.
