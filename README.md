<p align="center">
<img src="https://i.imgur.com/AeiqMDZ.png" alt="Traffic Examination"/>
</p>

<h1>Network-File-Shares-and-Permissions</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Domain Controller/Client Machine)
- Remote Desktop
- Shared Network Files

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Network File Shares and Permissions Module</h2>
</p>
<p>
In this lab we will set up shared network files and permissions. The goal is to create folders on the DC-1 virtual machine and make them available on the network, while restricting access to certain files to designated users only.
<p> 
By the end of this lab, We'll have gained valuable experience in managing network files and setting up permissions to ensure that confidential information is kept secure. Let's get started!
<p>
<img src="https://i.imgur.com/FRxdCJ3.png" height="70%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To begin, let's start by navigating to the c:/ drive on the DC-1 machine and creating four folders: "read-access", "read/write-access", "no-access", and "accounting". Each of these folders will have different access permissions.
<p>
Once the folders have been created, the next step is to share them on the network so that the client-1 machine can access them. In addition, we need to configure the appropriate access permissions for each folder on the DC-1 machine.
<p>
-  For instance, the "read-access" folder should be set to read-only permissions for domain users, <br />meaning they can only view the files but not make any changes. 
<br />-  On the other hand, the "read/write-access" folder should have read/write permissions for domain users, <br />allowing them to make changes to the files.
<br />-  Finally, the "no-access" folder should be restricted to domain admins only with read/write permissions. <br />This ensures that sensitive files within the folder are only accessible to authorized personnel.

By setting up these permissions, we can ensure that our network files are secure and that confidential information is only accessible to those with the appropriate permissions.

<h3>Attempting to Access File Shares as a Normal User</h3>
<p>
<img src="https://i.imgur.com/RbG2OQc.png" height="70%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To test the shared files we just created, we can log in to the client machine using a normal user account. This will enable us to verify that the permissions we've set are working correctly.
<p>
<img src="https://i.imgur.com/a03OLVP.png" height="70%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
If the permissions have been set up correctly, we should be able to access the "read-access" folder and view its contents, but not make any changes. Similarly, we should be able to access the "read/write access" folder and both view and edit the files within it.
<p>
<img src="https://i.imgur.com/QVePbZd.png" height="70%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On the other hand, attempting to access the "no-access" folder with a normal user account should result in an access denied error, since this folder is restricted to domain admins only.

By testing the shared files in this way, we can confirm that our permissions have been set up correctly and that our network files are secure.


<h3>Create an “ACCOUNTANTS” Security Group, Assign Permissions, and Test Access</h3>


<p>
<img src="https://i.imgur.com/Zvj44Db.png" height="60%" width="70%" alt="Disk Sanitization Steps"/>
<p>
</p>
Let's return to the DC-1 VM and create a security group called "Accountants" in Active Directory. Users assigned to this group will be the only ones allowed to view the "Accountants" folder.
<p>
<img src="https://i.imgur.com/cmeQ6kj.png" height="60%" width="70%" alt="Disk Sanitization Steps"/>
<p>
</p>
Next, we need to share the "Accountants" folder, similar to what we did in the previous section. However, this time, we will share it exclusively with the "Accountants" group. Normal users will not have access to this folder, and if we want to grant a normal user access to the "Accountants" folder, they will need to be added to the "Accountants" security group.
<p>
<img src="https://i.imgur.com/SKGiAeu.png" height="60%" width="70%" alt="Disk Sanitization Steps"/>
<p>
</p>
By creating a dedicated security group and granting exclusive access to the "Accountants" folder, we can ensure that only authorized personnel, such as the accountants, have access to confidential files. Adding our normal user to the security group enables them to access the "Accountants" folder, further reinforcing the security measures in place. 
<p>
<img src="https://i.imgur.com/e4VzO53.png" height="60%" width="70%" alt="Disk Sanitization Steps"/>

