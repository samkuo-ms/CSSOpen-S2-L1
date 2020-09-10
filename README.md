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

## 1.4 Start waagent service
> Check status Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl start waagent
> sam@samlinux-sa-spoke2-vm1:~$ sudo systemctl status waagent
> ```
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/4-1.png "4-1")<br>


-What’s the action status on portal ?
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/4-1.png "4-2")<br>

## 1.5 Login again and type the new password
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L1-Images/5-1.png "5-1")<br>

## 1.6 Change to original password in Linux VM
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
> Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ yum install httpd
> ```
## 2.2 Start httpd service and check status
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L2-Images/2-1.png "2-1")<br>
> Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ yum install httpd
> ```
## 2.3 Add Web page context in to index.html file
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L2-Images/3-1.png "3-1")<br>
> Command:
> ```sh
> sam@samlinux-sa-spoke2-vm1:~$ echo 'This is Sam’s EUS VM1.' > /var/www/html/index.html
> ```
## 2.4 Open webpage view result
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L2-Images/4-1.png "4-1")<br>


## CSSOpen Session 2 Lab 3 - Mount Azure Nfs share 
## 3.1 Mount Blob storage by using the Network File System (NFS) 3.0 protocol (preview)
[Mount Blob storage by using the Network File System (NFS) 3.0 protocol (preview)](https://docs.microsoft.com/en-us/azure/storage/blobs/network-file-system-protocol-support-how-to?tabs=linux)
- 3.1.1 Step 1: Register the NFS 3.0 protocol feature with your subscription
    1.Open a Cloud Shell (PowerShell)command window.
    2.Register the AllowNFSV3 feature by using the following command.
> ```ps
> PS Register-AzProviderFeature -FeatureName AllowNFSV3 -ProviderNamespace Microsoft.Storage 
> ```
    3.Register the PremiumHns feature by using the following command as well.
> ```ps
> PS Register-AzProviderFeature -FeatureName PremiumHns -ProviderNamespace Microsoft.Storage
> ```   
    4.Register the resource provider by using the following command.
> ```ps
> PS Register-AzResourceProvider -ProviderNamespace Microsoft.Storage
> ```  
- 3.1.2 Verify that the feature is registered
> ```ps
> PS Get-AzProviderFeature -ProviderNamespace Microsoft.Storage -FeatureName AllowNFSV3
> PS Get-AzProviderFeature -ProviderNamespace Microsoft.Storage -FeatureName PremiumHns
> ``` 
- 3.1.3 Create and configure a storage account
As you configure the account, choose these values:
In the preview release of this feature, NFS 3.0 protocol is supported only in [BlockBlobStorage](../blobs/storage-blob-create-account-block-blob.md) accounts.
> [!NOTE]
> NFS 3.0 protocol support in Azure Blob storage is in public preview and is available in the following regions: US East, US Central, US West Central, Australia Southeast, North Europe, UK West, Korea Central, Korea South, and Canada Central.

|Setting | Value|
|----|---|
|Location|One of the following regions: US East, US Central, US West Central, Australia Southeast, North Europe, UK West, Korea Central, Korea South, and Canada Central |
|Performance|Premium|
|Account kind|BlockBlobStorage|
|Replication|Locally-redundant storage (LRS)|
|Connectivity method|Public endpoint (selected networks) or Private endpoint|
|Secure transfer required|Disabled|
|Hierarchical namespace|Enabled|
|NFS V3|Enabled|
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L3-Images/1-1.png "1-1")<br>
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L3-Images/1-2.png "1-2")<br>
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L3-Images/1-2.png "1-3")<br>
- 3.1.4 Create a container
> ![GITGUB](https://github.com/samkuo-ms/CSSOpen-S2-L1/blob/master/CSSOpen-S2-L3-Images/1-2.png "1-4")<br>
- 3.1.5 Mount the container
Create a directory on your Windows or Linux system, and then mount a container in the storage account.
### [Linux](#tab/linux)

1. On a Linux system, create a directory.

   ```
   mkdir -p /mnt/test
   ```

2. Mount a container by using the following command.

   ```
   mount -o sec=sys,vers=3,nolock,proto=tcp <storage-account-name>.blob.core.windows.net:/<storage-account-name>/<container-name>  /mnt/test
   ```

   - Replace the `<storage-account-name>` placeholder that appears in this command with the name of your storage account.  

   - Replace the `<container-name>` placeholder with the name of your container.



