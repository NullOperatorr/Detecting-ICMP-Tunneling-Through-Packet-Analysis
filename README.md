# Detecting-ICMP-Tunneling-Through-Packet-Analysis
CyberLab-05



## Overview

This repository documents the analysis of a packet capture containing an ICMP tunneling session.  
The objective is to investigate how ICMP Echo Request and Echo Reply packets are used to transport interactive shell traffic instead of their intended diagnostic purpose.


<img width="1132" height="361" alt="image" src="https://github.com/user-attachments/assets/c3e82671-d0c3-49f2-aaa5-cf3e6527cb28" />  



---

## Objectives

- Analyze the packet capture using Wireshark.
- Identify indicators of ICMP tunneling.
- Examine ICMP packet payloads for encapsulated data.



---

## MITRE ATT&CK Mapping

 Tactic | Technique | ID |
|---------|-----------|----|
| Command and Control | Non-Application Layer Protocol | [T1095](https://attack.mitre.org/techniques/T1095/) |



## Analysis Summary

The packet capture demonstrates ICMP traffic that extends beyond normal network diagnostics. Inspection of packet payloads reveals Metasploit framework used, executed commands, and command output transported through ICMP packets.

These observations are consistent with an ICMP tunneling scenario in which ICMP Echo Request and Echo Reply messages are used.

---

## Learning Objectives

After reviewing this repository, readers should be able to:

- Understand how ICMP tunneling works.
- Identify abnormal ICMP communication patterns.
- Analyze ICMP payloads in Wireshark.




