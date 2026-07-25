# Detecting-ICMP-Tunneling-Through-Packet-Analysis
CyberLab-05



## Overview

This repository documents the analysis of a packet capture containing an ICMP tunneling session.  
The objective is to investigate how ICMP Echo Request and Echo Reply packets are used to transport interactive shell traffic instead of their intended diagnostic purpose.



---

## Objectives

- Analyze the packet capture using Wireshark.
- Identify indicators of ICMP tunneling.
- Examine ICMP packet payloads for encapsulated data.


---

## Learning Objectives

After reviewing this repository, readers should be able to:

- Understand how ICMP tunneling works.
- Identify abnormal ICMP communication patterns.
- Analyze ICMP payloads in Wireshark.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | Technique ID |
|---------|-----------|--------------|
| Command and Control | Protocol Tunneling | T1572 |

**Observed behavior**

- Large size ICMP Echo Requests and Replies packets.
- Interactive communication encapsulated within ICMP packets.

---


## Analysis Summary

The packet capture demonstrates ICMP traffic that extends beyond normal network diagnostics. Inspection of packet payloads reveals interactive shell communication, including login prompts, executed commands, and command output transported through ICMP packets.

These observations are consistent with an ICMP tunneling scenario in which ICMP Echo Request and Echo Reply messages are used as a covert communication channel.

A detailed packet-by-packet investigation is available in:

```
analysis/findings.md
```

---

## Indicators Observed

- Repeated ICMP Echo Request and Echo Reply messages.
- Application-layer data embedded within ICMP payloads.
- Interactive shell commands and command output.
- Network behavior consistent with protocol tunneling.

---

## Disclaimer

This packet capture is analyzed to demonstrate network traffic analysis techniques and should not be interpreted as guidance for unauthorized activities.
