<p align="center">
<img src="https://i.imgur.com/xlYwPUf.png" alt="Permissions Photo"/>
</p>

<h1>Understanding File Permissions</h1>
This lab focuses on file permissions and shares in the context of an Active Directory domain. File permissions and shares are key in a business setting to make sure users have the appropriate permissions and access to files they need. This is building up from a previous lab where I have a client joined to my domain ernestotest.com. I am logged in as Jane Doe (an admin account) on the domain controller VM and as a normal user on the client VM. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>File Permissions Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/bUjobDC.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/lz1DMos.png" height="80%" width="80%" alt="Permissions Steps"/>
</p>
<p>In order to set permissions for folders and files, we need to create the folders for sharing. While logged in to the domain controller VM as an admin, I've created four appropriately named folders on the C:\ drive.</p>

<p>To share a folder and assign permissions, open the folder's Properties and click on Share under the Sharing tab. Specify people on the network to share with and assign appropriate permissions. The permissions for the folders are as follows:</p>

<ol>
  <li>The read-access folder grants Domain Users Read permissions.</li>
  <li>The write-access folder gives Domain Users Read/Write permissions.</li>
  <li>The no-access folder provides Domain Admins with Read/Write access.</li>
</ol>

<p>It's important to note that the permissions for the accounting folder will be adjusted later in the process. This method demonstrates how folder sharing and permissions can be tailored to specific user groups, ensuring controlled access to shared resources.</p>

<br />

<p>
<img src="https://i.imgur.com/kWrpLFE.png" height="80%" width="80%" alt="Permissions Steps"/>
</p>
<p>
On the client VM, access the shared folders by navigating through File Explorer using the path \dc-1. Observe that certain folders restrict you from adding files, allowing only a view. Moreover, there might be a folder that denies access altogether. These restrictions exist because, as a Domain User, your permissions for each folder are intricately tied to both the Security Group to which you belong and the specific permissions configured for users within that Security Group. This setup showcases the nuanced and granular control that can be exerted over file access within a Windows/Active Directory environment.
</p>
<br />

<p>
<img src="https://i.imgur.com/NgM0CcI.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/I4k9T2J.png" height="80%" width="80%" alt="Permissions Steps"/>
</p>
<p>
Following the process on the domain controller, with the Active Directory Users and Computers panel open, create a new Security Group named ACCOUNTANTS. Once the new Group is established, proceed to the accounting folder and configure permissions to grant the ACCOUNTANTS Group Read/Write access to the folder. This ensures that members of the ACCOUNTANTS Group will have the appropriate permissions for accessing and modifying the contents of the accounting folder. This method demonstrates how Security Groups can be tailored to specific folders, allowing for streamlined access management in Active Directory environments.
</p>
<br />

<p>
<img src="https://i.imgur.com/xev1Svv.png" height="80%" width="80%" alt="Permissions Steps"/>
<img src="https://i.imgur.com/SHotVB2.png" height="80%" width="80%" alt="Permissions Steps"/>
</p>
<p>
In this scenario, the user is unable to access the accounting folder as they are not part of the ACCOUNTANTS Security Group. To address this, it's necessary to log off the client, allowing the permissions to take effect upon the next login.

On the domain controller, open the ACCOUNTANTS Properties in Active Directory Users and Computers. Navigate to the Members tab and add the respective user— in this case, bon.rovej. Once this adjustment is made, logging back into the client allows BLANK_ to successfully access the accounting folder, as they are now part of the ACCOUNTANTS Security Group. This demonstrates how effective management of Security Groups in Active Directory ensures precise access control for users.
<br />

<h2>Lessons Learned </h2>

This lab has provided me with a valuable insight into the workings of file permissions within the Windows/Active Directory environment. Understanding how file permissions operate is crucial for real-world scenarios where precise access control is essential. The importance of granting only the necessary permissions to individuals, ensuring they have access only to what is required for their tasks, has become evident. This practice not only enhances security but also ensures efficient workflow by limiting access to relevant resources. It emphasizes the principle of providing the minimum necessary permissions, a fundamental approach in effective access management within Windows and Active Directory environments.





