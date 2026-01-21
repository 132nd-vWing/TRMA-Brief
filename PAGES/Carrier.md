
# Carrier Information

- Always refer to **132-TTP-19 132nd Carrier Operations** for detailed procedures. 

## Blue Carrier 
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

## Red Carrier 
**N/A**  

# Carrier Control
## Cycle Overview

- TRMA Carrier operations are controller by the carrier script and is linked to **Realtime UTC**, this allows the standard realtime planning model used in the wing. The carrier script controls the recovery cycle, carrier lighting, recovery tanker and CASE II/III Marshal stack. It includes an F10 Options menu tree for user interaction. The function of this system is restricted by DCS and MOOSE capability.  

## Carrier Information 
*(F10 Options > Carrier Control > Carrier Information)*

**Weather and light conditions**
- Conditions are scanned every 30 minutes using the carriers current location as a reference to ensure localised accuracy. These determine the Recovery parameters with an attempt to match NATOPS parameters where possible. 
- *Night* is defined as sunset+15min to sunrise-15min.  

**Carrier / Recovery Heading**
- *Final Bearing (FB)* will be within 5 degrees of the wind direction to provide optimal landing conditions and wind over the deck of 20 knots.  
- *Base Recovery Course (BRC)* is derived from final bearing.

**Carrier Illumination**
- is configured automatically to match the carrier current state. When downwind navigation lights only, while turning upwind launch lights, recovery lights for the open recovery window until the carrier turns downwind. 

**Recovery Window (minute past the hour)**  
- The carrier will be upwind and on course from window open to window close. 
  - 30 - window opens, carrier configured for recovery. Broadcasted to CCA at minute 20. 
  - 55 - window closes. Briadcasted to CCA at close. 
- The carrier will remain on BRC for a further 2 minutes before its turn downwind.
- Recovery lighting including IFLOLS will only be on during the recovery window. 

**Recovery Tanker** 
- A recovery tanker will be launched when the recovery window opens. This will air launch to avoid deck crew conflict. The training tanker will remain indefinately.


## Case II/III Marshal Stack  
*(F10 Options > Carrier Control > Marshal Options)*

- This replaces the DCS ATC system and is used during CASE II/III operations when no controller is present, this is because ATC is based on game time and UTC which creates confusion. 

**The Marshal Stack**  
- Radials are offset from final bearing reciprocal. 0, +/-15 +/-30 
- Each radial has 4 slots 6/21, 7/22, 8/23, 9/24. 
- Slots assignments are fixed once assigned.
- Slots are released 3 minutes after a successful approach. 
- The queue can be joined between :00 and :45. (:45 is the last possible queue entry for a current window.)

**Approach Time**  
- Approach times are allocated from the possible window. (from >= open-5 until =< close-7). 
- On request approach times will always be at least 3 minutes in the future, to allow for positioning. 
- Approach times are unique to each queueing pilot. 
- Approach times can be updated should you be unable to achieve the first allocation, but the logic is simple, so it might result in an earlier time. 

**Modex Menus**  
*(F10 Options > Carrier Control > Marshal Options > 31X > 315 > Join/Leave/Show) [Broadcasted to CAA]*

- The menu tree includes a Modex specific menu that offers individual Join, Leave, Show and Update Approach Time options. 



## Carrier Admin Menu
*(F10 Options > Carrier Control > Carrier Admin ) [for debug and admin use only]*

**Window vs Cycle**  

- The recovery cycle includes the carrier manoeuvres and the recovery window from *turn-into-the-wind* to *turn-out-of-the-wind*. This is currently 37 minutes long starting at minutes 20 each hour.  
- minute 20 : carrier turns into the wind, this can take 10 minutes with the escort ships frequently causing course corrections. 
- minute 30 : recovery window opens. 
- minute 55 : recovery window closes. 
- minute 57 : carrier turns downwind
- Recovery lighting including IFLOLS will only be on during the recovery window. 

**Cycle Extensions**  
- The stardard recovery cycle can be extended in 5 minute increments, this pushes the cycle times out for the sum of the increments. All time links will be extended as well.

**Manual Starts**  
- Start CQ 90 recovery can be started at any time. The cycle is 90 minutes, which includes the 10m turn-in and 2 minute close-turn-out buffer.   
- Start Recovery Now overrides the standard timing and starts a recovery cycle immediated.  
- Manual cycles cannot be extended because they will not be UTC aligned, and standard cycles must be resumed as soon as possible.

**Recovery Tanker Control**
- The recovery tanker spawns on the first recovery cycle and remains airborne indefinately. 
- If required the menu item can be used to stop/start the tanker.   

**Marshall Queue Options**
- Show Queue is used to list the 9 soonest queue slots. They are sorted chronologically. (currently sorted by modex will be fixed)
- Clear Marshal Queue will empty the current queue. 
- Note the DCS limits the number of lines visible, and to avoid generating load, only the soonest 9 approaches will be show.  

```
Current Marshall Queue
Expect Final Bearing 352, QNH 3001
Hornet 311, Marshall from Mother at 343/22, at Angels 7. Pushtime Minute 31.
Tomcat 201, Marshall from Mother at 343/23, at Angels 8. Pushtime Minute 32.
Hornet 302, Marshall from Mother at 343/24, at Angels 9. Pushtime Minute 33.
```

**Carrier Lights**
- OFF - no lights. It is safest to always use OFF before another state, with 20-30 second delay between. 
- NAV - ships navigation lights. The deck is dark.
- LAUNCH - bow and waist flood lights and taxi lights. The deck is bright. 
- RECOVER - deck lights, taxi and navigation lights only, minimal floods. 
- **IMPORTANT: ALWAYS USE "OFF" AFTER "RECOVERY", failure to do this will result in the IFLOLS being disabled permanently** 

## Carrier Option Menu Tree
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
    │   ├── Clear Marshal Stack (DEBUG)
    │   └── Set Carrier Lights
    │       └── [ OFF / NAV / LAUNCH / RECOVER ]
    └── Marshal Options
        ├── Panthers
        │   └── [Contains options for adding/removing/updating flights 300-339]
        │        └── [ JOIN / LEAVE / SHOW / UPDATE ]
        └── Spectres
            └── [Contains options for adding/removing/updating flights 200-229]
                 └── [ JOIN / LEAVE / SHOW / UPDATE ]

[Back to frontpage](https://132nd-vwing.github.io/TRMA_Brief/)
