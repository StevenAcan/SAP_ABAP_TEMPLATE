# ABAP Coding Convention

## Naming Convention
1. Package: Z + PK + \<Module or Function\> (<= 30 Char)  
```
ZPKAB, ZPKMM, ZPKREFRESHTABLES
```

2. Program: Z + PG + \<Module or Function\> + \<short description\> - <= 30  
```REPORT ZPGAB_PROGRAMMING_STANDARD.
REPORT ZPGMM_MATERIAL_CHECKING.
```

3. Database Table: Z + TB + <Module or Function> + <short description> - <= 16 C
```
TABLES: ZTBAB_SYSTEMLOG, ZTBMM_DEL_MATRL
```

4. selection screen: Select options - S_XXXX
```
SELECT-OPTIONS: s_carrid FOR sflight-carrid.
```

5. selection screen: Parameters - P_XXXX
```
PARAMETERS: p_file  TYPE rlgrap-filename.
```

6. Global structure types: GTY_S_XXX
```
TYPES: gty_s_sflight TYPE sflight.
```

7. Global internal table types: GTY_T_XXX
```
TYPES: gty_t_sflight TYPE STANDARD TABLE OF sflight.
```

8. Global single variable types: GTY_V_XXX
```
TYPES: gty_v_birthday TYPE dats.
```

9. Global structure: GS_XXX
```
DATA: gs_flight TYPE sflight.
```

10. Global internal table: GT_XXX
```
DATA: gt_flightdata TYPE STANDARD TABLE OF sflight.
```

11. Global field symbols: GFS_XXX
```
FIELD-SYMBOLS: <gfs_flightdata> TYPE sflight.
```

12. Global class reference: GO_XXX (point to a Object)
```
DATA: go_alv_grid TYPE REF TO cl_gui_alv_grid.
```

13. Global constants: GC_XXX
```
CONSTANTS: gc_x TYPE c LENGTH 1 VALUE 'X'.
```

14. Global class: GCL_XXX_XXX
```
CLASS gcl_event_receiver DEFINITION.
```

15. Function Group: Z + FG + <Module or Function> + <short description>
```
ZFGAB_TABLEMAINTAIN, ZFGMM_MATERIALPROCESS
```

16. Function Module: Z + '_' + FM + <Module or Function> + <short description>
```
Z_FM_MM_GETDELETEDSTOCK, Z_FM_AB_ROUNDING
```

17. Message Class: Z + MG + <Module or Function> + <short description>
```
REPORT zpgab_alv_oo MESSAGE-ID ZMGAB_ALVOO.
```

18. SAP Structure: Z + ST + <Module or Function> + <short description>
```
DATA: gs_flight TYPE ZSTAB_FLIGHTDATA.
```

19. SAP Type of table: Z + TT +<Module or Function> + <short description>
```
DATA: gt_flight TYPE ZTTAB_FLIGHTDATA.
```

20. Domain: Z + DM + <Module or Function> + <short description>
```
ZDMAB_FILELENGTH, ZDMMM_MTDESCRP
```

21. Element: Z + EL + <Module or Function> + <short description>
```
DATA: gv_birthday TYPE ZELAB_BTHDAY.
```

22. Type Group: Z + TG +  'XX' -> 5 C
```
TYPE-POOLS: ZTGA1.
```

23. Customer Function Exit(CMOD): Z + EH + <Module or Function> + 'XXX'
```
ZEHMM001
```

24. BADI: Z + EH + BD + <Module or Function> + <short description> - <= 20C
```
ZEHBD_MM_MIGOCHECK01
```

25. IDOC type: Z + IDOC +  <Module or Function> + <short description> - <=30 C
```
ZIDOC_MM_SENDTOOA, ZIDOCMM_SENDTOOA
```

26. Segment type: Z + SEG + <Module or Function> + <short description> - <=30 C
```
ZSEG_MM_MTMAS01, ZSEGMM_MTMAS01
```

27. Smartforms: Z + SF + <Module or Function> + <short description> - <=30 C
```
ZSFMM_POINFO, ZSF_MM_POINFO
```

28. Global range table type: GTY_RT_XXX
```
TYPES: gty_rt_flightdate TYPE RANGE OF sflight-fldate.
```

29. Global range table: GRT_XXX
```
DATA: grt_flightdate TYPE gty_rt_flightdate.
```
## Module Mapping

<table>
<caption>Module Mapping</caption>
<tr>
	<th>Short</th>
	<th>Module</th>
</tr>

<tr>
	<td>AB</td>
	<td>ABAP or Basis</td>
</tr>

<tr>
	<td>SD</td>
	<td>Sales and Distribution</td>
</tr>

<tr>
	<td>MM</td>
	<td>Material management</td>
</tr>

<tr>
	<td>FI</td>
	<td>Finance and Control</td>
</tr>

<tr>
	<td>PP</td>
	<td>Production Planning</td>
</tr>

</table>

## Indicator Mapping

<table>
<caption>Indicator Mapping</caption>
<tr>
	<th>PK</th>
	<th>Package</th>
</tr>

<tr>
	<td>PG</td>
	<td>Program</td>
</tr>

<tr>
	<td>FG</td>
	<td>Function Group</td>
</tr>

<tr>
	<td>FM</td>
	<td>Function Module</td>
</tr>

<tr>
	<td>MG</td>
	<td>Message Class</td>
</tr>

<tr>
	<td>TB</td>
	<td>Database Table</td>
</tr>

<tr>
	<td>ST</td>
	<td>Structure</td>
</tr>

<tr>
	<td>DM</td>
	<td>Domain</td>
</tr>

<tr>
	<td>EL</td>
	<td>Element</td>
</tr>

<tr>
	<td>TG</td>
	<td>Type Group</td>
</tr>

<tr>
	<td>EH</td>
	<td>Enhancement</td>
</tr>

<tr>
	<td>SF</td>
	<td>Smartforms</td>
</tr>

<tr>
	<td>BD</td>
	<td>BADI</td>
</tr>

<tr>
	<td>CDS</td>
	<td>Core Data Services</td>
</tr>

<tr>
	<td>GTY_S</td>
	<td>Global type of a structure</td>
</tr>

<tr>
	<td>GTY_T</td>
	<td>Global type of a internal table</td>
</tr>

<tr>
	<td>GS_</td>
	<td>Global structure</td>
</tr>

<tr>
	<td>GT_</td>
	<td>Global internal table</td>
</tr>

<tr>
	<td>GO</td>
	<td>Global object reference</td>
</tr>

<tr>
	<td>GC_</td>
	<td>Global constant</td>
</tr>

<tr>
	<td>GFS_</td>
	<td>Global field symbol</td>
</tr>

<tr>
	<td>GCL_</td>
	<td>Global class</td>
</tr>

</table>

## Program comments

```
*&---------------------------------------------------------------------*
*& Program Name (Purchase Order Infor Check)
*&---------------------------------------------------------------------*
*& Program ID       : ZSDVNN0001                                       *
*& RICEF ID         : EUE0024                                          *
*& Module             : SD                                             *
*& Author              : Liu Can(Steven)                               *
*& Create Date      : 02-Sep-2020                                      *
*& Request No       : ED1K927957                                       *
*& Logical DB       : N/A                                              *
*& Program Type     : Screen Enhancement(executable)                   *
*& SAP Release      : ERP 6.0(S41909)                                  *
*& Description      :
*&---------------------------------------------------------------------*
*&Change Log                                                               
*& Version  Date        TR		   Author                 
*& 000      02-Sep-2020 ED1K927957 Liu Can(Steven)   
*& Description                                                         
*& Initinal version,CR#50253917 CO#50254067 
*& Add an new field in screen of VA01/VA02/VA03, Tab 'Additional Data B'
*&---------------------------------------------------------------------*
*& 001      01-Sep-2022  XXX       XXX                                                    
*& Description                                                         
*& XXX                                                                    
*&---------------------------------------------------------------------*
```

