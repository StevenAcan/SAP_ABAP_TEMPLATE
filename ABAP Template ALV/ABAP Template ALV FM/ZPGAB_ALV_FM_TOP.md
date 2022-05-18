```
TABLES: sflight,
        sscrfields. "For activating function key at the tool bar

TYPES: gty_t_sflight TYPE STANDARD TABLE OF zstab_sflight.

TYPES: gty_s_sflight TYPE zstab_sflight.

DATA: gt_itab TYPE STANDARD TABLE OF zstab_sflight.

DATA: gs_flight TYPE sflight.

DATA: gt_flightdata TYPE STANDARD TABLE OF zstab_sflight.

FIELD-SYMBOLS: <gfs_flightdata> TYPE zstab_sflight.

"Begin: Variables for Screen 0100
DATA: gv_ok_code  TYPE ok,
      gv_filepath TYPE rlgrap-filename.
"End: Variables for Screen 0100

CONSTANTS: gc_x TYPE c LENGTH 1 VALUE 'X',
           gc_a TYPE c LENGTH 1 VALUE 'A'.
```