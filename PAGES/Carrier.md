
# Carrier Information

Always refer to **132-TTP-19 132nd Carrier Operations** for detailed procedures. 

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
TRMA Carrier operations are controller by the carrier script and is linked to **Realtime UTC**, this allows the standard realtime planning model used in the wing. The carrier script controls the recovery cycle, carrier lighting, recovery tanker and CASE II/III Marshal stack. It includes an F10 Options menu tree for user interaction. The function of this system is restricted by DCS and MOOSE capability. 

### Carrier Information 
**Weather and light conditions**  
Conditions are scanned every 30 minutes using the carriers current location as a reference to ensure localised accuracy. These determine the next scheduled recovery parameters with an attempt to match NATOPS parameters where possible.  
 - *Night* is sunset+15min to sunrise-15min.

**Recovery Headings**  
Due to some complexity in the way MOOSE deal with turning into the wind we have simplified this for the meantime. The bearing are however MAGVAR aware. 
- *Base Recovery Course (BRC)* is derived from wind direction. 
- *Final Bearing (FB)* is BRC-9, therefore there will be slight crosswind. 

**Carrier Illumination**  
Lights are configured automatically to match the carrier current state. When downwind navigation lights only, while turning upwind launch lights, recovery lights for the open recovery window until the carrier turns downwind. These can be modified from the menus, changes can take up to 60 seconds to happen on the carrier, be patient.  

**Carrier Lights**
- Light changes can take up to 60 seconds, do not spam these items. 
- OFF - no lights. 
- NAV - ships navigation lights. The deck is dark.
- LAUNCH - bow and waist flood lights and taxi lights. The deck is bright. 
- RECOVER - deck lights, taxi and navigation lights only, minimal floods. 
- **IMPORTANT: WHEN TRANSITIONING FROM "RECOVERY LIGHTING" ALWAYS SWITCH "OFF" FIRST. Failure to do this will result in the IFLOLS being disabled permanently** 

### Recovery
**Recovery Window (minute past the hour)**  
The carrier will be upwind and on course from window open to window close. The carrier will remain on BRC for a further 2 minutes before its turn downwind. Recovery lighting including IFLOLS will only be on during the recovery window. Default timing is:  
- XX:30 - window opens, carrier configured for recovery. 
- XX:55 - window closes.  
The window can be extended by 5m from the menus.

**Special Recovery Windows**  
The menu offers the ability to change the next standard recovery cycle to a CQ cycle, which simple changes the window length from 25m to 85m. Everything adjusts to allow a longer unwind leg. 

**Recovery Tanker**  
A recovery tanker will be launched when the recovery window opens. This will air launch to avoid deck crew conflict. The recovery tanker will remain airborne indefinately. You can start or stop the recovery tanker through the menus. 

### Case II/III Marshal Stack  
This replaces the DCS ATC system and is used during CASE II/III operations when no controller is present, this is because ATC is based on game time and not UTC which creates confusion.

**The Marshal Stack**  
- Radials are offset from final bearing reciprocal. 0, +/-30 
- Each radial has 6 slots 6/21, 7/22, 8/23, 9/24, 10/25, 11/26. 
- The stack supports 18 slots. 
- Slots assignments are fixed once assigned.
- Slots are auto released 3 minutes after commencing. 
- The queue can be joined between 5minutes after the last cycle, until the last valid approach time +3. 

**Approach Time**  
- Approach times are allocated from times between ">= open-5" and "<= close-5". 
- When joining the queue your approach time will be at least 10m from request time. This allows positioning.  
- When requesting an updated approach time, it will be at least 3 minutes from require time as you are already in your 
- Approach times are unique to each queueing pilot, and expect pilots to arrive on FB at 12DME at roughly 1m intervals.  
- If your approach cannot be accomodated this cycle you will not be allocated a new time. 
- Join, Leave, Update the queue through the Marshal Options menus. 

### Carrier Option Menu Tree

- F10 Other >
  - Carrier Control
    - Carrier Information
    - Marshal Options
      - Show Marshal Queue
      - Panthers
        - [MODEX blocks 300–339]  
          - Join Queue
          - Leave Queue
          - Update Approach Time
          - Show My Queue Details
      - Spectres  
        - [Same as Panthers 200-229]
    - Carrier Admin
      - Extend current cycle 5m  (During window only)
      - Schedule CQ Cycle 
      - Start/Stop Recovery Tanker
      - Set Carrier Lights  
        - [ OFF / NAV / LAUNCH / RECOVER ]
    -\-\-\-
    - Carrier Debug  
      - Start Recovery Cycle NOW
      - Debug Report
      - Clear Marshal Stack 

[Back to frontpage](https://132nd-vwing.github.io/TRMA_Brief/)
