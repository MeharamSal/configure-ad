<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1

<h2>Deployment and Configuration Steps</h2>














<p>
<img width="635" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/40cc7f3f-aaa2-438f-8362-c7d7952cac5e">
  <img width="560" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/1a695cdf-c8f3-45bd-b2e5-9a67331f6f32">
  <img width="841" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/59bdee6d-9ac9-43e4-830b-a9abc65ab896">
<img width="388" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/d40ecd8d-f2b8-4c1f-b02d-6c03cbc0b204">


</p>
<p>
Create the Domain Controller VM (Windows Server 2022).
</p>
<p>
  Set Domain Controller’s NIC Private IP address to be static

</p>
<br />













<p>
<img width="553" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/21a78998-ea02-4611-995a-1b38a33a7d1c">
<img width="604" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/1a705240-fa9c-49b3-9520-e07bcff6a662">


</p>
<p>
Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created
</p>
<br />







<p>
<img width="1610" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/a67da3ae-a8e6-4006-8657-4edbda3a21be">

</p>
<p>
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping)

</p>
<br />







<p>
<img width="1013" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/6ba50f35-a736-4fc5-9a81-c77ef1170ed2">
<img width="1011" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/7bdd01a8-348c-448b-bde3-fffbce7a7f53">



</p>
<p>
Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall


</p>
<br />



<p>
<img width="811" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/86ec9a90-a0f8-49b2-b0fd-ee770537987e">
  <img width="325" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/9e1ea4bf-da8e-49a7-9eaa-877008c7c39b">

</p>
<p>
Login to DC-1 and install Active Directory Domain Services

</p>
<br />




<p>
<img width="289" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/91d15647-c65a-48d0-93b8-7b72b635caf3">
<img width="501" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/c7178769-9078-443c-9296-aacce7e1915f">

</p>
<p>
Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)

</p>
<br />
























<p>
<img width="321" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/c60505dd-09c9-4024-b16f-ef529af0e73f">

</p>
<p>
Restart and then log back into DC-1 as user: mydomain.com\labuser

</p>
<br />






















<p>
<img width="265" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/362695c2-fff3-4304-a749-e48648355b61">
<img width="614" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/e06ae893-5a99-49f0-b32c-bef0f1ac77a5">
<img width="488" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/bc064c34-9fdf-49f0-80a7-0bca5bd41043">



</p>
<p>
In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES” &"_ADMINS"

</p>
<br />

























<p>
<img width="319" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/844e3b89-f198-4cfd-99ea-9ca5a07f2b8a">
<img width="397" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/521cb5d2-ae84-41af-8b82-ac0e62e3b4ee">
<img width="293" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/84a5b756-7961-4769-885d-6c22e3a8a433">
<img width="320" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/b0211628-4c65-49dd-9c78-9c90e3b90862">



</p>
<p>
Create your first Employee
</p>
<p>
  Add your Employee to the “Domain Admins” Security Group

</p>
<br />





























<p>
<img width="285" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/95376876-b0ed-4e2a-ae6f-bdf07c713d12">

</p>
<p>
Log Back in As your newly created Employee
</p>
<br />





































<p>
<img width="591" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/518e45e7-464f-4b37-9f4c-56629d30bb7a">

</p>
<p>
From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address

</p>
<br />


















<p>
<img width="1130" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/452f66e2-fa14-449a-ad0f-b18516ed4b99">
<img width="298" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/843d2ffd-8551-4167-a45f-d68e1a57dd91">
  <img width="679" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/0151d6bb-374a-4807-a1b3-74f7bc8a9424">



</p>
<p>
After Restarting Client one and logging in as orginial user,join it to the domain. Your computer will restart if done Correctly.
</p>
<br />































<p>
<img width="490" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/8a0b032d-bbb5-48f5-a38d-cfd046cbd96a">

</p>
<p>
Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain

</p>
<br />




































<p>
<img width="1143" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/c616a17c-05ac-40bc-ae45-df62ca7b8d6f">
<img width="274" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/6081e701-3108-48a4-8f54-37bdfd789cd9">


</p>
<p>
Log into Client-1 as your new User 
</p>
<br />


































<p>
<img width="827" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/f9b6e296-b444-4cfe-bfbd-185cabb7bcc0">
<img width="421" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/a57826f5-adcb-4ea1-b556-c2eb0da8eeee">
<img width="285" alt="image" src="https://github.com/MeharamSal/configure-ad/assets/173064050/cd6c162a-21fc-4f68-90e7-dfe5485a8812">



</p>
<p>
navigate to “Remote Desktop”
Allow “domain users” access to remote desktop

</p>
<br />
