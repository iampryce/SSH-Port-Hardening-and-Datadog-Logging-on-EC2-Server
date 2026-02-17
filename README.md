


<p align="center">
   
<img width="180" height="175" alt="image" src="https://github.com/user-attachments/assets/7da0af19-19db-478f-8945-a69971771ac0" />

</p>

<h1 align="center">  SSH Port Hardening & Datadog Logging on EC2-Server
</h1>

<p align="center">

## 🚀 Technologies Used

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![Amazon EC2](https://img.shields.io/badge/Amazon%20EC2-FF9900?style=for-the-badge&logo=amazon-ec2&logoColor=white)
![Datadog](https://img.shields.io/badge/Datadog-632CA6?style=for-the-badge&logo=datadog&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![MobaXterm](https://img.shields.io/badge/MobaXterm-005C99?style=for-the-badge&logo=windows-terminal&logoColor=white)

## 📌Architecture Overview 
This project demonstrates how to harden SSH access on an Amazon EC2 Ubuntu server by changing the default SSH port and updating security group rules accordingly. It also integrates Datadog for centralized log collection and monitoring.
This setup reduces exposure to automated brute-force attacks targeting port 22 and introduces centralized monitoring for better visibility into server activity.


![Architecture 2](https://github.com/user-attachments/assets/6743008a-b843-4148-811e-c8449411b812)


## Table of Content

[Launched an Ubuntu EC2 instance ](d#1-launched-an-ubuntu-ec2-instance)

[Connected securely via SSH (port 22)](#2-connected-securely-via-ssh-port-22)

[Modified the SSH configuration file to change the default SSH port](#3-modified-the-ssh-configuration-file-to-change-the-default-ssh-port)

[Updated EC2 security group inbound rules to allow the new custom port](#4-updated-ec2-security-group-inbound-rules-to-allow-the-new-custom-port)

[Restarted and verified SSH service on the new port](#5-restarted-and-verified-ssh-service-on-the-new-port-1632)

[Installed the Datadog Agent to collect system and authentication logs](#6-installed-the-datadog-agent-to-collect-system-and-authentication-logs)

[Verified log ingestion through the Datadog dashboard](#7-verified-log-ingestion-through-the-datadog-dashboard-)


## Steps

## 1) Launched an Ubuntu EC2 instance

_Security Group:  Allow SSH (22) temporarily from anywhere_

<img width="1355" height="660" alt="security group rules" src="https://github.com/user-attachments/assets/f90a6d15-b768-4251-bd13-7c160842bb36" />


## 2) Connected securely via SSH (port 22)

_Connected to the instance via ssh (port 22) on MobaXterm with the instance IP and a keypair file_ &
_updated the sever_

<img width="1323" height="713" alt="server updated" src="https://github.com/user-attachments/assets/73bb4ce3-4933-49bd-abbc-58df8145c329" />


## 3) Modified the SSH configuration file to change the default SSH port
Note: _changed host name to: port-change_

File path :ubuntu@port-change:/etc/ssh$

commds:

_sudo nano sshd_config_

after edit,  save: _crt O enter control X_

<img width="1356" height="653" alt="ssh file edit 1" src="https://github.com/user-attachments/assets/f88872f7-34c3-40c9-af41-fd5191a678f4" />

<br/>

✔ Verified default port changed from 22 to 1632

<be/>
<img width="1298" height="646" alt="Verifed port changed" src="https://github.com/user-attachments/assets/7c44702d-590e-4ab2-9cac-0b64cfe3b9e5" />


## 4) Updated EC2 security group inbound rules to allow the new custom port
Note: Reboot sever  after to make changes sync sometimes that would be needed.

<img width="1339" height="655" alt="modfied ec2 inbound rule" src="https://github.com/user-attachments/assets/338830aa-be7d-4e07-872d-99c317a91231" />

## 5) Restarted and verified SSH service on the new port 1632

signed in with the new port on MobaXterm 

<img width="1316" height="665" alt="ssh on custom port 1" src="https://github.com/user-attachments/assets/9de92625-716a-4012-98e5-80b04eaef9e7" />

✔ Verified sever now listening on port 1632

commds : _sudo systemctl status ssh_

<img width="1284" height="680" alt="final check port changed" src="https://github.com/user-attachments/assets/b043ca42-7503-4e41-81ae-cc591af67a1b" />


## 6) Installed the Datadog Agent to collect system and authentication logs

_steps_

- signed in for datadog free-tier

- selected linux based agent since the sever is linux based
  
- Turned on Application performance monitoring & Log collection
  
- Ran the installation command on the server ( this will install the datadog agent on the server)

<img width="1283" height="702" alt="Agent set up 1" src="https://github.com/user-attachments/assets/0507a19b-1b64-409d-869e-781e04f5711d" />


✔ Verified Datadog is installed and running

<img width="1310" height="680" alt="Final Check Datadog agent running" src="https://github.com/user-attachments/assets/9d8f5796-200d-46bc-a7ba-3c648821e7a0" />



## 7) Verified log ingestion through the Datadog dashboard ✔

<img width="1294" height="709" alt="Verify log 2" src="https://github.com/user-attachments/assets/9259fa95-ae46-4f6c-a889-c28a11d62008" />

<img width="1345" height="679" alt="Final Verification Datadog logs" src="https://github.com/user-attachments/assets/ed22ad12-8651-47e0-aae8-667cb1e1cf65" />


## 📌 Conclusion 

The EC2 server is now secured with a custom SSH port and monitored with Datadog. Logs are centralized, and the setup is fully documented for easy replication. Checked attached folder for every step











