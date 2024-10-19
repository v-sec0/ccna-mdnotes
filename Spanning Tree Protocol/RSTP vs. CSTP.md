### Introduction
---
RSTP Port Types
1. Point-to-Point: Automatically assigned to full duplex ports.
2. Shared Port: Automatically assigned to half duplex ports.


RSTP and RPVSTP+ allow for faster convergence compared to the traditional 802.1d. 

It uses RSTP Sync to quickly determine if a link will cause a loop. 

On half-duplex connections, RSTP Sync is disabled. 

### Addressing the Differences 
---
RSPT (802.1w) is more of an evolution of CSTP (802.1d). While maintaining it's backwards compatibility, 802.1w improves the convergence time of CSTP. 

Some changes include:
1. No listening state
2. No timer for the learning state (CSTP uses a 15 second timer.)
3. RSTP Sync for fast convergence

However, there are some terminology changes when it comes to working with 802.1w:

| **CSTP Port**  | **CSTP Port State**   | **RSTP Port**    | **RSTP Port State** |
| -------------- | --------------------- | ---------------- | ------------------- |
| Root           | *Forwarding*          | Root             | *Forwarding*        |
| Designated     | *Forwarding*          | Designated       | *Forwarding*        |
| Non-Designated | *Blocking*            | Alternate/Backup | *Discarding*        |
| Disabled       | *---*                 | Disabled         | *Discarding*        |
| In-transition  | *Listening, Learning* | In-transition    | *Learning*          |

>[!tip]
>An alternative port in RSTP is a blocked port in CSTP. They act as a **standby for the switches Root Port in the event it goes down.** 
>
>While CSTP would take 30 seconds to failover to a blocked port, RSTP failovers immediately.

In RSTP there is also an **backup port** that acts as a standby for a designated port.