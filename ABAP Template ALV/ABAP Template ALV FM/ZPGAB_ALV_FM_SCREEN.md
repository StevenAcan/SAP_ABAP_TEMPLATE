```
SELECTION-SCREEN BEGIN OF BLOCK b1 WITH FRAME TITLE t1.

SELECT-OPTIONS: s_carrid FOR sflight-carrid,
                s_connid FOR sflight-connid,
                s_fldate FOR sflight-fldate.

SELECTION-SCREEN: SKIP 2.

"Button on selection screen; text set up in 'INITIALIZATION'
SELECTION-SCREEN: PUSHBUTTON 2(12) bt_allf USER-COMMAND allflight.

SELECTION-SCREEN: SKIP 2.


SELECTION-SCREEN END OF BLOCK b1.

"Activate a new function button at the tool bar
SELECTION-SCREEN: FUNCTION KEY 1.
```