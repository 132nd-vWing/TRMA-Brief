
# TRMA CVN-73 Carrier Control George Washington

Welcome to the CVN-73 carrier operations! This guide explains how the carrier operates automatically and how you, as a pilot, can interact with it during recovery operations.  
Please note, all timings referenced here are in **real time UTC**, not game time, meaning that they correspond to the actual time of the server PC hosting the mission.  
For detailed descriptions of Special Operating Procedures during Carrier Operations within the 132nd Virtual Wing, please refer to **132-TTP-19**.

Script update 3.7 in beta. 

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
Cyclic operations refers to the cyclic launch, recovery and positioning of the carrier, where possible we try to emulate reality as close as possible. 

- **Timing (minute past the hour)**: 
- 20 - cycle start, carrier turns into wind and configured for launch. 
- 30 - window opens, carrier configured for recovery. 
- 55 - window closes.  
- 57 - cycle ends, carrier configured for cruise and turns downwind. 

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

A recovery tanker will be launched when the recovery window opens. This will air launch to avoid deck crew conflict. The training tanker will remain indefinately. It can be disabled/enabled in the admin menu. 

## Player Menu Options to interact with the Carrier
```markdown
F10 Menu other/
└── Carrier Control
    ├── Carrier Information
    ├── Carrier Admin
    │   ├── Start Recovery Cycle NOW (DEBUG) 
    │   ├── Start CQ 90m Cycle NOW
    │   ├── Extend current cycle 5m
    │   ├── Start/Stop Recovery Tanker
    │   ├── Show Marshal Stack
    │   └── Set Carrier Lights
    │       └── [ OFF / NAV / LAUNCH / RECOVER ]
    ├── Marshal Options
    │   ├── Panthers
    │   │   └── [Contains options for adding/removing/updating flights 300-339]
    │   └── Spectres
    │       └── [Contains options for adding/removing/updating flights 200-229]
```

This is an overview of the menu tree accessible to the pilots. Please note the carrier will reply or send information only to pilots currently within the Marshalling Area (50nm around the boat).  
If you do not get a reply from the Carrier, get within the Marshall Area, then try again.

## Carrier Information

Provides real-time updates on the carrier's current state:
- Whether a cycle is open.
- The heading of the carrier.
- Information about the wind direction and wind speed over the deck.
- Expected **Final Bearing (FB)** and **QNH** (pressure setting).

## Carrier Admin Menu

### Manual Starts
the 90 minute CQ training window will start when the menu is selected, it will update Carrier Information accordingly. The 30 minute DEBUG option will be removed. Extended cycles cannot be extended more.

### Extend Cycle
This option will only appear when a cycle is open. You can delay the time before the carrier ends the cycle by 5 minutes when you activate this functionality. This can be called multiple times if required. The new window end time will be updated accordingly and can be retrieved by the CVN-73 Carrier Information function.

### Recovery Tanker
This starts and stops the airspawn recovery tanker. 

### Clear Marshall Queue
This is also for testing and problem-solving. This will kick everyone from the **CASE II/CASE III Marshall Stack** (see functionality described below).

### Carrier Lights
You can control the carrier lights with these options. 
- OFF - no lights. It is safest to always use OFF before another state, with 20-30 second delay between. 
- NAV - ships navigation lights. The deck is dark.
- LAUNCH - bow and waist flood lights and taxi lights. The deck is bright. 
- RECOVER - deck lights, taxi and navigation lights only, minimal floods. 
(note ALWAYS USE OFF AFTER RECOVERY, failure to do this will result in the IFLOLS being disabled permanently)

## Marshall Options
This functionality can be used when **CASE II/III Marshalling** is required and no controllers are present.  
Pilots can add any **Modex** to the Marshall queue; those Modex numbers will then be stacked by the time of being added (first come, first serve)

### The Marshal Stack
- Radials are offset from final bearing reciprocal. 0, +/-15 +/-30 
- Each radial has 4 slots 6/21, 7/22, 8/23, 9/24. 
- Your slots remains static. 
- Your slot is auto cleared 3 minutes after approach, unless you request an update.

### Approach Time
- Approach times are allocated from the possible window ( > open-5 < close-7). 
- On request approach times will always be at least 3 minutes in the future, to allow for positioning. 
- Therefore the latest queue entry is minute 45 (close-7 +3)
- it might be that your approach is denied due to insufficient time. I suggest you tank and get comfortable. 

### Join / Leave 
Adds or removes the modex from the marshal queue and notifies you of your instructions. 

### Show 
Will show your marshal instruction again. 

### Update time
Will assign you a new approach time. It will be a minimum of 3m from now. 

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
Note the DCS limits the number of lines visible, and to avoid generating load, only the soonest 9 approaches will be show. 

## Panthers and Spectres Submenus

Here, pilots can add/remove/show/update their (or anyone else's) Modex to/from the Marshall Stack.  
The stack does not collapse. 

## Back

[Back to frontpage](https://132nd-vwing.github.io/TRMA_Brief/)
