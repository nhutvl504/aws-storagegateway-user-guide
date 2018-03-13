# Troubleshooting Your Microsoft Hyper\-V Setup<a name="ResourceConfigureHostHyperV-troubleshooting"></a>

The following table lists typical issues that you might encounter when deploying AWS Storage Gateway on the Microsoft Hyper\-V platform\.


| Issue | Action to Take | 
| --- | --- | 
| You try to import a gateway and receive the error message: "Import failed\. Unable to find virtual machine import file under location \.\.\."\.![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-troubleshoot01.png) |  This error can occur for the following reasons: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/ResourceConfigureHostHyperV-troubleshooting.html)  | 
|  You try to import a gateway and receive the error message: "Import failed\. Import task failed to copy file\." ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-troubleshoot02.png)  |  If you have already deployed a gateway and you try to reuse the default folders that store the virtual hard disk files and virtual machine configuration files, then this error will occur\. To fix this problem, specify new locations in the **Hyper\-V Settings** dialog box\. ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-settings11.png)  | 
|  You try to import a gateway and receive an error message: "Import failed\. Import failed because the virtual machine must have a new identifier\. Select a new identifier and try the import again\." ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-troubleshoot03.png)  |  When you import the gateway make sure you select the **Copy the virtual machine** option and check the **Duplicate all files** option in the **Import Virtual Machine** dialog box to create a new unique ID for the VM\. The following example shows the options in the **Import Virtual Machine** dialog box that you should use\. ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-import03.png)  | 
|  You try to start a gateway VM and receive an error message "The child partition processor setting is incompatible with parent partition\." ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-troubleshoot04.png)  | This error is likely caused by a CPU discrepancy between the required CPUs for the gateway and the available CPUs on the host\. Ensure that the VM CPU count is supported by the underlying hypervisor\. For more information about the requirements for AWS Storage Gateway, see [Requirements](Requirements.md)\. | 
|  You try to start a gateway VM and receive an error message "Failed to create partition: Insufficient resources exist to complete the requested service\." ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-troubleshoot05.png)  |  This error is likely caused by a RAM discrepancy between the required RAM for the gateway and the available RAM on the host\. For more information about the requirements for AWS Storage Gateway, see [Requirements](Requirements.md)\.  | 
|  Your snapshots and gateway software updates are occurring at slightly different times than expected\.  |  The gateway VM's clock might be offset from the actual time, known as clock drift\. Check and correct the VM's time using local gateway console's time synchronization option\. For more information, see [Synchronizing Your Gateway VM Time](manage-on-premises-common.md#MaintenanceTimeSync-common)\.  | 
|  You need to put the unzipped Microsoft Hyper\-V AWS Storage gateway files on the host file system\.  |  Access the host as you do a typical Microsoft Windows server\. For example, if the hypervisor host is name `hyperv-server`, then you can use the following UNC path `\\hyperv-server\c$`, which assumes that the name `hyperv-server` can be resolved or is defined in your local hosts file\.  | 
|  You are prompted for credentials when connecting to hypervisor\. ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/storagegateway/latest/userguide/images/hyperv-vm-connect02.png)  |  Add your user credentials as a local administrator for the hypervisor host by using the Sconfig\.cmd tool\.  | 