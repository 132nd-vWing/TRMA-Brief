
# Carrier Information

- Always refer to **132-TTP-19 132nd Carrier Operations** for detailed procedures. 

### Blue Carrier 
**CVN-73 George Washington**
- **TACAN**: 13X, identifier "T73"
- **ICLS**: 13, identifier "I73"
- **Datalink**: 331 MHz, identifier "A73"
- **ACLS**: Activated on 331 MHz, identifier "A73"
- **Marshal**: 309.2 Mhz, callsign "Warfighter"
- **Tower**: 309.1 Mhz
- **Carrier ATC AI**: 309.5 MHz (AI ATC interaction only, no human comms)

- **Recovery Tanker TACAN**: Channel 64Y, identifier "SH7"
- **Recovery Tanker Radio Frequency**: 282.5 MHz

- **Recovery Window**: XX:30 - XX:55 Realtime UTC

### Red Carrier 
**N/A**  

<br><br>

# Carrier Control
### Cycle Overview

- TRMA Carrier operations are controller by the carrier script and is linked to **Realtime UTC**, this allows the standard realtime planning model used in the wing. The carrier script controls the recovery cycle, carrier lighting, recovery tanker and CASE II/III Marshal stack. It includes an F10 Options menu tree for user interaction. The function of this system is restricted by DCS and MOOSE capability.  

### Carrier Information 
*(F10 Options > Carrier Control > Carrier Information) [Broadcasted to CCA]*

**Weather and light conditions**
- Conditions are scanned every 30 minutes using the carriers current location as a reference to ensure localised accuracy. These determine the Recovery parameters with an attempt to match NATOPS parameters where possible. 
- *Night* is defined as sunset+15min to sunrise-15min.  

**Carrier / Recovery Heading**
- Due to some complexity in the way MOOSE deal woith turning into the wind, we have simplified this for the meantime. 
- *Base Recovery Course (BRC)* is derived from wind direction. 
- *Final Bearing (FB)* is BRC-9, therefore there will be slight crosswind. 

**Carrier Illumination**
- is configured automatically to match the carrier current state. When downwind navigation lights only, while turning upwind launch lights, recovery lights for the open recovery window until the carrier turns downwind. 

**Recovery Window (minute past the hour)**  
- The carrier will be upwind and on course from window open to window close. 
  - :30 - window opens, carrier configured for recovery. Broadcasted to CCA at minute 20. 
  - :55 - window closes. Broadcasted to CCA at close. 
- The carrier will remain on BRC for a further 2 minutes before its turn downwind.
- Recovery lighting including IFLOLS will only be on during the recovery window. 

**Recovery Tanker** 
- A recovery tanker will be launched when the recovery window opens. This will air launch to avoid deck crew conflict. The recovery tanker will remain airborne indefinately.

### Case II/III Marshal Stack  
- This replaces the DCS ATC system and is used during CASE II/III operations when no controller is present, this is because ATC is based on game time and not UTC which creates confusion. 

**The Marshal Stack**  
- Radials are offset from final bearing reciprocal. 0, +/-15, +/-30 
- Each radial has 4 slots 6/21, 7/22, 8/23, 9/24. 
- The stack supports 20 slots. 
- Slots assignments are fixed once assigned.
- Slots are released 3 minutes after commencing. 
- The queue can be joined between :00 and :47. (:50 is the last possible approach)

**Approach Time**  
- Approach times are allocated from times between ">= open-5" and "<= close-5". 
- Approach times are allocated no more that now+3 to allow for positioning. 
- Approach times are unique to each queueing pilot. 
- Updated approachtimes can be requested, it will always be in the future, if a new time is not available the update reuqest will be denied. 

### Marshal Options Menus
*(F10 Options > Carrier Control > Marshal Options)* 

**Options**
- Set my Modex - One time modex registration. Once done the server should remember. If you change your PlayerName re-register. This is persistent. 
- Join/Leave - client specific triggers with player only responses. 
- Show My Marshal Info - repeats your marshal call. 
- Update Approach Time - assigns you a later approach time, if available. 
- Show Marshal Stack - show sthe entire stack (BROADCASTED TO CCA). eg below. 

```
Current Marshall Queue
Expect Final Bearing 352, QNH 3001
311, Mother 343 / 22 angels 7 approach 31
201, Mother 343 / 23 angels 8 approach 32
302, Mother 343 / 24 angels 9 approach 33
```
### Carrier Admin Menu
*(F10 Options > Carrier Control > Carrier Admin )*

**Window vs Cycle**  
- The recovery cycle includes the carrier manoeuvres and the recovery window from *turn-into-the-wind* to *turn-out-of-the-wind*. This is currently 37 minutes long starting at minutes 20 each hour.  
- :20 - carrier turns into the wind, this can take 10 minutes with the escort ships frequently causing course corrections. 
- :30 - recovery window opens. 
- :55 - recovery window closes. 
- :57 - carrier turns downwind
- Recovery lighting including IFLOLS will only be on during the recovery window. 

**Cycle Extensions**  
- Any recovery cycle can be extended in 5 minute increments, this pushes the cycle times out for the sum of the increments.

**Options**  
- Schedule CQ Recovery - converts the next Recovery to carrier Qual (90 minutes)   
- Start/Stop Recovery Tanker - do one or the other depending on tanker state. 
- Configure Carrier Lights - See below

**Carrier Lights**
- Light changes can take up to 30 seconds, do not spam these items. 
- OFF - no lights. 
- NAV - ships navigation lights. The deck is dark.
- LAUNCH - bow and waist flood lights and taxi lights. The deck is bright. 
- RECOVER - deck lights, taxi and navigation lights only, minimal floods. 
- **IMPORTANT: WHEN TRANSITIONING FROM "RECOVERY LIGHTING" ALWAYS SWITCH "OFF" FIRST. Failure to do this will result in the IFLOLS being disabled permanently** 

### Carrier Option Menu Tree

- F10 Other >
  - Carrier Control
    - Carrier Information
    - Marshal Options
      - Join Queue
      - Leave Queue
      - Show my Info
      - Update Approach Time
      -\-\-\-
      - Set my Modex  
        - Panthers  
          - [Contains options for adding/removing/updating flights 300–339]  
            - Register MODEX
        - Spectres  
          - [Contains options for adding/removing/updating flights 200–229]  
            - Register MODEX
    - Carrier Admin
      - Extend current cycle 5m  (During window only)
      - Start CQ Cycle 
      - Start/Stop Recovery Tanker
      - Set Carrier Lights  
        - [ OFF / NAV / LAUNCH / RECOVER ]
    -\-\-\-
    - Carrier Debug  
      - Start Recovery Cycle NOW
      - Debug Report
      - Clear Marshal Stack 
      - Identify My Aircraft
      - Old Marshal Options


[Back to frontpage](https://132nd-vwing.github.io/TRMA_Brief/)
