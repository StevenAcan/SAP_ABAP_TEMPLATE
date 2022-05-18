```
*&---------------------------------------------------------------------*
*& Program: Template ALV FM
*&---------------------------------------------------------------------*
*&---------------------------------------------------------------------*
*& Program ID       : ZPGAB_ALV_FM                                     *
*& RICEF ID         : R00001                                           *
*& Program Name     : ALV FM Template                                  *
*& Module Name      : AB(ABAP) Cross-Module                            *
*& Sub-Module       :                                                  *
*& Author           : Liu Can(Steven)                                  *
*& Create Date      : 2021-10-25                                       *
*& Request No       :                                                  *
*& Program Type     : Executable program                               *
*& SAP Release      : S4/Developer Edition                             *
*& Description      : This program works as a template of ALV FM Report*
*&---------------------------------------------------------------------*
*&---------------------------------------------------------------------*
*& REVISION LOG                                                        *
*& RN    Date         TR          Author                               *
*& 0000  2021-10-25   S4DK901598  Liu Can(Steven)                      *
*& Description                                                         *
*& XXX
*&---------------------------------------------------------------------*
*& 0001  YYYY-MM-DD   XXX         XXX                                  *
*& Description                                                         *
*&                                                                     *
*&---------------------------------------------------------------------*

REPORT zpgab_alv_fm.

include zpgab_alv_fm_top.

include zpgab_alv_fm_screen.

include zpgab_alv_fm_atscreen.

include zpgab_alv_fm_subroutine.

INITIALIZATION.

  PERFORM sub_initialization.

START-OF-SELECTION.

  PERFORM sub_data_retrieve CHANGING gt_itab.

  PERFORM sub_data_process USING gt_itab.

  PERFORM sub_report_display.
```