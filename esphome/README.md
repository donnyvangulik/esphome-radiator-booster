# ESPHome Device Notes

## Pinout (Feather ESP32-S3)

- **Fan PWM (LEDC):** GPIO39, 25 kHz, `zero_means_zero: true`
- **Tach (RPM):** GPIO38, `pulse_meter` (2 pulses/rev, `multiply: 0.5`)
- **USB-PD CFG pins:** GPIO40/41/42
- **NTC ADCs:** GPIO4 (inlet), GPIO5 (outlet), GPIO6 (internal)
- **I2C:** bus A (SDA=9, SCL=10), bus B (SDA=18, SCL=21)
- **Status LED:** GPIO1

## Entities

- **Numbers:** `Ts1`, `Ts2`, `Ts1_cool`, `Ts2_cool`, `Te_heat_on`, `Te_heat_off`, `Te_cool_on`, `Manual PWM % (override)`
- **Sensors:** `Fan RPM`, `Fan PWM %`, `Internal temperature`, `NTC1 temperature (inlet)`, `NTC2 temperature (outlet)`, `USB Voltage`
- **Button:** `Return to Auto`
- **Switches:** `Heating logic enabled`, `Cooling logic enabled`, `Invert inlet/outlet`
