Errata and Known Issues
========================

Errata
------

  * The DVIULC6-4SC6 Vin has been connected to the TPS73101 LDO output.
    It should have been connected to the 5V rail.
  * The power and reset buttons are not labelled as such on the PCB silkscreen.
    This will be fixed in the next PCB revision.

Known Issues
------------

  * The RTC, the SPI Flash and the eMMC exist on the board but have not been
    brought up. They will be enabled in future SW upgrades.
  * The user LEDs are too bright, and the power LED is dimmer than usual. The
    serial resistors will need updating in the next revision.
  * Some of the expansion pins have not been configured from the device tree
    and cannot be used as of now. Currently only the SPI, UART and I2C
    interfaces have been brought up on the expansion header. PWM and eQEP are
    yet to be brought up. The expansion header also needs to be documented
    so that applications can make use of these pins, through a library or
    otherwise.
  * The Gigabit Ethernet speeds are limited, the maximum achievable streaming
    sampling rate through the link is 10MSps @16 channels or 20MSps @8 channels.
  * Due to the “hold” feature in the 74LVCH16T245 logic buffer used to buffer
    the logic signals before going to the SoC, pins once high will stay high
    until pulled low. This does not affect the operation of the logic analyzer,
    but can be noticed as anomalous behavior as one would expect the pin not
    connected to anything to be “low”.
  * The board supports both TTL-level and 1.8V logic level thresholds,
    but some work is required to integrate this support into PulseView and the
    web frontend.
