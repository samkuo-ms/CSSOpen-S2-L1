# CSSOpen-S2-L1 - Understanding and using Linux service with Azure Linux Agent (waagent)
CSSOpen Session 2 Lab 1 

## Check waagent service status

> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Image/1-1.png "1-1")<br>

> Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl status waagent
> ```

## Stop waagent service and check status
Stop waagent service
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Image/2-1.png "2-1")<br>

> Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl stop waagent
> ```
check waagent service service has been already stopped
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Image/2-2.png "2-2")<br>
> Check status Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl status waagent
> ```

## Reset password from Azure portal

-What’s the action status on portal ?


## Start waagent service

-What’s the action status on portal ?

## Login again and type the new password

## Change to original password in Linux VM




