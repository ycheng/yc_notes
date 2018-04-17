Suspend:
 * https://www.kernel.org/doc/Documentation/power/states.txt
 * go to suspend: # echo mem > /sys/power/state
 * config s2idle or s3:
 ** "# echo s2idle > /sys/power/mem_sleep # suspend to idle"
 ** "# echo deep > /sys/power/mem_sleep # s3"

Cgroup:
