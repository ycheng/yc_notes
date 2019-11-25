CPU PM:
* package-based P-states
* package-based C-states (PC-states)
* core-based C-states  (CC-states)
* There are no per-core based P-states.

ACPI在運行中有以下幾種模式：
* S0 正常。
* S1 CPU停止工作。喚醒時間：0秒。
* S2 CPU關閉。喚醒時間：0.1秒。
* S3 除了記憶體外的部件都停止工作。喚醒時間：0.5秒。
* S4 記憶體內容寫入硬碟，所有部件停止工作。喚醒時間：30秒。（休眠狀態）
* S5 關閉。

S0idle
* WOV: wake on voice (can be supported)
* Run-time D3 (RTD3) enable device is needed. The clock can be turned off.

