# Especificações de Hardware - Waveshare RP2350-PiZero (Projeto: rp_os)

## Caminhos do Ambiente Local (Não baixar novamente)
- PICO_SDK_PATH: `/root/pico-sdk`
- PicoDVI RP2350: `/root/ia_project_rp2350/PicoDVI_rp2350`
- Pico-PIO-USB: `/root/ia_project_rp2350/Pico-PIO-USB`
- Saída de Firmware: Copiar sempre para `/sdcard/Download/rp_os.uf2`

## Mapa Completo de Pinagem da Placa
- **Placa Alvo CMake**: `PICO_BOARD=waveshare_rp2350_pizero`
- **Microcontrolador**: RP2350B (Dual-Core Cortex-M33, 520KB SRAM, 16MB Flash externa + suporte a PSRAM QSPI).
- **Saída Mini-HDMI / DVI (PIO0)**:
  - CLK+: GPIO 26 | CLK-: GPIO 27
  - D0+: GPIO 28 | D0-: GPIO 29 (Atenção: verificar conflito com PIO-USB caso use ambos; usar config padrão `waveshare_rp2350_pizero` do PicoDVI).
  - D1+: GPIO 22 | D1-: GPIO 23
  - D2+: GPIO 24 | D2-: GPIO 25
- **Conector USB-C Host (PIO-USB para Hub, Teclado, Mouse e Pendrive MSC)**:
  - D+: GPIO 28 (ou conforme definição nativa da placa no SDK) / D-: GPIO 29 (Nota: Se DVI usar 22-29, verificar o esquemático exato da placa para PIO-USB nos pinos dedicados).
- **Conector USB-C Device (Nativo)**: Alimentação, gravação UF2 e console serial CDC.
- **Slot Cartão MicroSD (SPI0)**:
  - MISO (SD_D0): GPIO 36
  - CS (SD_D3): GPIO 39
  - SCK (SD_CLK): GPIO 34
  - MOSI (SD_CMD): GPIO 35
- **Barramento GPIO 40-Pinos (Livre para Usuário / I2C / SPI / PWM)**:
  - GPIOs livres: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 20, 21.
  - Sensor interno de temperatura: Canal ADC 4.
