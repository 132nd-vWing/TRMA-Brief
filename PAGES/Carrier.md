
# TRMA CVN-73 Carrier Control George Washington

Welcome to the CVN-73 carrier operations! This guide explains how the carrier operates automatically and how you, as a pilot, can interact with it during recovery operations.  
Please note, all timings referenced here are in **real time**, not game time, meaning that they correspond to the actual time of the server PC hosting the mission.  
For detailed descriptions of Special Operating Procedures during Carrier Operations within the 132nd Virtual Wing, please refer to **132-TTP-19**.

## Navigation and Communication Information

- **TACAN**: Channel 13X, identifier "T73"
- **ICLS**: Channel 13, identifier "I73"
- **Datalink**: 331 MHz, identifier "A73"
- **ACLS**: Activated on 331 MHz, identifier "A73"
- **Recovery Tanker Radio Frequency**: 282.5 MHz
- **Recovery Tanker TACAN**: Channel 64Y, identifier "SH1"
- **Carrier AI Frequency**: 309.5 MHz

> **Note**: Carrier AI Frequency is NOT monitored, and no calls are made on this frequency. The sole purpose of the AI Frequency is to activate ACLS functionality if pilots choose to do so.

## Cyclic Operations

- **Timing**: CVN-73 opens a recovery window at **20 minutes past every hour (real time)**. For example, a recovery window would start at 14:20, 15:20, and so on.
- **Duration**: Each recovery window remains open for **35 minutes**, providing a dedicated period for aircraft to land on the carrier.
- During this time, the carrier will turn into the wind, creating ideal conditions for safe landings.

> **Note**: At minute 20, the carrier will start its turn into the wind. Depending on weather and current carrier heading, the turn can take up to 5 minutes to complete.

## Short Description of the Communication Flow (detailed instructions in **132-TTP-19**)

### Departure
- Monitor Tower Freq (309.100) and do all radio calls on Tower until after the Departure, then switch to Marshall freq (309.200).  
  **Do NOT use the carrier AI Freq (309.500)**.

### Recovery
- Before entering the Marshall Area, give a radio call to Marshall on 309.200 to check in.  
  **Do NOT use the AI Freq, do NOT use the ED ATC**.  

- **Stay on Marshall Freq from the time of Checkin until AFTER you announced 'Modex xxx, Commencing', THEN switch to Tower.**

### CASE I
- AFTER the Commence call (on Marshall), switch to Tower (309.100).  
  Your next call will be 'Modex xxx, Initials', then the Ball call.  
  Other pilots, do not transmit when another has called the Ball, until they report 'Green Deck'.

### CASE III
- If a human Marshall Controller is present, work with them.  
  If not, use the script (outline below) to add your Modex to the Marshall Queue.
- Call 'Modex xxx, Established' when you enter your assigned holding.
- At your assigned Push Time, call 'Modex xxx, Commencing' on Marshall Freq.  
  If you cannot meet your Push Time, announce it on Marshall so other pilots can adjust their timings accordingly, or leave the Marshall stack and re-enter to get a new hold and time assigned at the end of the queue.
- AFTER your Commence call, switch to Tower (309.100).  
  Your next call will be 'Modex xxx, Platform'. Make all further calls on Tower Freq unless you have to enter Marshalling again.

> **Note**: For ACLS functionality, in DCS, ACLS relies on checking in with the ED ATC.  
If you intend to use ACLS, use the ED ATC menu to make your call on AI Freq (309.500), but switch back to the correct frequency (Marshall or Tower) ASAP.  
No calls are made on AI Freq, as this is not monitored by anyone.

## Recovery Tanker Support

A recovery tanker will be launched when the recovery window opens. Please leave room on the deck for the tanker to taxi to the catapult and allow the recovery tanker to launch as the first plane.  
The tanker will remain airborne until the end of the recovery window, when it will return to base. There is a delay for the tanker to recover, so it should be the last plane to land.

## Player Menu Options to interact with the Carrier

```markdown
F10 Menu other/
└── Carrier Control
    ├── CVN-73 Carrier Information
    ├── CVN-73 Admin
    │   ├── Extend current recovery window by 5 Minutes (only if recovery is active)
    │   ├── Debug: Start Cycle Manually
    │   ├── Clear Marshall Queue
    │   ├── Set Case I
    │   ├── Set Case II
    │   └── Set Case III
    │   └── Auto-set Carrier ATIS
    ├── CVN-73 CASE II/III Marshall
    │   ├── Display the Marshall Stack
    │   ├── Panthers
    │   │   └── [Contains options for adding/removing flights 300-326]
    │   └── Spectres
    │       └── [Contains options for adding/removing flights 200-226]
```

This is an overview of the menu tree accessible to the pilots. Please note the carrier will reply or send information only to pilots currently within the Marshalling Area (50nm around the boat).  
If you do not get a reply from the Carrier, get within the Marshall Area, then try again.

## CVN-73 Carrier Information

Provides real-time updates on the carrier's current state:
- Whether a cycle is open.
- The heading of the carrier.
- Information about the wind direction and wind speed over the deck.
- Expected **Final Bearing (FB)** and **QNH** (pressure setting).
- ATIS including QNH

> **Note**: You will know when the carrier has finished its turn when the reported carrier heading equals the expected BRC as reported by the Carrier Information menu.

## CVN-73 Admin

- **Extend current recovery window by 5 Minutes**: This option will only appear when a cycle is open. You can delay the time before the carrier ends the cycle by 5 minutes when you activate this functionality.  
  This can be called multiple times if required. The new window end time will be updated accordingly and can be retrieved by the CVN-73 Carrier Information function.

### Debug: Start Cycle Manually

- This is for testing and own training only, not to be used in 132nd Training events unless allowed by the event host.  
  This will make the carrier turn immediately and open a new cycle with the standard duration.

### Clear Marshall Queue

- This is also for testing and problem-solving. This will kick everyone from the **CASE II/CASE III Marshall Stack** (see functionality described below).

### Set Case x

- This can be used to configure the Carrier for a CASE I/II/III recovery, to update the expected/active CASE X recovery when Carrier Information is selected

### Auto-set Carrier ATIS

- This can be used to configure the Carrier for a CASE I/II/III automatically dependeing on DCS weather. The weather infromation is not very reliable and you may still have to set the case via the manual menu 'Set Case X'.

## CVN-73 CASE II/III Marshall

This functionality can be used when **CASE II/III Marshalling** is required and no controllers are present.  
Pilots can add any **Modex** to the Marshall queue; those Modex numbers will then be stacked by the time of being added (first come, first serve).

### Display the Marshall Stack

At any time, all players within the Marshall can request the current Marshall Stack information.  
Here is an example output (Note: as with all Carrier functionality, this will be displayed only within the Marshall Area):

```
Current Marshall Queue:
Expect Final Bearing 352, QNH 3001
Hornet 311, Marshall from Mother at 343/22, at Angels 7. Pushtime Minute 31.
Tomcat 201, Marshall from Mother at 343/23, at Angels 8. Pushtime Minute 32.
Hornet 302, Marshall from Mother at 343/24, at Angels 9. Pushtime Minute 33.
```

## Panthers and Spectres Submenus

Here, pilots can add/remove their (or anyone else's) Modex to/from the Marshall Stack.  
If a number is removed, the stack will collapse and update accordingly.

## Back

[Back to frontpage](https://132nd-vwing.github.io/TRMA_Brief/)
