# Active Directory VAPT Lab

A beginner-friendly hands-on Active Directory security lab documenting enumeration from the perspective of a low-privileged domain user.

## Lab

- Domain: `corp.local`
- Domain Controller: `DC01.corp.local`
- DC IP: `192.168.56.101`
- Workstation: Windows 10 / `Windows.corp.local`
- Attacker: Kali Linux
- Domain user: `CORP\\alice`

## What I Practiced

- Nmap service enumeration
- LDAP RootDSE enumeration
- LDAP user and group enumeration
- Computer enumeration
- User attribute analysis
- SMB share enumeration
- SYSVOL and NETLOGON access
- SMBMap permission mapping
- RPC user/group enumeration
- Group Policy enumeration
- SPN enumeration
- Basic Kerberos concepts

## Repository Structure

```text
AD-Lab/
├── README.md
├── reports/
│   └── AD_Writeup.docx
├── evidence/
│   ├── ldap/
│   ├── smb/
│   ├── rpc/
│   ├── gpo/
│   ├── kerberos/
│   └── network/
└── commands/
    └── enumeration.md
```

## Key Observations

- Alice is a normal domain user and a member of the `IT` group.
- Alice can read `SYSVOL` and `NETLOGON`.
- Alice cannot access `ADMIN$` or `C$`.
- The domain contains the standard `Default Domain Policy` and `Default Domain Controllers Policy`.
- The captured Default Domain Policy has a 7-character minimum password length and `LockoutBadCount = 0`.
- The Domain Controllers Policy contains LDAP signing, Netlogon signing/sealing and SMB signing controls.
- No normal user-backed SPN was identified in the refined SPN enumeration.

## Evidence

The evidence folders contain screenshots collected during the lab. The SMBMap screenshot has been redacted where a credential was visible on the command line.

## Scope

This repository documents an authorized local training lab. It is intended for learning and portfolio documentation, not for testing systems without permission.

## Next Steps

- Kerberos service-account/SPN lab
- Kerberoasting in the isolated lab
- BloodHound relationship mapping
- ACL and privilege-path analysis
- Windows privilege escalation
- Lateral movement
