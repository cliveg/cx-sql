# VM-high-iops-data-disks

Create a SQL Server Enterprise VM with 5TB of Data Disks configured for high IOPS

<a href="https://azuredeploy.net" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

This template creates an instance with the 5  data disks configured in a simple storage space as a single drive.   It creates a new volume with the target interleave of 64KB striped across the number of disks present.  The volume is formatted with NTFS and presented as the H:\.    This is ideal for IOPS and throughput intensive workloads while still leveraging standard storage.  The storage account created is locally redundant (LRS) Premium Storage.


Below are the parameters that the template expects

| Name   | Description    |
|:--- |:---|
| newStorageAccountName  | Name of the storage account to create |
| adminUsername | Admin username for the VM |
| adminPassword | Admin password for the VM |
| vmSourceImageName | Name of image to use for the VM <br> <ul><li>SQL 2014 Enterprise on Windows Server 2012 R2 Datacenter**(default)**</li></ul>|
| location  | Location where to deploy the resource  |
| vmSize | Size of the VM <br> <ul>**Currenlty allowed values**<li>Standard_DS13 **(default)**</li></ul>|
| sizeOfEachDataDiskInGB | The disks created will all be of this size <ul><li>1023 **(default)**</li></ul>|
| publicIPAddressName | Name of the public IP address to create |
| dnsName | DNS name that will map to the public IP |
| vmStorageAccountContainerName | Name of storage account container for the VM <br> <ul><li>vhds **(default)**</li></ul>|
| vmName | Name for the VM |
| virtualNetworkName | Name of the Virtual Network |
| nicName | Name for the Network Interface |
| modulesUrl | Url for the DSC configuration module <br> <ul> <li><b>https://github.com/CliveG/cx-sql/raw/master/StoragePool.ps1.zip</li></ul>|
