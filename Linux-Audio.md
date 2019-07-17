* lspci | grep -i audio
*       => controller.

*/proc/asound/cards
*        have card and codec bus.
*/proc/asound/card0
*/proc/asound/card1

*codec:
*        AC97: 目前幾乎沒有
*       HDA bus.
*        I2S: arm platform mostly.
*        sound wire: new

*/proc/asound/card0/codec#0 => usually analog codec
*/proc/asound/card0/codec#2 => usually hdmi codec

*alsa-info

* verb table ?
