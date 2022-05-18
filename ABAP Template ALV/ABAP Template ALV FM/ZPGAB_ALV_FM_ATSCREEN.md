```
AT SELECTION-SCREEN.

  CASE sscrfields-ucomm.
    WHEN'FC01'. "Reserved function code

*      CALL SCREEN '0100' STARTING AT 3 3 ENDING AT 80 10.

    WHEN OTHERS.

  ENDCASE.

  CASE sy-ucomm.

    WHEN 'ALLFLIGHT'.

*      PERFORM sub_factory_alv_demo.

    WHEN OTHERS.

  ENDCASE.

*AT SELECTION-SCREEN ON VALUE-REQUEST FOR p_file.
*  PERFORM sub_selectfile.
*
*AT SELECTION-SCREEN ON VALUE-REQUEST FOR p_filep.
*  PERFORM sub_selectfilepath.
```