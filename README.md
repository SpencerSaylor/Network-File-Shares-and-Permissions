<p align="center">
<img src="https://i.imgur.com/ji8tw98.png" width="50%" height="50%"/>
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Create some sample file shares with various permissions</h2>
<ol>
  <li>Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)</li>
  <li>Connect/log into Client-1 as a normal user (mydomain\<someuser>)</li>
  <li>On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”</li>
  <li> Set the following permissions (share the folder)
    <ol>
      <li>Folder: “read-access”, Group: “Domain Users”, Permission: “Read”</li>
      <li>Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”</li>
      <li>Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”</li>
      <li>(Skip accounting for now)</li>
    </ol>
  </li>
</ol>

<h2>Attempt to access file shares as a normal user</h2>
<ol>
  <li>On Client-1, navigate to the shared folder (start, run, \\dc-1)</li>
  <li>Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?</li>
</ol>

<h2>Create an “ACCOUNTANTS” Security Group, assign permissions, an test access</h2>
<ol>
  <li>Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”</li>
  <li>On the “accounting” folder you created earlier, set the following permissions:
    <ol>
      <li>Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”</li>
    </ol>
  </li>
  <li>On Client-1, as  <someuser>, try to access the accountants folder. It should fail.</li>
  <li>Log out of Client-1 as  <someuser></li>
  <li>On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group</li>
  <li>Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now?
</li>
</ol>
