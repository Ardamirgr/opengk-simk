# Hyundai 2.0L Siemens 653056 v2.0

Authored by: Chase Hammargren and  Kostas Anestopoulos


## Categories

- Y Axis (31 items)

- X Axis (19 items)

- IACV & Idle Settings (13 items)

- Engine Error Detection (3 items)

- Fuel (9 items)

- IVVT (11 items)

- Driver's Wish (probably only for AT) (1 items)

- AT Control (3 items)

- Ignition (16 items)

- Volumetric Efficiency (4 items)

- Catalyst Settings (6 items)

- Torque Maps (10 items)

- Exhaust Maps (1 items)

- Engine Warmup (2 items)

- Engine Cooling (1 items)

- Engine Speed (10 items)

- EVAP Control (1 items)

- Sensor Definitions (4 items)

- Identification (7 items)

- KWP IO Patch (1 items)



## Patches


<details>
-	<summary>KWP IOCLID Privilege Escalation</summary>

	Adds a new InputOutputControlByLocalIdentifier, 0xBB, that upon passing to LONG_TERM_ADJUSTMENT, escalates privileges in current diagnostic session to Siemens level

</details>




## Constants


<details>
	<summary>1022B Conf MAF Max</summary>

	c_maf_max

</details>



<details>
	<summary>0x1028C AC Safety Disengage RPM</summary>

	The RPM where the car disengages the AC pulley to prevent damage to the compressor. Might be useful for fast spooling engines e.g forced induction.

</details>



<details>
	<summary>10294 RPM Launch Limit 1</summary>

	Set this the same as launch limit 2

Launch Control Enable 1 & 2 need to be enabled for these limits to work. Launch Limits work best at 4000 RPM and RPM Limit Hysterisis 1 & 2 set to 0 RPM. Lower values of 3500 RPM will work but at a reduced bounce rate.

</details>



<details>
	<summary>0x1011C IVVT Camshaft Setpoint Range Max</summary>

	C_CAM_ADJ_RNG_MAX_IN

Constant Camshaft Adjust Range Max Intake

</details>



<details>
	<summary>102AA RPM Soft Limit</summary>

	Ignition cutoff. Typically 96RPM lower than RPM Hard Limit.

If used with RPM Limit Hysterisis 1 & 2 set to 0 RPM you can set both Soft and Hard Limits to the same RPM value.

</details>



<details>
	<summary>0x1074A Minimum Ambient Pressure for Catalyst Heating</summary>

	c_amp_ad_min_ch

</details>



<details>
	<summary>0x101C6 Maximum Vehicle Speed for Catalyst Heating</summary>

	c_iga_vs_max_ch

</details>



<details>
	<summary>0x100A0 Catalyst Efficiency Monitoring</summary>

	c_conf_cat_eff

</details>



<details>
	<summary>0x100A1 Catalyst Protection</summary>

	c_conf_cp

</details>



<details>
	<summary>0x100A2 Catalyst Protection Diagnosing</summary>

	c_conf_diagcp

</details>



<details>
	<summary>102AB RPM Hard Limit</summary>

	Fuel cutoff. Typically 96RPM higher than RPM Hard Limit.

If used with RPM Limit Hysterisis 1 & 2 set to 0 RPM you can set both Soft and Hard Limits to the same RPM value.

</details>



- 10408 Vehicle Speed Max 1 [Engine Speed]



- 10409 Vehicle Speed Max 2 [Engine Speed]



<details>
	<summary>102B5 RPM Limit Hysterisis 1</summary>

	Set to 0 for fast limiter bounce.
Set to 1 for OEM limiter bounce.

Use in conjuction with RPM Limit Hysterisis 2.

</details>



<details>
	<summary>102B6 RPM Limit Hysterisis 2</summary>

	Set to 0 for fast limiter bounce.
Set to 17 for OEM limiter bounce.

Use in conjuction with RPM Limit Hysterisis 1.

</details>



## Tables


<details>
-	<summary>Platform Version</summary>

	Chassis/Year/Region/Engine

May be used by NGM to identify tune parameters. Example being "Stg2_310I" indicating Stage 2 310.

</details>



<details>
-	<summary>158ED 16x12 8bit Ignition Table Basic ignition angle</summary>

	Degrees of ignition advance for given RPM and engine load range.

X Axis is milligrams per stroke of airflow
Y axis is RPM

</details>



<details>
-	<summary>0x193EC 8x8 8bit  Basic ignition angle IVVT Offset</summary>

	Index: 444  IGA: ip_iga_bas_ofs_ivvt
            IP_IGA_BAS_OFS_IVVT[°CRK] = f(N_32[rpm]), f(MAF_HB[mg/stk])

</details>



<details>
-	<summary>0x15AD5 8x8 8bit Basic Ignition Angle Temperature Correction Factor</summary>

	Index: 89   TQ: IP_IGA_BAS_TEMP_FAC__TIA__TCO
            IP_IGA_BAS_TEMP_FAC[-] = f(TIA[°C], TCO[°C])

</details>



<details>
-	<summary>0x15AA5 8x6 8bit Basis for temperatur correction of IGA_BAS</summary>

	Index: 88   TQ: IP_IGA_BAS_TEMP__N_32__MAF_HB
            IP_IGA_BAS_TEMP[°CRK] = f(N_32[rpm], MAF_HB[mg/stk]

</details>



<details>
-	<summary>19571 12x16 8bit IVVT Offset Injection time at TCO2</summary>

	Index: 381  TI : ip_ti_ofs_ivvt__n__maf
Offset Injection time at TCO2
            IP_TI_OFS_IVVT[-] = f(N[rpm]), f(MAF[mg/stk])

</details>



<details>
-	<summary>0x18EAE 6x6 8bit Intake Camshaft Setpoint at TCO1 Idle</summary>

	Index: 388  TI :IP_CAM_SP_TCO_1_IS_IVVT_IN
Target spread for TCO_1, idle, intake camshaft
           IP_CAM_SP_TCO_1_IS_IVVT_IN[°CRK] = f(N[rpm], MAF_IVVT[mg/stk])

</details>



<details>
-	<summary>0x18FA3 6x6 8bit Intake Camshaft Setpoint at TCO2 Idle</summary>

	Index: 389  TI :IP_CAM_SP_TCO_2_IS_IVVT_IN
Target spread for TCO_2, idle, intake camshaft
           IP_CAM_SP_TCO_2_IS_IVVT_IN[°CRK] = f(N[rpm], MAF_IVVT[mg/stk])

</details>



<details>
-	<summary>0x18ED2 12x16 8bit IVVT Camshaft Setpoint TCO1 Part Load</summary>

	Index: 391  TI :IP_CAM_SP_TCO_1_PL_IVVT_IN
Target spread for TCO_1, part load, intake camshaft
           IP_CAM_SP_TCO_1_PL_IVVT_IN[°CRK] = f(N[rpm], MAF_IVVT[mg/stk])

</details>



<details>
-	<summary>0x18FC6 12x16 8bit IVVT Camshaft Setpoint TCO2 Part Load</summary>

	Index: 392  TI :IP_CAM_SP_TCO_2_PL_IVVT_IN
Target spread for TCO_2, part load, intake camshaft
           IP_CAM_SP_TCO_2_PL_IVVT_IN[°CRK] = f(N[rpm], MAF_IVVT[mg/stk])

</details>



<details>
-	<summary>0x18D39 12x16 8bit IVVT Camshaft Setpoint Stoichiometric Limiting Gradient</summary>

	Index: 397  TI : ID_CAM_SP_AFS_LGRD
Maximum allowed gradient into overlap direction, in and ex
           ID_CAM_SP_AFS_LGRD[°CRK] = f(N[1/min], MAF[mg/stk])

</details>



<details>
-	<summary>15CA5 16x12 8bit basic map for reference ignition angle</summary>

	Degrees of ignition advance for given RPM and engine load range.

X Axis is milligrams per stroke of airflow
Y axis is RPM

</details>



<details>
-	<summary>0x1942C 8x8 8bit Reference ignition angle IVVT Offset</summary>

	Index: 446  IGA: ip_iga_ref_ofs_ivvt
            IP_IGA_REF_OFS_IVVT[°CRK] = f(N_32[rpm]), f(MAF_HB[mg/stk])

</details>



<details>
-	<summary>15B1D 16x12 8bit Base Minimum Ignition Angle Difference</summary>

	Basic minimum ignition angle difference value

</details>



<details>
-	<summary>15270 4x8 8bit IGA correction for re-start in PL (RPL)</summary>

	Index 98: IGA: id_iga_rpl__n__tco
IGA correction for re-start in PL (RPL)
            ID_IGA_RPL[°CRK] = f(N[rpm], TCO[°C]) 

</details>



<details>
-	<summary>15266 4x1 8bit Duration of IGA during non-stationary correction (AT)</summary>

	Index 97: IGA: id_iga_cycnr_tra_knk_at__n
Duration of IGA during non-stationary correction (AT)
            ID_IGA_CYCNR_TRA_KNK_AT[-] = f(N[rpm])

</details>



<details>
-	<summary>15262 4x1 8bit Duration of IGA during non-stationary correction (MT)</summary>

	Index 96: IGA: id_iga_cycnr_tra_knk_at__n
Duration of IGA during non-stationary correction (MT)
            ID_IGA_CYCNR_TRA_KNK_MT[-] = f(N[rpm])

</details>



<details>
-	<summary>1526A 4x1 8bit Spark retard at recognised knocking, Intensity 1</summary>

	Index: 317  KNK: id_iga_dec_knk_1__n_knk
            ID_IGA_DEC_KNK_1[°CRK/720°CRK] = f(N_KNK[rpm])

</details>



<details>
-	<summary>1526D 4x1 8bit Spark retard at recognised knocking, Intensity 2</summary>

	Index: 319  KNK: id_iga_dec_knk_2__n_knk
            ID_IGA_DEC_KNK_2[°CRK/720°CRK] = f(N_KNK[rpm])

</details>



- 0x159AD 8x4 IP_IGA_BAS_AMP_COR [Ignition]



<details>
-	<summary>0x15F81 6x4 Minimum MAF for Cat. Overh. Prev. activation</summary>

	Index: 193
Catalyst protection function

            IP_MAF_MIN_COP[mg/TDC] = f(N[rpm],IGA_COP[°CRK])

</details>



<details>
-	<summary>0x12226 12x16  CPS duty cycle</summary>

	Index 482: CPS duty cycle

IP_CPPWM__FLOW_COR_CPS__PRS_CPS

</details>



<details>
-	<summary>0x169F2 8x8 Warm-up TI correction vs. operating point (MT)</summary>

	Index: 198  INJ_WUP: ip_ti_wup__n__maf
            IP_TI_WUP[-] = f(N[rpm], MAF[mg/stk])

</details>



<details>
-	<summary>0x16A32 8x8 Warm-up TI correction vs. operating point (AT)</summary>

	Index: 199  INJ_WUP: ip_ti_wup_at__n__maf
            IP_TI_WUP_AT[-] = f(N[rpm], MAF[mg/stk])

</details>



<details>
-	<summary>0x12026 16x8 IP_AR_RED_ISA</summary>

	Index: 34
    34:     
Calculation of basic reduced area

            IP_AR_RED_ISA[cm²] = f(OPG_AV_ISA[%], N[rpm])

</details>



<details>
-	<summary>0x12B00 12x6 IP_ISAPWM_ISA[%]</summary>

	Index: 604
   604:     
Idle Speed Actuator Control

            IP_ISAPWM_ISA[%] = f(OPG_SP_ISA[%], VB[V])

</details>



<details>
-	<summary>0x1334C 8x16IP_OPG_SP_MDL_BAS_ISA[%]</summary>

	Index: 614
Idle speed valve opening

            IP_OPG_SP_MDL_BAS_ISA[%] = f(N[rpm], AR_RED_SP_ISA[cm²])

</details>



<details>
-	<summary>0x194C5 8x8  IP_MAF_ADD_ISAPWM [PLACEHOLD]</summary>

	Index: 418  IVVT: 
Idle speed valve opening

            IP_MAF_ADD_ISAPWM[mg/TDC] = f(N_32[rpm], ISAPWM[%])

</details>



<details>
-	<summary>0x15BED 8bit Setpoint spark retard for torque setpoint</summary>

	Index: 107
Setpoint Ignition Angle

            IP_IGA_DIF_SP[°CRK] = f(EFF_IGA_SP[-])

</details>



<details>
-	<summary>0x15BDD 8bit Min. ignition angle vs. exhaust gas temp.</summary>

	Index: 100    
Min. IGA limitation for exhaust gas temp. protection

            IP_IGA_DIF_MIN_TEG[°CRK] = f(TEG_DYN[°C])

</details>



<details>
-	<summary>0x14FD4 16bit Basic ignition angle effiency</summary>

	Index: 82

            IPM_EFF_IGA[-] =f(IGA_DIF[°CRK])

</details>



<details>
-	<summary>10098 Injection Time Multiplier</summary>

	This is a scale factor for the injection pulse width. Can be used to scale injector size up and down. It is not precise as it affects the injector dead times as well.

</details>



<details>
-	<summary>0x189D6 6x8 16bit Idle RPM w/o Load MT</summary>

	Index: 40
Engine Speed Setpoint Calculation
Nominal idle speed w/o additional load on the engine
            IP_N_SP_IS_MT[rpm] = f(TCO[°C], TIA[°C])

</details>



<details>
-	<summary>0x18890 6x4 16bit  RPM Offset for Over Rev. detection during gear change</summary>

	Index 62: IP_N_GEAR_SHIFT_OFS
Engine speed offset for the detection of over speed during gear changes
 IP_N_GEAR_SHIFT_OFS = f(MAF[mg/stk], GEAR[-])

</details>



<details>
-	<summary>*0x18860 4x6 16bit Min permitted deviation between reference N (AJ) and N to detect changes in DT (1->0)</summary>

	Index 63: IP_N_DIF_REF_LPF_AJ_MIN
IP_N_DIF_REF_LPF_AJ_MIN = f(GEAR[rpm], TOIL[øC])

The map defines, based on transmission gear and oil temperature, the minimum allowed difference between the reference engine speed (N AJ) and actual engine speed (N) required to detect a change in drivetrain state from active (1) to inactive (0).

</details>



<details>
-	<summary>0x18854 16bit Max permitted deviation between reference N (AJ) and N to detect changes in DT (1->0)</summary>

	Index 64: IP_N_DIF_REF_LPF_AJ_MAX = f(N_32[rpm])

The map defines the max allowed difference between the reference engine speed (N AJ) and actual engine speed (N) required to detect a change in drivetrain state from active (1) to inactive (0).

</details>



- 0x14104 Basic threshold for misfire detection MT [Engine Error Detection]



- 0x1417C Basic threshold for misfire detection AT [Engine Error Detection]



<details>
-	<summary>0x18844 Diff. Threshold to detect MAF/TPS failure with Algorithm2</summary>

	Index: 538 MAF-TPS rationality check
MAF_MDL_DIF thd.to detect MAF/TPS failure with Algorithm2
            IP_MAF_TPS_PLAUS_DIAG_2[kg/h] = f(N_32[rpm])


</details>



- rpm 16 axis [Y Axis]



- 0x11158 ISA RPM Axis X [Y Axis]



<details>
-	<summary>0x114AC 16bit TEG_DYN 16 axis</summary>

	Exhaust Gas Temp in Celsius

</details>



<details>
-	<summary>0x114CE 16bit EFF_IGA_SP 16 axis</summary>

	Igintion Angle Setpoint

</details>



- 0x110D0 RPM 16 Axis Alt [Y Axis]



- RPM IVVT 16 Axis [Y Axis]



- 0x11262 RPM 12 Axis VE Slope [Y Axis]



- 0x11796 RPM 10 Axis Alt [Y Axis]



- 0x10A92 RPM N32 VE Axis [Y Axis]



- 0x10C98 RPM N32 Torque Axis [Y Axis]



- 0x1125016bit load VE Axis [X Axis]



- rpm 8 axis [Y Axis]



- N_32_IP_IGA_REF_TEMP [Y Axis]



- N_32_IP_TQI [Y Axis]



- N_32 IP_TI_NOT_CAT [Y Axis]



- N_32 IP_WUP_TI [Y Axis]



- LDPM_IGA_DIG__EFF_IGA [Y Axis]



- Torque RPM 16 axis [Y Axis]



- Friction Torque RPM 16 axis [Y Axis]



- 0x10CE0 RPM 6 Axis Catalyst Prot. [Y Axis]



<details>
-	<summary>TCO 6 axis</summary>

	Coolant Temperature

</details>



<details>
-	<summary>TCO IP IGA DIF MIN</summary>

	Coolant Temperature

</details>



<details>
-	<summary>TCO 5 axis Catalyst Heat</summary>

	Coolant Temperature

</details>



<details>
-	<summary>0x1802F TIA 6 axis</summary>

	Input Air Temperature

</details>



- 0x1826C RPM IVVT Idle 6 axis [Y Axis]



- 0x18208 RPM IVVT IGA OFFSET 8 axis [Y Axis]



<details>
-	<summary>0x14FC8 Exh. Temperature influence by ignition angle adjustments</summary>

	Index: 128  kf 82k : ipm_add_teg_iga
            IPM_ADD_TEG_IGA[°C] = f(POW_DIF[kW])

</details>



- iat voltage 16 axis [Y Axis]



<details>
-	<summary>0x10BE0 Load 12 Injection Axis</summary>

	RPM

</details>



<details>
-	<summary>0x18211 Load 8 IGA IVVT OFFSET HB</summary>

	High Byte

</details>



<details>
-	<summary>0x10BCF RPM N32 Injection Axis</summary>

	RPM

</details>



<details>
-	<summary>0x117E6 load 12 axis Fuel</summary>

	milligrams per stroke

</details>



<details>
-	<summary>0x1198C load 12 axis Torque</summary>

	milligrams per stroke

</details>



<details>
-	<summary>0x18288 IVVT load 12 axis</summary>

	milligrams per stroke

</details>



<details>
-	<summary>0x18244 IVVT load gradient 12 axis</summary>

	milligrams per stroke

</details>



<details>
-	<summary>load 8 axis</summary>

	milligrams per stroke

</details>



<details>
-	<summary>POW_DIF [[kNm/s]]</summary>

	Unkown Conversion

</details>



<details>
-	<summary>TIA_IP_IGA_BAS_TEMP_FAC</summary>

	TIA IN C

</details>



<details>
-	<summary>TCO_IP_TQI</summary>

	TCO IN C

</details>



<details>
-	<summary>MAF 12 axis</summary>

	milligrams per stroke

</details>



<details>
-	<summary>MAF_CYL_STK 12 axis</summary>

	milligrams per stroke

</details>



<details>
-	<summary>0x11136 OPG_AV_ISA</summary>

	milligrams per stroke

</details>



<details>
-	<summary>0x1154A OPG_SP_ISA</summary>

	milligrams per stroke

</details>



<details>
-	<summary>0x11648 AR_RED_SP_ISA [[cm²]]</summary>

	AR_RED_SP_ISA [[cm²]]

</details>



<details>
-	<summary>0x18382 8bit Valve Overlap 1</summary>

	CRK degrees

</details>



<details>
-	<summary>0x1827A IVVT load 6 axis</summary>

	milligrams per stroke

</details>



<details>
-	<summary>0x1819C Gear</summary>

	Selected Gear

</details>



<details>
-	<summary>0x11824 load hPA 6 axis</summary>

	hPA

</details>



<details>
-	<summary>AMP_IP_TQI</summary>

	hPA

</details>



<details>
-	<summary>16A72 IAT Definition</summary>

	Intake air temperature  sensor definition

</details>



<details>
-	<summary>166B4 12x16 8bit Closed Loop Injection Correction Factor</summary>

	Index: 151
   151:      
Correction factor basic injection time

            IP_TI_COR[-] = f(N[rpm], MAF[mg/stk])

</details>



<details>
-	<summary>16774 8x8 8bit Closed Loop Injection Idle Correction Factor</summary>

	Index: 152  kf   2: ip_ti_cor_is__n__maf
            IP_TI_COR_IS[-] = f(N[rpm], MAF[mg/stk])

</details>



<details>
-	<summary>0x15539 8x8 8bit VE factor vs IAT</summary>

	Index: 13   IMM: ip_eff_tia_fac
            IP_EFF_TIA_FAC[-] = f(N_32[rpm], MAF[mg/stk])

</details>



<details>
-	<summary>0x1245E 12x8 16bit Offset cylinder air mass flow</summary>

	Index: 15   IMM: ip_eff_vol_ofs
            IP_EFF_VOL_OFS[kg/h] = f(N[rpm], VO[°CRK])

</details>



<details>
-	<summary>0x1252A 12x8 16bit Slope cylinder air mass flow</summary>

	Index: 16   IMM: ip_eff_vol_slop
            IP_EFF_VOL_SLOP[kg/(h*hPa)] = f(N[rpm], VO[°CRK])

</details>



<details>
-	<summary>0x154F9 8x8 8bit VE factor vs TCO</summary>

	Index: 12   IMM: ip_eff_tco_fac
            IP_EFF_TCO_FAC[-] = f(N_32[rpm], MAF[mg/stk])

</details>



<details>
-	<summary>PLACEHOLDER 8x6 8bit Min Eng. Speed for trailing throttle fuel cut activation w/AC on, AT</summary>

	Index: 221  ip_n_min_puc_at__tco__tar_gc
           IP_N_MIN_PUC_AT[rpm] = f(TCO[°C], TAR_GC[-])

TAR_GC = Target Gear Change

</details>



<details>
-	<summary>11B4E 16x16 16bit MAF Definition</summary>

	MAF sensor definition

</details>



<details>
-	<summary>0x12022 8x16 16bit Definition</summary>

	MAF sensor definition

</details>



<details>
-	<summary>Calibration Version</summary>

	This should match the XDF file version.

</details>



<details>
-	<summary>0x18976 6x8 16bit Idle RPM w/o Load AT</summary>

	Index: 41
Engine Speed Setpoint Calculation
Nominal idle speed w/o additional load on the engine
            IP_N_SP_IS_AT[rpm] = f(TCO[°C], TIA[°C])

</details>



<details>
-	<summary>0x1864E 6x8 16bit Idle RPM with Drive engaged AT</summary>

	Index: 42
Engine Speed Setpoint Calculation
Nominal idle speed with Drive Engages on the engine
            IP_DRI_N_SP_IS[rpm] = f(TCO[°C], TIA[°C])

</details>



<details>
-	<summary>0x184BC 6x8 16bit Idle RPM with A/C MT</summary>

	Index: 43
Engine Speed Setpoint Calculation
Nominal idle speed w/ air conditioning
          IP_ACIN_N_SP_IS_MT[rpm] = f(TCO[°C], TIA[°C])

</details>



<details>
-	<summary>0x186BA 6x8 16bit Idle RPM with A/C AT</summary>

	Index: 45
Engine Speed Setpoint Calculation
Nominal idle speed w/ air conditioning
         IP_ACIN_N_SP_IS_AT[rpm] = f(TCO[°C], TIA[°C])

</details>



<details>
-	<summary>0x1864E 6x8 16bit Idle RPM with A/C and Drive Engaged AT</summary>

	Index: 45
Engine Speed Setpoint Calculation
Nominal idle speed w/ air conditioning and drive engaged
        IP_DRI_ACIN_N_SP_IS[rpm] = f(TCO[°C], TIA[°C])

</details>



<details>
-	<summary>0x1892E 6x5 16bit Idle RPM Additive Factor for Catalyst Heating MT</summary>

	Index: 48
Additive term on nominal idle speed when CH function is active for MT
       IP_N_SP_ADD_CAT_MT[rpm] = f(TCO[°C], AMP[hPa])

</details>



<details>
-	<summary>0x188FC 5x5 16bit Idle RPM Additive Factor for Catalyst Heating AT | Drive</summary>

	Index: 47   TQ: IP_N_SP_ADD_CAT_AT_DRI
            IP_N_SP_ADD_CAT_AT_DRI[rpm] = f(TCO[°C], T_AST[s])
Additive term on nominal idle speed when CH function is active for AT if LV_DRI = 1

</details>



<details>
-	<summary>0x188C0 6x5 16bit Idle RPM Additive Factor for Catalyst Heating AT | Not Drive</summary>

	Index: 46   TQ: IP_N_SP_ADD_CAT_AT
            IP_N_SP_ADD_CAT_AT[rpm] = f(TCO[°C], AMP[hPa])
Additive term on nominal idle speed when CH function is active for AT if LV_DRI = 0

</details>



- Machine Code Version [Identification]



<details>
-	<summary>ECM Number & Index</summary>

	Printed on ECM label

</details>



<details>
-	<summary>Serial</summary>

	Last 4 digits are printed on ECM label

</details>



<details>
-	<summary>Manufacture Date</summary>

	Printed on ECM label

</details>



<details>
-	<summary>VIN Number</summary>

	May be blank with zeros or ÿ for years 2002-2004.

</details>



<details>
-	<summary>168CE 6x16 8bit WOT Enrichment</summary>

	Conversion value UNKNOWN

Increase to enrichen fuel and decrease to lean fuel under full load WOT condition at a given RPM. Use WOT TPS Trigger table to set TPS angle for full load WOT detection.

</details>



<details>
-	<summary>168CE 6x16 8bit WOT Enrichment | AFR Target (EXPERIMENTAL)</summary>

	Conversion value UNKNOWN

Increase to enrichen fuel and decrease to lean fuel under full load WOT condition at a given RPM. Use WOT TPS Trigger table to set TPS angle for full load WOT detection.

</details>



<details>
-	<summary>0x1692E 6x6 8bit TI correction without catalyst</summary>

	Index: 213  kf  27: ip_ti_not_cat__n__maf
            IP_TI_NOT_CAT[-] = f(N[rpm], MAF[mg/stk])

</details>



<details>
-	<summary>154C7 1x16 8bit WOT TPS Trigger</summary>

	Conversion value is estimated and not exact.

Sets minimum TPS angle for full load WOT condition. Use WOT Enrichment table to adjust enrichment factor.

</details>



<details>
-	<summary>0x18E27 1x16 8bit IVVT Full Load TPS Trigger</summary>

	Index: 394  IVVT: ID_PV_AV_FL_IVVT
            PV-threshold to control IVVT at high load
            ID_PV_AV_FL_IVVT[%] = f(N[rpm])

</details>



<details>
-	<summary>0x18E9E 1x16 8bit IVVT Full Load Camshaft Setpoint TCO1</summary>

	Index 395: IP_CAM_SP_TCO_1_FL_IVVT_IN          
            Target spread at TCO_1, high load, intake camshaft
             IP_CAM_SP_TCO_1_FL_IVVT_IN[°CRK] = f(N[rpm])

</details>



<details>
-	<summary>0x18F92 1x16 8bit IVVT Full Load Camshaft Setpoint TCO2</summary>

	Index 396: IP_CAM_SP_TCO_2_FL_IVVT_IN          
            Target spread at TCO_2, high load, intake camshaft
             IP_CAM_SP_TCO_2_FL_IVVT_IN[°CRK] = f(N[rpm])

</details>



<details>
-	<summary>0x1946C 1x5 8bit IVVT Adhesion Detector Active Counter</summary>

	Index: 434  IVVT: IP_IVVTHPWM_ADH_CYC_IN
            IP_IVVTHPWM_ADH_CYC_IN[-] = f(CAM_DIF_IN[°CRK])
 Map for cycle counter STATE_IVVT_ADJ if adhesion detection is active (inlet)


</details>



<details>
-	<summary>10371 Launch Control Enable 1</summary>

	To enable launch control, set value to 104.
To disable launch control, set value to 177.

Launch Control Enable 2 is also required.

</details>



<details>
-	<summary>106EE Launch Control Enable 2</summary>

	To enable launch control, set value to 1 & 0.
To disable launch control, set value to 104 & 16.

Launch Control Enable 1 is also required.

</details>



<details>
-	<summary>18002 Radiator Fan Trigger Temperature</summary>

	Conversion equation is UNKNOWN.

Set first value to 189 for OEM trigger temp of about 193F.
Set first value to 171 for a trigger temp of about 175F.

First value is initial fan trigger temperature. 
Second and third values are unknown. These other values likely middle and high overheat shutdown trigger temps to enable an ignition or fuel strategy to save the motor from damage.

</details>



- inj volt 8 axis [Y Axis]



- VB [Y Axis]



- 1661C Injection Dead Times [Fuel]



<details>
-	<summary>*0x129F8 8x8 16bitIP_FAC_TQ_REQ_DRIV_AT</summary>

	Index: 649  TQ: IP_FAC_TQ_REQ_DRIV_AT

            IP_FAC_TQ_REQ_DRIV_AT[-] = f(N[rpm], PV_AV_H[%])


</details>



<details>
-	<summary>0x14D68 16x12 16bit Engine Torque Reference</summary>

	Index: 619:
Reference and Basic Torque

            IP_TQI_REF[Nm] = f(N[rpm],MAF_CYL_STK[mg/stk])

</details>



<details>
-	<summary>0x12EC0 6x6 16bit Positive Torque Curve No load AT</summary>

	Index: 564  kf 283a: ip_maf_min_er_mt__n_32__tco
            IP_MAF_MIN_ER_MT[mg/stk] = f(N_32[rpm], TCO[°C])

</details>



<details>
-	<summary>0x12F08 6x6 16bit Positive Torque Curve No load MT</summary>

	Index: 564  kf 283a: ip_maf_min_er_mt__n_32__tco
            IP_MAF_MIN_ER_MT[mg/stk] = f(N_32[rpm], TCO[°C])

</details>



<details>
-	<summary>0x14BE0 8x8 16bit Coolant and Oil temperature correction of friction torque</summary>

	Index: 622  TQ: IP_TQFR_ADD
            IP_TQFR_ADD[Nm] = f(TCO[°C],TOIL[°C])

</details>



<details>
-	<summary>0x14AE0 16x8 16bit Base friction torque and pumping losses</summary>

	Index: 621
Torque Losses
            IP_TQFR[Nm] = f(N[rpm],MAF[mg/stk])

</details>



<details>
-	<summary>0x14CF8 12x4 16bit Minimum requested indicated torque in PU phase</summary>

	Index: 653  TQ: IP_TQI_MIN_REQ_PU
            IP_TQI_MIN_REQ_PU[Nm] = f(N[rpm],TCO[°C])

</details>



<details>
-	<summary>FIND AXIS0x14CE8 16bit Minimum requested indicated torque in PU phase | AMP Offset</summary>

	Index: 690  TQ: IP_TQI_MIN_PU_OFS_AMP
            IP_TQI_MIN_PU_OFS_AMP[Nm] = f(AMP[hPa])

</details>



<details>
-	<summary>0x14C88 12x4 16bit Minimum load limitation on indicated torque level in PU phase</summary>

	Index: 688
Minimum Indicated Torque at Trailing Throttle Conditions
            IP_TQI_MIN_PU[Nm] = f(N[rpm],TCO[°C])

</details>



<details>
-	<summary>0x14C70 16bit Minimum load limitation on indicated torque level in PUC phase</summary>

	Index: 689  TQ: IP_TQI_ADD_PUC
            IP_TQI_ADD_PUC[Nm] = f(N[rpm])

</details>



<details>
-	<summary>0x12F5C 12x16 MAF Setpoint (Torque Dependent)</summary>

	Index: 692
   692:     
Torque Coordination

            IP_MAF_SP[Nm] = f(N[rpm], TQI_SP_MAF[Nm])

</details>



---
[OpenGK.org](https://opengk.org)