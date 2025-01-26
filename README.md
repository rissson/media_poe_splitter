# Media PoE splitter

This board splits a PoE+ input into a 24V 85W output and a USB interface for data. It is meant to be used as part of my
home media system for driving in-wall speakers.

## Specs

- Uses a [Silvertel Ag5800](https://silvertel.com/ag5800/) for PoE control and DC-DC conversion
  - From PoE+ to PoE++ (Type 2 to Type 4, 802.3at and 802.3bt)
  - Outputs up to 85W of power over 24V
- Converts the data from 4 pairs Ethernet to USB 2.0 with a [Microchip 7850](https://www.microchip.com/en-us/product/lan7850)
  - 10/100/1000 Ethernet (but limited by USB 2.0 speed at around 400 Mbps)

## Usage

My usage of this board is with a
[HiFiBerry Amp2](https://www.hifiberry.com/shop/boards/dealing-with-blocked-p5-holes-7/) and a
[Raspberry Pi Zero 2 W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/).

Power is provided to the Amp2, which in turns powers the RPi and drives 2 speakers.

Data is provided to the RPi via Micro USB 2.0. The data output of the `media_poe_splitter` is done over a flex ribbon
cable (pitch 0.5mm, 6pos) to fit dimension constraints. The associated `usb_breakout` board transforms that into a Micro
USB connector that can be plugged in the RPi data port.

## Considerations

Thermal management should be done accordingly to the recommendations provided by the Ag5800 documentation.

The board has 4 heat pads which should be coated using thermally conductive oxime board mounting the Ag5800.

## Datasheets and reference boards

- Ag5800
  - https://silvertel.com/images/datasheets/Ag5800-datasheet-%20IEEE802_3bt-Power-over-Ethernet-4-pair-PD.pdf
  - The EVALAg5800 schematic and BOMs are not publicly published by Silvertel, but they sent it over by email when asked
    for it. As such, I won't reproduce them here, but here are some public references for similar boards:
    - https://silvertel.com/images/Eval-Board-User-Guides/EVALAg5810-User-Manual.pdf
    - https://silvertel.com/images/Eval-Board-User-Guides/EvalAg59600-Board-User-Manual.pdf
- LAN7850
  - https://ww1.microchip.com/downloads/aemDocuments/documents/UNG/ProductDocuments/DataSheets/LAN7850-Data-Sheet-DS00001993F.pdf
  - https://www.farnell.com/datasheets/3109926.pdf
  - https://ww1.microchip.com/downloads/aemDocuments/documents/UNG/ProductDocuments/BoardDesignFiles/UNG8002_EVB_LAN7850_A1.pdf
- Wurth Elektronik PoE Ethernet to USB board
  - https://www.we-online.com/components/media/o758720v410%20RD022_EN.pdf
