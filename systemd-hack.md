To temporarily disable systemd power button handling so that you don't
get shutdown immediately due to this issue:

 * sudo systemd-inhibit --mode=block --what=handle-power-key