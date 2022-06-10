[TryHackMe | Active Directory Basics](https://tryhackme.com/room/activedirectorybasics)
# Active Directory Basics
`Learn the basics of Active Directory and how it is used in the real world today`
## Task 1 Introduction

## Task 2 Physical Active Directory

## Task 3 The Forest

## Task 4 Users + Groups

## Task 5 Trusts + Policies

## Task 6 Active Directory Domain Services + Authentication
[TryHackMe | Attacking Kerberos](https://tryhackme.com/room/attackingkerberos)

### Domain Authentication Overview
There are two main types of authentication in place for Active Directory: NTLM and Kerberos.
1. Kerberos - The default authentication service for Active Directory uses ticket-granting tickets and service tickets to authenticate users and give users access to other resources across the domain.
2. NTLM - default Windows authentication protocol uses an encrypted challenge/response protocol

## Task 7 AD in the Cloud
|   Windows Server AD   |   Azure AD    |
|     :-----------:     |   :-------:   |
|   LDAP                |   Rest APIs   |
|   NTLM                |   OAuth/SAML  |
|   Kerberos            |   OpenID      |
|   OU Tree             |   Flat Structure    |
| Domains and Forests   |   Tenants     |
|   Trusts              |   Guests      |

## Task 8 Hands-On Lab
[PowerView-3.0 tips and tricks](https://gist.github.com/HarmJ0y/184f9822b195c52dd50c379ed3117993)

```
C:\Users\Administrator\Downloads>systeminfo

Host Name:                 DOMAIN-CONTROLL
OS Name:                   Microsoft Windows Server 2019 Standard
OS Version:                10.0.17763 N/A Build 17763
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Primary Domain Controller
OS Build Type:             Multiprocessor Free
Registered Owner:          Windows User
Registered Organization:
Product ID:                00429-70000-00000-AA733
Original Install Date:     5/13/2020, 7:00:12 PM
System Boot Time:          5/30/2022, 7:35:20 AM
System Manufacturer:       Xen
System Model:              HVM domU
System Type:               x64-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: Intel64 Family 6 Model 63 Stepping 2 GenuineIntel ~2400 Mhz
BIOS Version:              Xen 4.11.amazon, 8/24/2006
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (UTC-08:00) Pacific Time (US & Canada)
Total Physical Memory:     2,048 MB
Available Physical Memory: 780 MB
Virtual Memory: Max Size:  3,200 MB
Virtual Memory: Available: 2,005 MB
Virtual Memory: In Use:    1,195 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    CONTROLLER.local
Logon Server:              \\DOMAIN-CONTROLL
Hotfix(s):                 5 Hotfix(s) Installed.
                           [01]: KB4586875
                           [02]: KB4512577
                           [03]: KB4580325
                           [04]: KB4587735
                           [05]: KB4592440
Network Card(s):           1 NIC(s) Installed.
                           [01]: AWS PV Network Device
                                 Connection Name: Ethernet
                                 DHCP Enabled:    Yes
                                 DHCP Server:     10.10.0.1
                                 IP address(es)
                                 [01]: 10.10.96.54
                                 [02]: fe80::d9c9:b053:a4ed:96d2
Hyper-V Requirements:      A hypervisor has been detected. Features required for Hyper-V will not be displayed.

C:\Users\Administrator\Downloads>
```
```
Microsoft Windows [Version 10.0.17763.1637]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\Users\Administrator>cd Downloads

C:\Users\Administrator\Downloads>dir
 Volume in drive C has no label.
 Volume Serial Number is F83F-6346

 Directory of C:\Users\Administrator\Downloads

01/03/2021  10:59 AM    <DIR>          .
01/03/2021  10:59 AM    <DIR>          ..
05/14/2020  11:39 AM         1,261,832 mimikatz.exe
05/14/2020  11:41 AM           374,625 PowerView.ps1
05/14/2020  11:43 AM           973,325 SharpHound.ps1
               3 File(s)      2,609,782 bytes
               2 Dir(s)  47,337,594,880 bytes free

C:\Users\Administrator\Downloads>powershell -ep bypass
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\Administrator\Downloads> . .\PowerView.ps1
PS C:\Users\Administrator\Downloads> ls


    Directory: C:\Users\Administrator\Downloads


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/14/2020  11:39 AM        1261832 mimikatz.exe
-a----        5/14/2020  11:41 AM         374625 PowerView.ps1
-a----        5/14/2020  11:43 AM         973325 SharpHound.ps1
```
```
PS C:\Users\Administrator\Downloads> Get-NetComputer -fulldata |select operatingsystem

operatingsystem
---------------
Windows Server 2019 Standard
Windows 10 Enterprise Evaluation
Windows 10 Enterprise Evaluation
```
```
PS C:\Users\Administrator\Downloads> Get-NetUser |select name

name
----
Administrator
Guest
krbtgt
Machine-1
Admin2
Machine-2
SQL Service
POST{P0W3RV13W_FTW}
sshd
```
```
PS C:\Users\Administrator\Downloads> Get-NetGroup -GroupName *
Administrators
Users
Guests
Print Operators
Backup Operators
Replicator
Remote Desktop Users
Network Configuration Operators
Performance Monitor Users
Performance Log Users
Distributed COM Users
IIS_IUSRS
Cryptographic Operators
Event Log Readers
Certificate Service DCOM Access
RDS Remote Access Servers
RDS Endpoint Servers
RDS Management Servers
Hyper-V Administrators
Access Control Assistance Operators
Remote Management Users
Storage Replica Administrators
Domain Computers
Domain Controllers
Schema Admins
Enterprise Admins
Cert Publishers
Domain Admins
Domain Users
Domain Guests
Group Policy Creator Owners
RAS and IAS Servers
Server Operators
Account Operators
Pre-Windows 2000 Compatible Access
Incoming Forest Trust Builders
Windows Authorization Access Group
Terminal Server License Servers
Allowed RODC Password Replication Group
Denied RODC Password Replication Group
Read-only Domain Controllers
Enterprise Read-only Domain Controllers
Cloneable Domain Controllers
Protected Users
Key Admins
Enterprise Key Admins
DnsAdmins
DnsUpdateProxy
```
```
PS C:\Users\Administrator\Downloads> Get-NetGroup -GroupName *V*
Event Log Readers
Certificate Service DCOM Access
RDS Remote Access Servers
RDS Endpoint Servers
RDS Management Servers
Hyper-V Administrators
RAS and IAS Servers
Server Operators
Terminal Server License Servers
```
```
PS C:\Users\Administrator\Downloads> Get-NetUser -SPN |select pwdlastset

pwdlastset
----------
5/13/2020 8:14:47 PM
5/13/2020 8:26:58 PM
```
```
PS C:\Users\Administrator\Downloads> Get-NetUser -SPN |?{$_.memberof -match 'Domain Admins'}


logoncount            : 0
badpasswordtime       : 12/31/1600 4:00:00 PM
description           : My password is MYpassword123#
distinguishedname     : CN=SQL Service,CN=Users,DC=CONTROLLER,DC=local
objectclass           : {top, person, organizationalPerson, user}
displayname           : SQL Service
userprincipalname     : SQLService@CONTROLLER.local
name                  : SQL Service
objectsid             : S-1-5-21-849420856-2351964222-986696166-1107
samaccountname        : SQLService
lastlogon             : 12/31/1600 4:00:00 PM
codepage              : 0
samaccounttype        : 805306368
whenchanged           : 5/14/2020 3:42:53 AM
accountexpires        : 9223372036854775807
countrycode           : 0
adspath               : LDAP://CN=SQL Service,CN=Users,DC=CONTROLLER,DC=local
instancetype          : 4
objectguid            : 1c3f20d7-c383-466a-9a67-92a774650cb8
sn                    : Service
lastlogoff            : 12/31/1600 4:00:00 PM
objectcategory        : CN=Person,CN=Schema,CN=Configuration,DC=CONTROLLER,DC=local
dscorepropagationdata : {5/14/2020 3:29:56 AM, 1/1/1601 12:00:00 AM}
serviceprincipalname  : DOMAIN-CONTROLLER/SQLService.CONTROLLER.local:60111
givenname             : SQL
admincount            : 1
memberof              : {CN=Group Policy Creator Owners,OU=Groups,DC=CONTROLLER,DC=local, CN=Domain Admins,OU=Groups,DC=CONTROLLER,DC=local, CN=Enterprise
                        Admins,OU=Groups,DC=CONTROLLER,DC=local, CN=Schema Admins,OU=Groups,DC=CONTROLLER,DC=local...}
whencreated           : 5/14/2020 3:26:57 AM
badpwdcount           : 0
cn                    : SQL Service
useraccountcontrol    : 66048
usncreated            : 12820
primarygroupid        : 513
pwdlastset            : 5/13/2020 8:26:58 PM
usnchanged            : 12890
```
