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
