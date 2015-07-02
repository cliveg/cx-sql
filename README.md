# VM-high-iops-data-disks

Create a SQL Server Enterprise VM with 5TB of Data Disks configured for high IOPS

<a href="https://azuredeploy.net" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

This template creates SQL Server instances with the 5  data disks configured in a simple storage space as a single drive for maximum IOPS. You can customize the count of instances so you can build 1 SQL Server to as many as you like! It creates a new volume with the target interleave of 64KB striped across the number of disks present.  The volume is formatted with NTFS and presented as the H:\.    This is ideal for IOPS and throughput intensive workloads while still leveraging standard storage.  The storage account created is locally redundant (LRS) Premium Storage.<br>

Trigger using the button on this page 'Deploy to Azure' or PowerShell.<br>

Azure PowerShell Approach:<br>
1. Add-AzureAccount<br>
2. Set-AzureSubscription -Name 'my subscription' (optional if you have multiple!)<br>
3. New-AzureResourceGroup -DeploymentName 'AzureDeploy' -Location 'WestUS' -TemplateUri 'https://raw.githubusercontent.com/cliveg/cx-sql/prod-two-server/azuredeploy.json'-verbose -newStorageAccountName contososa123 -DnsName uniquename123 -Name 'SQLServer' -vmCount 1<br>
<br>

Below are the parameters that the template expects<br>

| Name   | Description    |
|:--- |:---|
| newStorageAccountName  | Name of the storage account to create |
| adminUsername | Admin username for the VM <ul><li>AzAdmin **(default)**</li></ul>|
| adminPassword | Admin password for the VM <ul><li>AzP@ssword1 **(default)**</li></ul>|
| vmSourceImageName | Name of image to use for the VM <br> <ul><li>SQL 2014 Enterprise on Windows Server 2012 R2 Datacenter**(default)**</li></ul>|
| location  | Location where to deploy the resource  |
| vmCount | Quantity of the VMs <br> <ul><li>2 **(default)**</li></ul>|
| vmSize | Size of the VM <br> <ul>**Currenlty allowed values**<li>Standard_DS13 **(default)**</li></ul>|
| sizeOfEachDataDiskInGB | The disks created will all be of this size <ul><li>1023 **(default)**</li></ul>|
| publicIPAddressName | Name of the public IP address to create |
| dnsName | DNS name that will map to the public IP |
| vmStorageAccountContainerName | Name of storage account container for the VM <br> <ul><li>vhds **(default)**</li></ul>|
| vmName | Name for the VM |
| virtualNetworkName | Name of the Virtual Network |
| nicName | Name for the Network Interface |
| modulesUrl | Url for the DSC configuration module <br> <ul> <li><b>https://github.com/CliveG/cx-sql/raw/prod-two-server/StoragePool.ps1.zip</li></ul>|
