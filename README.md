# AD Homelab — Build, Attack, Defend

A from-scratch Active Directory corporate network built in VirtualBox, then attacked from Kali Linux, then defended. Hands-on practice for Tier 1 SOC analyst work and Security+ concepts. Everything here was done by hand — no scripts doing the thinking for me.

## The lab

| Host | OS | Role | IP |
|------|----|------|----|
| DC01 | Windows Server 2025 | Domain controller (`mylab.local`) | 192.168.56.10 |
| LAB-PC-001 | Windows 11 | Domain-joined workstation | 192.168.56.20 |
| Kali_VM | Kali Linux | Attacker box (lab-only) | 192.168.56.30 |

All three VMs on a VirtualBox host-only network ("labnet").

## The 7 phases

0. **Recon** — map the lab, document the starting state
1. **Network foundation** — labnet, static IPs, connectivity, DNS
2. **Domain controller** — promote DC01, create the `mylab.local` forest
3. **Build the company** — OUs, users, groups, file shares
4. **Helpdesk drills + GPO** — account unlocks, password resets, Group Policy
5. **Attack (lab only)** — password spraying, AS-REP roasting from Kali
6. **Detect & defend** — hunt Event IDs 4625/4740, harden what broke
7. **Write-up** — resume-ready summary of the whole project

Each phase folder has notes on what I did, why I did it, and what broke along the way.

## Key things I learned

- (Fill this in as you go — this section is the whole point of the repo.)
