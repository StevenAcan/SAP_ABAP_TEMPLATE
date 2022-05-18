```

FORM sub_data_retrieve  CHANGING p_gt_itab TYPE gty_t_sflight.

  SELECT *
  FROM sflight
  INTO CORRESPONDING FIELDS OF TABLE p_gt_itab
  WHERE carrid IN s_carrid
  AND   connid IN s_connid
  AND   fldate IN s_fldate.


ENDFORM.
*&---------------------------------------------------------------------*
*& Form sub_data_process
*&---------------------------------------------------------------------*
*& text
*&---------------------------------------------------------------------*
*&      --> GT_ITAB
*&---------------------------------------------------------------------*
FORM sub_data_process  USING VALUE(p_gt_itab) TYPE gty_t_sflight.

  "Place Holder


ENDFORM.
*&---------------------------------------------------------------------*
*& Form sub_report_display
*&---------------------------------------------------------------------*
*& text
*&---------------------------------------------------------------------*
*& -->  p1        text
*& <--  p2        text
*&---------------------------------------------------------------------*
FORM sub_report_display .

  DATA: ls_layout  TYPE slis_layout_alv,
        ls_variant TYPE disvariant,
        lt_fcat    TYPE slis_t_fieldcat_alv,
        lt_sort    TYPE slis_t_sortinfo_alv.

  PERFORM sub_fieldcat_set CHANGING lt_fcat.

  PERFORM sub_layout_set   CHANGING lt_sort
                                    ls_layout
                                    ls_variant.

  PERFORM sub_alv_display  USING lt_fcat
                                 lt_sort
                                 ls_layout
                                 ls_variant.

ENDFORM.
*&---------------------------------------------------------------------*
*& Form sub_fieldcat_set
*&---------------------------------------------------------------------*
*& text
*&---------------------------------------------------------------------*
*&      <-- LT_FCAT
*&---------------------------------------------------------------------*
FORM sub_fieldcat_set  CHANGING p_lt_fcat TYPE slis_t_fieldcat_alv.

  CONSTANTS: lc_table TYPE c LENGTH 7 VALUE 'SFLIGHT'.

  "Method 1: Call Funtion to generate Fieldcats Table as a whole
*  REUSE_ALV_FIELDCATALOG_MERGE
*  CALL FUNCTION 'REUSE_ALV_FIELDCATALOG_MERGE'
*    EXPORTING
*      i_program_name   = sy-repid
**     I_INTERNAL_TABNAME           =
*      i_structure_name = 'SFLIGHT'
**     I_CLIENT_NEVER_DISPLAY       = 'X'
**     I_INCLNAME       =
**     I_BYPASSING_BUFFER           =
**     I_BUFFER_ACTIVE  =
*    CHANGING
*      ct_fieldcat      = p_lt_fcat
**   EXCEPTIONS
**     INCONSISTENT_INTERFACE       = 1
**     PROGRAM_ERROR    = 2
**     OTHERS           = 3
*    .
*  IF sy-subrc = 0.
*    LOOP AT lt_fieldcat ASSIGNING FIELD-SYMBOL(<lfs_fieldcat>).
*
*      DATA(lv_index) = sy-tabix.
*
*      IF  <lfs_fieldcat>-fieldname = 'SEL'.
*
*        DELETE lt_fieldcat INDEX lv_index.
*
*        CONTINUE.
*
*      ENDIF.
*
*      IF <lfs_fieldcat>-fieldname = 'ZCOGS' OR
*         <lfs_fieldcat>-fieldname = 'LCOST' OR
*         <lfs_fieldcat>-fieldname = 'EXPEN' OR
*         <lfs_fieldcat>-fieldname = 'OEXPN' OR
*         <lfs_fieldcat>-fieldname = 'WIPLC' OR
*         <lfs_fieldcat>-fieldname = 'WIPEX' OR
*         <lfs_fieldcat>-fieldname = 'WIPOX' OR
*         <lfs_fieldcat>-fieldname = 'ACCRL' OR
*         <lfs_fieldcat>-fieldname = 'YCOGS'.
*
**        <lfs_fieldcat>-edit_mask = '==FLTQU'.
*        <lfs_fieldcat>-edit_mask = '==VAL02'.
*        <lfs_fieldcat>-decimals_out = '2'.
*        <lfs_fieldcat>-tabname = 'P_GT_ALVFINAL'.
*
*      ENDIF.
*
*
*    ENDLOOP.
*  ENDIF.

  "Method 2: Set up fieldcats manually

  PERFORM sub_fieldcat_add USING 'CARRID' "Field name
                                 "TEXT-f01 "Field Description
                                 'CARRID' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Table Name
                                 '' "Output length
                                 'X' "Key
                                 '' "Edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'CONNID' "Field name
                                 "TEXT-f02 "Field Description
                                 'CONNID' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 'X' "Key
                                 '' "edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'FLDATE' "Field name
                                 "TEXT-f03 "Field Description
                                 'FLDATE' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 'X' "Key
                                 '' "edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'PRICE' "Field name
                                 "TEXT-f04 "Field Description
                                 'PRICE' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 '' "Key
                                 'X' "edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'CURRENCY' "Field name
                                 "TEXT-f05 "Field Description
                                 'CURRENCY'"Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 '' "Key
                                 'X'"edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'PLANETYPE' "Field name
                                 "TEXT-f06 "Field Description
                                 'PLANETYPE' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 '' "Key
                                 '' "edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'SEATSMAX' "Field name
                                 "TEXT-f07 "Field Description
                                 'SEATSMAX' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 '' "Key
                                 '' "edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'SEATSOCC' "Field name
                                 "TEXT-f08 "Field Description
                                 'SEATSOCC' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 '' "Key
                                 '' "edit
                           CHANGING p_lt_fcat.

  PERFORM sub_fieldcat_add USING 'PAYMENTSUM' "Field name
                                 "TEXT-f09 "Field Description
                                 'PAYMENTSUM' "Referenced field
                                 'SFLIGHT' "Referenced field of Table
                                 lc_table "Referenced Table
                                 '' "Output Length
                                 '' "Key
                                 '' "edit
                           CHANGING p_lt_fcat.


ENDFORM.
*&---------------------------------------------------------------------*
*& Form sub_fieldcat_add
*&---------------------------------------------------------------------*
*& text
*&---------------------------------------------------------------------*
*&      --> P_
*&      --> lc_table
*&      --> P_
*&      --> P_
*&      --> P_
*&---------------------------------------------------------------------*
FORM sub_fieldcat_add  USING    VALUE(p_fieldname)
                                VALUE(p_ref_field)
                                VALUE(p_ref_table)
                                p_lc_table
                                VALUE(p_output_length)
                                VALUE(p_key)
                                VALUE(p_edit)
                       CHANGING p_lt_fcat TYPE slis_t_fieldcat_alv.

  DATA ls_fieldcat TYPE slis_fieldcat_alv.

  ls_fieldcat-fieldname     = p_fieldname.
  ls_fieldcat-tabname       = p_lc_table.
  ls_fieldcat-ref_fieldname = p_ref_field.
  ls_fieldcat-ref_tabname   = p_ref_table.
  ls_fieldcat-outputlen     = p_output_length.
  ls_fieldcat-key           = p_key.
  ls_fieldcat-edit          = p_edit.

*  ls_fieldcat-seltext_l = p_longtext.
*  ls_fieldcat-no_out = p_no_out.

  APPEND ls_fieldcat TO p_lt_fcat.

ENDFORM.
*&---------------------------------------------------------------------*
*& Form sub_layout_set
*&---------------------------------------------------------------------*
*& text
*&---------------------------------------------------------------------*
*&      <-- LS_LAYOUT
*&---------------------------------------------------------------------*
FORM sub_layout_set  CHANGING p_lt_sort    TYPE slis_t_sortinfo_alv
                              p_ls_layout  TYPE slis_layout_alv
                              p_ls_variant TYPE disvariant.

  DATA: ls_sort    TYPE LINE OF slis_t_sortinfo_alv.

  "layout
  p_ls_layout-zebra = gc_x.

  "Variant
  p_ls_variant-report = sy-repid.

  "Sort
  ls_sort-fieldname = 'CARRID'.
  APPEND ls_sort TO p_lt_sort.


ENDFORM.
*&---------------------------------------------------------------------*
*& Form sub_alv_display
*&---------------------------------------------------------------------*
*& text
*&---------------------------------------------------------------------*
*&      --> LT_FCAT
*&      --> LS_LAYOUT
*&---------------------------------------------------------------------*
FORM sub_alv_display  USING VALUE(p_lt_fcat)    TYPE slis_t_fieldcat_alv
                            VALUE(p_lt_sort)    TYPE slis_t_sortinfo_alv
                            VALUE(p_ls_layout)  TYPE slis_layout_alv
                            VALUE(p_ls_variant) TYPE disvariant.


  CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
    EXPORTING
      i_callback_program       = sy-repid "Mandatory if extra button needs to be added
      i_callback_pf_status_set = 'SUB_STATUS_1000'
      i_callback_user_command  = 'SUB_COMMAND_ALV'
*     i_callback_html_top_of_page = 'SUB_TOP_OF_PAGE_HTML'
      i_callback_top_of_page   = 'SUB_TOP_OF_PAGE'
      i_grid_title             = 'Flights Data ALV'
      is_layout                = p_ls_layout
      it_fieldcat              = p_lt_fcat
*     it_sort                  = p_lt_sort
      i_save                   = gc_a
      is_variant               = p_ls_variant
    TABLES
      t_outtab                 = gt_itab
    EXCEPTIONS
      program_error            = 1
      OTHERS                   = 2.
  IF sy-subrc <> 0.
    MESSAGE i398(00) WITH 'Error happens when calling ALV Display function.'.
    RETURN.
  ENDIF.



ENDFORM.

FORM sub_command_alv USING r_ucomm     TYPE sy-ucomm
                           rs_selfield TYPE slis_selfield.

  CASE r_ucomm.
    WHEN '&GEN_INFO'.
      MESSAGE i398(00) WITH 'This is a report above flights data'.
    WHEN '&IC1'."Double Click
      "Begin: Jump to MM03
*      READ TABLE gt_itab INTO gs_itab INDEX selfield-tabindex.
*      CASE selfield-fieldname.
*        WHEN 'MATNR'.
*          IF wa_output-matnr IS NOT INITIAL.
*            SET PARAMETER ID 'MAT' FIELD wa_output-matnr.
*            CALL TRANSACTION 'MM03' AND SKIP FIRST SCREEN.
*          ELSE.
*            MESSAGE s000(zm) WITH text-054.
*          ENDIF.
      "End: Jump to MM03
    WHEN OTHERS.
      MESSAGE i398(00) WITH 'Double Click'.
  ENDCASE.


ENDFORM.

FORM sub_status_1000 USING rt_extab TYPE slis_t_extab. "Parameters are mandantory

  SET PF-STATUS 'STATUS_1000'.

ENDFORM.



FORM sub_top_of_page_html USING p_cl_dd TYPE REF TO cl_dd_document.

  DATA: lv_m_p      TYPE i,
        lv_m_buffer TYPE string.

  lv_m_buffer = '<HTML><CENTER><H2>SAP Template: ALV FM</H2></CENTER><HTML>'.

  CALL METHOD p_cl_dd->html_insert
    EXPORTING
      contents = lv_m_buffer
    CHANGING
      position = lv_m_p.

  CONCATENATE '#####' sy-datum INTO lv_m_buffer.

  CALL METHOD p_cl_dd->html_insert
    EXPORTING
      contents = lv_m_buffer
    CHANGING
      position = lv_m_p.


ENDFORM.

FORM sub_top_of_page.

  DATA: ls_header TYPE slis_listheader,
        lt_header TYPE slis_t_listheader,
        lv_accno  TYPE n LENGTH 4.

  CLEAR: ls_header.
  REFRESH: lt_header.

*---------------------------------------
  ls_header-typ = 'H'.
  ls_header-info = 'SAP Template: ALV FM'.
  APPEND ls_header TO lt_header.

  CLEAR ls_header.
  ls_header-typ = 'S'.
  ls_header-info = 'TOP of Page'.
  APPEND ls_header TO lt_header.

  CLEAR ls_header.
  ls_header-typ = 'A'.
  ls_header-info = 'Action0001'.
  APPEND ls_header TO lt_header.

  CLEAR lv_accno.

*  CALL FUNCTION 'NUMBER_GET_NEXT'
*    EXPORTING
*      nr_range_nr             = '01'
*      object                  = 'Z_AB_ACCC1' "created by SNRO
**     QUANTITY                = '1'
**     SUBOBJECT               = ' '
**     TOYEAR                  = '0000'
**     IGNORE_BUFFER           = ' '
*    IMPORTING
*      number                  = lv_accno
**     QUANTITY                =
**     RETURNCODE              =
*    EXCEPTIONS
*      interval_not_found      = 1
*      number_range_not_intern = 2
*      object_not_found        = 3
*      quantity_is_0           = 4
*      quantity_is_not_1       = 5
*      interval_overflow       = 6
*      buffer_overflow         = 7
*      OTHERS                  = 8.
*  IF sy-subrc = 0.
*    CONCATENATE ls_header-info lv_accno INTO ls_header-info.
*  ENDIF.



  CALL FUNCTION 'REUSE_ALV_COMMENTARY_WRITE'
    EXPORTING
      it_list_commentary = lt_header
*     I_LOGO             =
*     I_END_OF_LIST_GRID =
      i_alv_form         = 'X'.


ENDFORM.


FORM sub_initialization .

  t1 = 'Input Flight info'.

  sscrfields-functxt_01 = '@2U@'.

  bt_allf = 'All Flight'.

ENDFORM.
```