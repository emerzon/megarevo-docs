# Megarevo Inverter Setup Parameters

This repository documents Megarevo R-Series Inverter parameters (and rebranded versions such as the EG4 Electronics EG4 8KEXP-240V and VESTWOODS SK-8LNA-A). The goal is to provide a clearer understanding of each parameter and how it affects the inverter's operation.

These parameters are typically accessible from the SolarMan App (either via Remote Control or Local Mode).

## Table of Contents

1. [Basic Settings](#1-basic-settings)
2. [Basic Settings - 2](#2-basic-settings---2)
3. [Battery Settings - Normal](#3-battery-settings---normal)
4. [Battery Settings - Lithium](#4-battery-settings---lithium)
5. [Battery Settings - Lithium - 2](#5-battery-settings---lithium---2)
6. [Battery Settings - Lead-Acid](#6-battery-settings---lead-acid)
7. [Battery Settings - Lead-Acid - 2](#7-battery-settings---lead-acid---2)
8. [Grid Settings - Normal](#8-grid-settings---normal)
9. [Grid Settings - Normal 2](#9-grid-settings---normal-2)
10. [Grid Settings - Custom (When Grid Standard=Custom)](#10-grid-settings---custom-when-grid-standardcustom)
11. [Grid Settings - Connect Parameters](#11-grid-settings---connect-parameters)
12. [Grid Settings - Voltage Protect](#12-grid-settings---voltage-protect)
13. [Grid Settings - Frequency Protect](#13-grid-settings---frequency-protect)
14. [Grid Settings - PU Curve](#14-grid-settings---pu-curve)
15. [Grid Settings - PF Curve](#15-grid-settings---pf-curve)
16. [Grid Settings - Reactive Type](#16-grid-settings---reactive-type)
17. [Grid Settings - QU Curve](#17-grid-settings---qu-curve)
18. [Grid Settings - PQ Curve](#18-grid-settings---pq-curve)
19. [Grid Settings - Voltage Ride-through](#19-grid-settings---voltage-ride-through)
20. [Grid Settings - Detection Protection](#20-grid-settings---detection-protection)
21. [Other Settings](#21-other-settings)
22. [Peakshift Settings](#22-peakshift-settings)
23. [Parallel Set](#23-parallel-set)
24. [Generator Set](#24-generator-set)
25. [Generator Set - 2](#25-generator-set---2)
26. [Advanced Work Mode - Normal (L1,H1,LNA)](#26-advanced-work-mode---normal-l1h1lna)
27. [Advanced Work Mode - Normal (L1,H1,LNA) - 2](#27-advanced-work-mode---normal-l1h1lna---2)
28. [Advanced Work Mode - Normal (G2,H3)](#28-advanced-work-mode---normal-g2h3)
29. [Advanced Work Mode - Time Slot](#29-advanced-work-mode---time-slot)
30. [Advanced Work Mode - Time Slot - 2](#30-advanced-work-mode---time-slot---2)
31. [AC Couple](#31-ac-couple)
32. [Battery Energy Management (Custom)](#32-battery-energy-management-custom)
33. [Battery 485 Communication Parameter (Custom)](#33-battery-485-communication-parameter-custom)

[Glossary](#glossary)

---

**1. Basic Settings**

*   **Sell Enable (true/false):**
    *   **Description:** Determines if the inverter is allowed to send excess power back to the grid.
    *   **Context:** This is a fundamental setting for grid-tied operation.
*   **CT Ratio \[0~30000]:**
    *   **Description:** The ratio of the current transformer (CT) used to measure current flowing to or from the grid or generator.  This allows the inverter to correctly read the values.
    *   **Technical Explanation:** A CT is used to measure AC current by inducing a smaller current in its secondary winding. The ratio is the relationship between the current in the primary and secondary windings. A common ratio would be 1:1000.
*   **Language:**
    *   **Description:**  Selects the display language for the inverter's LCD.
    *   **Options:** Various languages like Chinese, English, and German.
*   **Current Time:**
    *   **Description:** Sets the real-time clock within the inverter.
    *   **Context:** Necessary for time-based functions like peak shifting and time-of-use battery charging/discharging schedules.
*   **Week:**
    *   **Description:** Sets the current day of the week within the inverter.
    *   **Context:** Necessary for time-based functions like peak shifting and time-of-use battery charging/discharging schedules.

**2. Basic Settings - 2**

*   **CT/Meter \[CT, Meter]:**
    *   **Description:** Choose between *CT* when a current transformer is being used, or *Meter* when using a external Meter connected via RS485 interface
    *   **Context:** This should be set depending on your specific setup.

**3. Battery Settings - Normal**

*   **Bat-Type \[DC Source, Lead-Acid, Lithium]:**
    *   **Description:**  Specifies the type of battery connected to the inverter.
    *   **Options:** *DC Source*, *Lead-Acid*, or *Lithium*. Setting this correctly is crucial for proper battery charging and management.
*   **BMS Host \[CAN, 485]:**
    *   **Description:** Selects the communication protocol used between the inverter and battery’s battery management system (BMS).
    *   **Options:** *CAN* (Controller Area Network) or *RS485* (Recommended Standard 485).
*  **Bat Charge Current  \[1~210 A]:**
      *   **Description:** The maximum current that the inverter will use when charging the battery bank.
*   **Bat DisCharge Power Scale \[0~100 %]:**
    *   **Description:** Limits the maximum discharge power of the batteries, as a percentage of the inverter's power capacity.

**4. Battery Settings - Lithium**

*  **Bat On-Grid DOD \[10~100%]:**
     *   **Description:** Sets the Depth of Discharge (DOD) for the battery during on-grid operation.
    *  **Technical Explanation:** Depth of Discharge refers to the percentage of a battery's capacity that has been discharged relative to its full capacity.
*   **Bat Off-Grid DOD \[10~100%]:**
     *   **Description:** Sets the Depth of Discharge (DOD) for the battery during off-grid operation.
*   **OnGrid EodHyst \[0~100%]:**
    *   **Description:** The end-of-discharge hysteresis used in on-grid mode. It is the SOC above the discharge level where the inverter will not discharge the battery.
     *   **Technical Explanation:** Hysteresis prevents constant switching and stabilizes battery discharge behavior.

*   **OffGrid EodHyst \[0~100%]:**
    *    **Description:** The end-of-discharge hysteresis used in off-grid mode.
*   **Wake Up Enable \[true/false]:**
    *   **Description:** If enabled, allows the inverter to send instructions to the BMS to wake up the batteries when it is disconnected, to enable the inverter to charge it
     *   **Context:** Enables the inverter to wake the battery if it has gone to a low state of charge.

**5. Battery Settings - Lithium - 2**
*   **CAN_BMSID \[0~30000]:**
    *  **Description:** Specifies the CAN address of the connected BMS on a system using CAN communications

**6. Battery Settings - Lead-Acid**

*   **Lead-acid Bat Capacity \[50~2000 AH]:**
    *   **Description:** The capacity of the lead-acid battery bank, measured in Amp-hours (Ah).
    *   **Technical Explanation:** Amp-hours (Ah) indicate how much electrical charge a battery can store.
*   **Lead-acid Bat Float Volts \[50~620 V]:**
     *   **Description:** The floating voltage level at which a Lead-acid battery will be maintained, after reaching full charge.
    *   **Technical Explanation:** Float voltage is the steady-state voltage that maintains the battery at full charge, without overcharging it.
*   **Lead-acid Bat Max V \[51~620 V]:**
    *   **Description:** The maximum voltage at which the lead-acid battery can be charged.
*    **Lead-acid Bat Min V \[40~500 V]:**
     *  **Description:** The minimum voltage at which the lead-acid battery will be discharged
**7. Battery Settings - Lead-Acid - 2**
*   **Lead-acid Bat Absorption V \[40~620 V]:**
    *   **Description:** The absorption charging voltage for lead acid batteries. This is the voltage the battery is charged at until it reaches a particular charging current threshold.
  *  **Technical Explanation:** Absorption charge is the stage of charging a Lead Acid battery where it’s charged at a constant voltage and decreasing current to bring the battery closer to full charge

**8. Grid Settings - Normal**

*  **Grid Standard \[AU,AU-W,NZ,UK,PK,KR,PHI,CN,US,THAIL,SA,Custom,POL,EN50549,VDE4105,JPN,ITA,SLO,CZE,SWE,HU,SK,AT,BE,JM]:**
     * **Description:** This selects the local grid standards for electrical operation.
      *  **Options:** A wide range of grid standards including Australia, New Zealand, United Kingdom, and several countries from Europe and Asia. A ‘custom’ options is also provided.

**9. Grid Settings - Normal 2**
*  **American Standard Classification \[UL1741&IEEE1547.2020,Rule21,SDR-UL1741 1,UL1471 SB, UL1741 SA, Heco 2, Puerto Rico]:**
     *  **Description:** Used when operating in North America, this setting dictates compliance with different electrical and interconnection standards.
     *  **Context:** These selections will also change the protection characteristics to comply with the selected standard

**10. Grid Settings - Effective when Grid Standard selecting custom**

*   **Vac Min (Efective when Grid Standard selecting custom) \[150~220 V]:**
    *   **Description:** Sets the minimum AC voltage for the grid when 'Custom' standard is selected.
*   **Vac Max (Efective when Grid Standard selecting custom) \[220~280 V]:**
    *   **Description:** Sets the maximum AC voltage for the grid when 'Custom' standard is selected
*   **Fac Min (Efective when Grid Standard selecting custom) \[40~70 Hz]:**
    *   **Description:** Sets the minimum AC frequency for the grid when 'Custom' standard is selected.
*  **Fac Max (Efective when Grid Standard selecting custom) \[40~70 Hz]:**
     *   **Description:** Sets the maximum AC frequency for the grid when 'Custom' standard is selected.

**11. Grid Settings - ConnectParameters**

These settings control how the inverter interacts with the grid, particularly during reconnection after a grid outage.

*   **ReconnectVoltUp \[80~120 %Un]:**
    *   **Description:** A threshold voltage (expressed as percentage of nominal voltage) that, when reached, initiates the grid reconnection sequence.
*  **ReconnectVoltLow \[80~120 %Un]:**
      *  **Description:** A threshold voltage that, when fallen below, initiates the grid disconnection sequence.
*   **Inv NorRampRate \[0.01~100 %Pn/S]:**
    *   **Description:**  The ramp rate for active power during normal operation when connecting or disconnecting to the grid, expressed as a percentage of nominal power (Pn) per second.
    *   **Technical Explanation:** The ramp rate determines how quickly the inverter increases or decreases its output power.
*   **Inv SoftRampRate \[0.01~100 %Pn/S]:**
    *   **Description:** The ramp rate for active power during a soft start, when connecting to the grid for the first time or after an outage, expressed as a percentage of nominal power (Pn) per second.
*   **grid reconnection time \[0.1~600 S]:**
    *   **Description:** A delay applied before the inverter initiates reconnection with the grid.

**12. Grid Settings - VoltageProtect**

These settings define the inverter's response to abnormal grid voltage conditions.

*   **Vac HV1 Trip \[100~140 %/Vn]:**
    *   **Description:** The first level High-voltage trip point (expressed as percentage of nominal voltage). When the grid voltage reaches this point, the inverter will trip and disconnect to prevent over-voltage
*   **Vac HV2 Trip \[10~150 %/Vn]:**
     *   **Description:** The second level High-voltage trip point (expressed as percentage of nominal voltage). When the grid voltage reaches this point, the inverter will trip and disconnect to prevent over-voltage
*   **Vac HV3 Trip \[100~140 %/Vn]:**
     *   **Description:** The third level High-voltage trip point (expressed as percentage of nominal voltage). When the grid voltage reaches this point, the inverter will trip and disconnect to prevent over-voltage
*   **Vac HV1 ClrTime \[0~300 S]:**
      *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a overvoltage was detected. (Level one setting).
    *  **Technical Explanation:** Clear Time is a setting that defines the wait time after a fault before the system will try to connect again.
*  **Vac HV2 CltTime \[0~300 S]:**
     *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a overvoltage was detected. (Level two setting).
*   **Vac HV3 CltTime \[0~300 S]:**
      *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a overvoltage was detected. (Level three setting).
*  **Vac LV1 Trip \[1~100 %/Vn]:**
      *   **Description:** The first level Low-voltage trip point (expressed as percentage of nominal voltage). When the grid voltage goes below this point, the inverter will trip and disconnect to prevent under-voltage
*  **Vac LV2 Trip \[0.1~100 %/Vn]:**
      *   **Description:** The second level Low-voltage trip point (expressed as percentage of nominal voltage). When the grid voltage goes below this point, the inverter will trip and disconnect to prevent under-voltage
*  **Vac LV3 Trip \[0.1~100 %/Vn]:**
      *   **Description:** The third level Low-voltage trip point (expressed as percentage of nominal voltage). When the grid voltage goes below this point, the inverter will trip and disconnect to prevent under-voltage
*  **Vac LV1 ClrTime \[0~300 S]:**
       *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a undervoltage was detected. (Level one setting).
*   **Vac LV2 CltTime \[0~300 S]:**
     *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a undervoltage was detected. (Level two setting).
*  **Vac LV3 CltTime \[0~300 S]:**
     *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a undervoltage was detected. (Level three setting).

**13. Grid Settings - FrequencyProtect**

These settings define the inverter's response to abnormal grid frequency conditions.

*   **Fac HF1 Trip \[40~70 Hz]:**
    *   **Description:** The first level High-frequency trip point at which the inverter will disconnect.
*   **Fac HF2 Trip \[40~70 Hz]:**
     *  **Description:** The second level High-frequency trip point at which the inverter will disconnect.
*  **Fac HF3 Trip \[40~70 Hz]:**
     *   **Description:** The third level High-frequency trip point at which the inverter will disconnect.
*   **Fac HF1 ClrTime \[0~3000 S]:**
   *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a overfrequency condition was detected. (Level one setting).
*   **Fac HF2 ClrTime \[0~3000 S]:**
     *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a overfrequency condition was detected. (Level two setting).
*   **Fac HF3 ClrTime \[0~3000 S]:**
    *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a overfrequency condition was detected. (Level three setting).
*   **Fac LF1 Trip \[40~70 Hz]:**
   *   **Description:** The first level Low-frequency trip point at which the inverter will disconnect.
*   **Fac LF2 Trip \[40~70 Hz]:**
     *   **Description:** The second level Low-frequency trip point at which the inverter will disconnect.
*   **Fac LF3 Trip \[40~70 Hz]:**
     *   **Description:** The third level Low-frequency trip point at which the inverter will disconnect.
*   **Fac LF1 ClrTime \[0~3000 S]:**
       *    **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a underfrequency condition was detected. (Level one setting).
*   **Fac LF2 CltTime \[0~3000 S]:**
     *   **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a undervoltage condition was detected. (Level two setting).
*  **Fac LF3 CltTime \[0~3000 S]:**
      *    **Description:** A time delay setting that the inverter will wait before attempting to reconnect to the grid if a undervoltage condition was detected. (Level three setting).

**14. Grid Settings - PU Curve**

These settings control how the inverter responds to grid voltage variations when connecting to it.

*   **Generating Voltage Response \[true/false]:**
    *   **Description:** When enabled, the inverter will limit its power output when the voltage is abnormal.
*  **Charging Voltage Response \[true/false]:**
     *   **Description:** When enabled, the inverter will limit battery charging power when the voltage is abnormal.
*   **Vac Pwr Start \[105~115 %/Vn]:**
    *   **Description:**  Start point for the change on active power output in response to voltage changes on the Grid, measured in percentage of nominal voltage.

*    **Vac Pwr Stop \[105~115 %/Vn]:**
    *    **Description:** Stop point for the change on active power output in response to voltage changes on the Grid, measured in percentage of nominal voltage.
*    **Vac Pwr RspTime \[0.01~60 S]:**
     *    **Description:** The time it takes to react to voltage changes on the Grid.

**15. Grid Settings - PF Curve**

These settings control how the inverter responds to grid frequency variations when connecting to it, and their response times.

*  **Generating Frequency Response \[true/false]:**
     *   **Description:** When enabled, the inverter will limit its power output when the frequency is abnormal.
*   **Charging Frequency Response \[true/false]:**
    *   **Description:** When enabled, the inverter will limit battery charging power when the frequency is abnormal.
*  **Fac Pwr HFDb \[0~2 Hz]:**
     *   **Description:** Upper deadband for frequency response when the grid frequency is high.
*  **Fac Pwr HFK \[1~300 %Pn/Hz]:**
     *   **Description:**  High frequency gain for active power regulation, expressed as percentage of nominal power (Pn) per Hz.
*   **Fac Pwr HFRspTime \[0.05~30 S]:**
    *   **Description:** The time it takes to react to high frequency changes on the Grid.
*   **Fac Pwr LFDb \[0~2 Hz]:**
     *   **Description:** Lower deadband for frequency response when the grid frequency is low.
*  **Fac Pwr LFK \[1~200 %Pn/Hz]:**
     *   **Description:**  Low frequency gain for active power regulation, expressed as percentage of nominal power (Pn) per Hz.
*   **Fac Pwr LFRspTime \[0.05~30 S]:**
    *   **Description:** The time it takes to react to low frequency changes on the Grid.
* **Overfrequency recovery dead band \[0~1 Hz]:**
     *   **Description:** The offset value, that when passed when decreasing the frequency, signals to the system to end the limited power function

**16. Grid Settings - Reactive Type**

This section allows to choose the inverter's reactive control mode.

*   **Reactive Type \[PowerFactor, ReactPower, QUWave, QPWave]:**
    *   **Description:** Select the inverter reactive power control type.
    *   **Options**:
        *   *PowerFactor* - Sells back power at a constant power factor.
        *   *ReactPower* - Sells back power at a certain percentage of reactive vs. real power.
        *   *QUWave* -  changes the power factor depending on the grid voltage and the related settings. (Volt-VAR mode)
        *   *QPWave* - Adjusts the power factor depending on how much power the inverter is drawing or selling back (Watt-VAR)
*   **Power Factor \[-1~0.8|0.8~1]:**
     *   **Description:** When Reactive Type is selected as 'Power Factor',  allows selecting the desired Power Factor.
       *   **Technical Explanation:** Power factor is a ratio between real power (watts) and apparent power (volt-amps), It measures how efficiently electrical power is being used.
*   **Reactive Power \[-65~65]:**
    *  **Description:** When Reactive Type is selected as 'Reactive Power', allows selecting the percentage of reactive power vs real power.
       *   **Technical Explanation:** Reactive power is the component of electrical power that does no work but is necessary to supply the electrical system, such as for magnetic fields required by inductors or electric fields required by capacitors.

**17. Grid Settings - QU Curve**

These settings control the voltage-dependent reactive power adjustment, used when Reactive Type is set to *QU Wave*.

*  **Vac VarV1 \[80~120 %]:**
     *   **Description:** The grid voltage setpoint that affects reactive power control at the first level.
*   **Vac VarV2 \[80~120 %]:**
     *   **Description:** The grid voltage setpoint that affects reactive power control at the second level.
*   **Vac VarV3 \[80~120 %]:**
      *   **Description:** The grid voltage setpoint that affects reactive power control at the third level.
*  **Vac VarV4 \[80~120 %]:**
    *   **Description:** The grid voltage setpoint that affects reactive power control at the fourth level.
*   **Vac VarQ1 \[10~45 %]:**
    *   **Description:**  Reactive power percentage at level 1.
*   **Vac VarQ2 \[10~45 %]:**
      *   **Description:**  Reactive power percentage at level 2.
*   **Vac VarQ3 \[10~45 %]:**
     *   **Description:**  Reactive power percentage at level 3.
*  **Vac VarQ4 \[10~45 %]:**
      *  **Description:**  Reactive power percentage at level 4.
 *  **Var Var RspTime \[1~300 S]:**
     *   **Description:**  Response time to achieve the desired reactive power when the grid voltage changes.
*  **lockinPwr \[0~100 %Pmax]:**
     *  **Description:** The Inverter's active power lock-in point. At this power the inverter can start injecting VARs.
*  **lockoutPwr \[0~100 %Pmax]:**
    *   **Description:** The Inverter's active power lock-out point. At this power the inverter will stop injecting VARs.

**18. Grid Settings - PQ Curve**

These settings control the power-dependent reactive power adjustment, used when Reactive Type is set to *QP Wave*.

*   **PQ\_Q1 \[-0.45~0.45]:**
    *  **Description:** First level reactive power setting
*  **PQ\_Q2 \[-0.45~0.45]:**
     *  **Description:** Second level reactive power setting
*   **PQ\_Q3 \[-0.45~0.45]:**
   *    **Description:** Third level reactive power setting
*   **PQ\_Q1' \[-0.45~0.45]:**
    *    **Description:** First level reactive power setting, when the inverter is selling power back to the grid
*   **PQ\_Q2' \[-0.45~0.45]:**
      *  **Description:** Second level reactive power setting, when the inverter is selling power back to the grid
*   **PQ\_Q3' \[-0.45~0.45]:**
     *  **Description:** Third level reactive power setting, when the inverter is selling power back to the grid.
*  **PQ\_response\_time \[0~300 S]:**
     *   **Description:** Response time to achieve the desired reactive power when the active power changes.

**19. Grid Settings - Voltage Ridethrough**

These settings determine whether the inverter should remain connected during voltage fluctuations on the grid.

*   **LVRT enable \[true/false]:**
     *   **Description:** Enables or disables Low Voltage Ride-Through (LVRT) capability.
         *  **Technical Explanation:**  LVRT helps the inverter remain operational during short periods of low grid voltage.
*  **HVRT enable \[true/false]:**
     *   **Description:** Enables or disables High Voltage Ride-Through (HVRT) capability.
        *   **Technical Explanation:**  HVRT helps the inverter remain operational during short periods of high grid voltage.

**20. Grid Settings - Detection Protection**

These settings enable protection and safety features related to the grid:

*   **Active Island Enable \[true/false]:**
     *   **Description:** Enables or disables anti-islanding protection to prevent the inverter to continue feeding the local grid when a grid outage is detected.
*   **Leakage Current Detection Enable \[true/false]:**
    *   **Description:** Enables or disables the detection of leakage current.
     *   **Technical Explanation:** monitors leakage current to prevent electrical accidents.
*   **Insulation Detection Enable \[true/false]:**
    *    **Description:** Enables or disables insulation detection.
        *   **Technical Explanation:** monitors insulation status to prevent electrical accidents.

**21. Other Settings**

These parameters control a range of other functionalities.

*   **CT inversely \[true/false]:**
    *   **Description:** Enables or disables the reverse of the CT. When the CT is installed in reverse, enabling this option will correct the reading.

*   **Zero Export Power \[-500~500]:**
    *   **Description:** Used in zero export mode to ensure that no excess power is sent back to the grid. A positive input takes power from the grid, and a negative input sells power to the grid.

*  **home load enable \[true/false]:**
     *   **Description:** Enables or disables an home load port.
*   **no bat func \[true/false]:**
    *   **Description:** When enabled, the system can operate without a battery connected to it.

*   **BMS Aux manage \[true/false]:**
   *   **Description:** Allows the Inverter to manage the battery aux pins if supported by the BMS.
*   **BatLowCap Standby \[true/false]:**
    *   **Description:** If enabled, will put the inverter into standby when a low-battery alarm is triggered.
*  **Forced OffGrid \[true/false]:**
     *   **Description:** Enables the Forced Off-Grid mode. *See Work Mode FORC OFFGRID in Chapter 3.3 for more details*
*   **RSD Button En \[true/false]:**
    *   **Description:** Enable or Disable RSD button
 *   **ARC Enable \[true/false]:**
     *  **Description:** Enable or disable ARC detection function
*   **Ban Fast Check of Grid Voltage \[true/false]:**
    *   **Description:** When enabled, the fast checking of Grid Voltage will be disabled to prevent false alarms.
*  **10Min Over Volt \[true/false]:**
    *  **Description:** Enables or disables 10-minute average voltage checks.
*   **Test Cmd2-Bit3 \[true/false]:**
     *  **Description:** Debug parameter, should be set to default
*  **Test Cmd2-Bit5 \[true/false]:**
    *  **Description:** Debug parameter, should be set to default
*  **Test Cmd2-Bit8 \[true/false]:**
    *    **Description:** Debug parameter, should be set to default
*  **Test Cmd2-Bit9 \[true/false]:**
    *  **Description:** Debug parameter, should be set to default
*   **Cancel Battery

---

## Glossary

### Current Transformer (CT) and CT Ratio  
**Description:** A CT measures AC current and provides a scaled-down current reading for the inverter’s monitoring system. The CT ratio ensures accurate measurement of current flow.  
**Context:**  
- **CT Ratio Setting:** Must be configured based on the physical CT’s specifications.  
- Used to monitor energy flow in grid-tied or hybrid systems.  

### Depth of Discharge (DOD)  
**Description:** Refers to how much of the battery’s capacity has been used. A higher DOD means more usage, potentially reducing battery lifespan.  
**Context:**  
- *On-Grid DOD:* Directly sets how low the battery can discharge when grid-connected.  
- *Off-Grid DOD:* Governs discharge behavior when the system is not grid-connected.

### Low Voltage Ride-Through (LVRT) and High Voltage Ride-Through (HVRT)  
**Description:** LVRT allows the inverter to remain connected during short periods of low voltage, while HVRT handles brief overvoltage events.  
**Context:**  
- Ensures compliance with modern grid codes.  
- Helps maintain grid stability during voltage disturbances.

### Reactive Power Control  
**Description:** Manages VAR (Volt-Amp Reactive) output to maintain grid stability and compliance with local utility requirements.  
**Context:**  
- *Volt-VAR (QU Wave):* Adjusts reactive power based on grid voltage.  
- *Watt-VAR (QP Wave):* Adjusts reactive power based on active power output.  
- Used to support grid conditions and meet regulatory requirements.

### Absorption Voltage and Float Voltage  
**Description:**  
- **Absorption Voltage:** The voltage at which the battery is held after bulk charging to ensure it reaches full capacity.  
- **Float Voltage:** A lower voltage used to maintain a fully charged battery without overcharging.  
**Context:**  
- *Absorption Voltage:* Defines the charging stage where the current begins to taper off.  
- *Float Voltage:* Used for long-term maintenance charging of batteries.

### Hysteresis  
**Description:** Prevents rapid on/off switching by introducing a buffer zone, reducing wear and tear on components.  
**Context:**  
- *OnGrid EodHyst:* Adds a buffer to prevent frequent discharge/recharge cycles.  
- *Grid EodHyst in Advanced Work Modes:* Ensures smoother transitions in grid-interactive systems.

---

[Back to Top](#table-of-contents)
