# CSSOpen-S2-Lab

## CSSOpen Session 2 Lab 1 - Understanding and using Linux service with Azure Linux Agent (waagent)

## 1.1 Check waagent service status

> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/1-1.PNG "1-1")<br>

> Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl status waagent
> ```

## 1.2 Stop waagent service and check status
Stop waagent service
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/2-1.PNG "2-1")<br>

> Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl stop waagent
> ```
check waagent service service has been already stopped
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/2-2.PNG "2-2")<br>
> Check status Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl status waagent
> ```

## 1.3 Reset password from Azure portal
Reset password on Azure portal, choose your vm and reset password
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/3-1.png "3-1")<br>
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/3-2.png "3-1")<br>

-What’s the action status 5 mins after your trigger reset password on portal?

-If you try to login to your VM now, does the new password work?
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/3-3.png "3-3")<br>

## Start waagent service
> Check status Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl start waagent
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl status waagent
> ```
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/4-1.png "4-1")<br>


-What’s the action status on portal ?
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/4-1.png "4-2")<br>

## 1.4 Login again and type the new password
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/5-1.png "5-1")<br>

## 1.5 Change to original password in Linux VM
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/6-1.png "6-1")<br>
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ passwd
> ```

Does it work?
if it does not work you can use this
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo passwd type-your-usersame-here
> ```
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/6-1.png "6-2")<br>

## CSSOpen Session 2 Lab 2 - Install httpd package for web service
## 2.1 Install httpd package
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L2-Images/1-1.png "1-1")<br>
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ yum install httpd
> ``
## 2.2 Start httpd service and check status
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L2-Images/2-1.png "2-1")<br>
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ yum install httpd
> ``
## 2.3 Add Web page context in to index.html file
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L2-Images/3-1.png "3-1")<br>
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ echo 'This is Sam’s EUS VM1.' > /var/www/html/index.html
> ``
## 2.4 Open webpage view result
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L2-Images/4-1.png "3-1")<br>


## CSSOpen Session 2 Lab 3 - Mount Azure Nfs share 
