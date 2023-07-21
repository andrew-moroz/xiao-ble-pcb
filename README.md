# xiao-ble-pcb

A simple example Eagle project for the <a href="https://github.com/meshtastic/firmware/pull/2633" target="_blank">Xiao BLE + E22-900M30S Meshtastic variant</a>.

#### Note: This board is currently untested, so it's "build at your own risk" for the time being. I should be able to confirm it works as intended by the end of this week (7/28/23).

This is set up to use the E22 in 'automatic Tx/Rx switching' mode, with TXEN and DIO2 connected to each other rather than to the Xiao. I created it with two additional breakout boards in mind – the <a href="https://www.adafruit.com/product/1863" target="_blank">Adafruit Switched JST Breakout</a> and the <a href="https://www.adafruit.com/product/4654" target="_blank">Adafruit MiniBoost</a>. The switched JST goes in the GND, SW, +, and GND pins, and the MiniBoost goes in the EN, 5V, GND, and VIN pins. You can of course use any other 5V power source, and/or forego the JST board and solder the battery directly to the board, but the breakouts are inexpensive ($6.50 USD before tax and shipping) and ideally suited to the task. 

To get the full 30 dBm transmit power out of the E22, a buffering capacitor (ideally at least 100 µF) should be placed between the 5V rail and GND. If using the MiniBoost, you can place a through-hole capacitor across its 5V and GND pins and then use the cap's leads in place of header pins for those two pads. Alternately, you could solder a capacitor across pins 10 (VCC) and 11 (GND) on the E22.

The board breaks out the Xiao's unused GPIO pins (D4, D5, D6, NFC1, NFC2) and also preserves access to its SWCLK, SWDIO, RST, and GND pins on the bottom.

# Bill of materials

<strong>Note: </strong>You can use a Xiao BLE Sense instead if you want. I went with the non-sense version since it's $5 cheaper and I didn't need the extra bells and whistles.

| Part | Source | Cost&nbsp;(USD) | Note |
| :------------ | :---------------------------- | :-----------------| :-----------------|
| Xiao BLE | <a href="https://www.digikey.com/en/products/detail/seeed-technology-co-ltd/102010448/16652893" target="_blank">DigiKey</a> | $10.38 ||
| Ebyte E22-900M30S | <a href="https://www.aliexpress.us/item/3256801621928909.html" target="_blank">AliExpress</a> | $9.42 | Also available on <a href="https://www.amazon.com/EBYTE-E22-900M30S-Wireless-Transmitter-Receiver/dp/B07RLQ9LTF">Amazon</a> for a couple bucks more |
| Adafruit Switched JST Breakout | <a href="https://www.digikey.com/en/products/detail/adafruit-industries-llc/1863/6565368" target="_blank">DigiKey</a> | $2.50 ||
| Adafruit MiniBoost (5V @ 1A) | <a href="https://www.digikey.com/en/products/detail/adafruit-industries-llc/4654/12697636" target="_blank">DigiKey</a> | $3.95 ||
| 100 uF capacitor | <a href="https://www.digikey.com/en/products/detail/würth-elektronik/860040272001/5727432" target="_blank">DigiKey</a> | $0.13 | Just one example with decent specs, lots of other (and smaller) options available |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;||||
| <strong>Total</strong> || $26.38 | Plus the cost of the PCB – roughly $25 (HASL w/ lead surface finish) or $55 (ENIG surface finish) for 10 boards at <a href="https://www.pcbway.com" target="_blank">pcbway.com</a>; can probably be had for less elsewhere |


# TODO

* Route the board manually
* Create a "version 2" for assembly with the boost converter, JST + switch, and maybe also a solar charge controller integrated into the design