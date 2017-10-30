# How to solve the testing problems of udacity simulator between windows and vmware Linux? （Original works）

[//]: # (Image References)
[image1]: ./1.png
[image2]: ./2.png
[image3]: ./3.png
[image4]: ./4.png

---
With regards to udacity simulator, we will use it from term 1 to term 3. And the setup of udacity simulator is supported very well on Linux if your host OS is linux, if your host OS is windows, you need to setup some tools like Ubuntu bash to run the linux kernel container and setup development environment for udacity simulator. This is complicated and has some impact to your windows OS.

But the udacity simulator works well on real single linux/windows/mac, if you run the simulator in virtual machine environment, it runs very hysteresis and nearly had to smoothly test the projects P4&P5 of term 2, which testing are lake race track, and term 3’s related projects. But the P1&P2 simulator works well in virtual machine. This is because there are some unknowing reasons about Unity support on vmware and linux in vmware.

So If your host OS is windows 7/10, and you have a virtual machine like vmware or others, you installed Linux in your virtual machine, your coding environment is under Linux (many library is based on linux of simulator). 

How to easily solve the simulation and development environment problems between windows and linux in virtual machine?

I tried many ways, including setup the driver and many kinds of tools, or config the etc file of virtual machine linux, but never work. 
I thought of an easy way to solve the problem, this way can solve above problems whatever windows < -- >linux, or windows< -- >mac, you can spread the thought to other situations. My case:
Host OS: win10
Virtual machine: vmware
OS in virtual machine: Ubuntu

The term2_sim_linux run very slowly in my virtual machine Linux when doing test on project lake race track, but the term2_sim_windows runs very smoothly in host win10 environment. So why not use term2_sim_windows on host windows with the code compiled on virtual linux to test the project?

Solution:

Config your virtual machine to communicate with host windows:
1.	Open your virtual machine software, like vmware.
2.	Edit --> virtual network editor.
This is to config your network. Maybe this step need administrator priviledge.

![alt text][image1]


3.	Add Port transport mapping config.

![alt text][image2]
 

4.	Config your port mapping between your host OS and virtual machine OS.
Here:
a.	Host port: it is ‘4567’, this is fixed value of simulator
b.	Protocol type: you must choose TCP protocol
c.	Virtual machine IP address: fill your own virtual machine OS Ethernet IP address, like: 192.168.*.*, you can check this by ‘ifconfig’ command in linux.
d.	Virtual machine port: Fill ‘4567’ at here, this is also a fixed value.
e.	Press OK, and the virtual machine network services will restart. (If not effect, you can restart the virtual machine OS.)
 
![alt text][image3]


Now, you can run udacity simulator in your windows OS, and compile the project code in your virtual linux OS.
 
![alt text][image4]

Good luck!

