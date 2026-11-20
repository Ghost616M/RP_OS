cmake_minimum_required(VERSION 3.13)

if(NOT DEFINED PICO_FLASH_SIZE_BYTES)
    set(PICO_FLASH_SIZE_BYTES 16777216)
endif()
set(PICO_FLASH_SIZE_BYTES "${PICO_FLASH_SIZE_BYTES}" CACHE STRING "Flash size in bytes" FORCE)

if(NOT DEFINED PICO_BOARD)
    set(PICO_BOARD waveshare_rp2350_pizero)
endif()
if(NOT DEFINED PICO_PLATFORM)
    set(PICO_PLATFORM rp2350-arm-s)
endif()
set(PICO_BOARD "${PICO_BOARD}" CACHE STRING "PICO target board" FORCE)
set(PICO_PLATFORM "${PICO_PLATFORM}" CACHE STRING "PICO target platform" FORCE)

set(PICO_PROJECT_ROOT ${CMAKE_CURRENT_LIST_DIR})

list(APPEND PICO_BOARD_HEADER_DIRS ${PICO_PROJECT_ROOT}/boards)
set(PICO_BOARD_HEADER_DIRS "${PICO_BOARD_HEADER_DIRS}" CACHE STRING "PICO board header directories" FORCE)

include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

set(PICO_PIO_USB_PATH /root/ia_project_rp2350/Pico-PIO-USB)
set(PICODVI_ROOT /root/ia_project_rp2350/PicoDVI_rp2350/software)
set(FATFS_VENDOR_DIR ${PICO_SDK_PATH}/lib/tinyusb/lib/fatfs/source)
set(FATFS_DIR ${CMAKE_CURRENT_BINARY_DIR}/fatfs)
file(COPY ${FATFS_VENDOR_DIR}/ DESTINATION ${FATFS_DIR})
configure_file(${CMAKE_CURRENT_LIST_DIR}/src/ffconf.h ${FATFS_DIR}/ffconf.h COPYONLY)

project(rp_os C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_subdirectory(${PICODVI_ROOT}/libdvi libdvi)

set(RP_OS_SOURCES
    src/main.c
    src/board.c
    src/display.c
    src/gfx.c
    src/input.c
    src/hw.c
    src/sd_spi.c
    src/flash_disk.c
    src/diskio.c
    src/storage.c
    src/usb_host.c
    src/usb_descriptors.c
    src/usb_net.c
    src/net_stack.c
    src/ath9k_wifi.c
    src/shell.c
    src/theme.c
    src/gui.c
    src/gui_wm.c
    src/apps/app_terminal.c
    src/apps/app_files.c
    src/apps/app_gpio.c
    src/apps/app_editor.c
    src/apps/app_sysmon.c
    src/apps/app_network.c
    src/apps/app_settings.c
    ${FATFS_DIR}/ff.c
    ${FATFS_DIR}/ffunicode.c
    ${FATFS_DIR}/ffsystem.c
)

add_executable(rp_os ${RP_OS_SOURCES})

target_include_directories(rp_os PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/src
    ${PICO_SDK_PATH}/lib/tinyusb/src
    ${PICODVI_ROOT}/include
    ${PICODVI_ROOT}/assets
    ${FATFS_DIR}
)

target_compile_definitions(rp_os PRIVATE
    PICO_PIO_USE_GPIO_BASE=1
    PICO_CORE1_STACK_SIZE=0x800
    PIO_USB_DP_PIN_DEFAULT=28
    PIO_USB_USE_TINYUSB=1
    CFG_TUH_RPI_PIO_USB=1
    DVI_DEFAULT_SERIAL_CONFIG=waveshare_rp2350_pizero
    DVI_DEFAULT_PIO_INST=pio0
    DVI_VERTICAL_REPEAT=2
)

target_compile_options(rp_os PRIVATE
    -Wall
    -Wextra
    -Wno-unused-parameter
)

target_link_libraries(rp_os PRIVATE
    pico_stdlib
    pico_multicore
    pico_util
    pico_bootrom
    pico_unique_id
    pico_malloc
    pico_flash
    hardware_clocks
    hardware_vreg
    hardware_adc
    hardware_pwm
    hardware_watchdog
    hardware_dma
    hardware_pio
    hardware_irq
    hardware_sync
    hardware_spi
    hardware_flash
    hardware_i2c
    tinyusb_device
    tinyusb_host
    tinyusb_pico_pio_usb
    pico_lwip
    pico_lwip_arch
    libdvi
)

pico_enable_stdio_uart(rp_os 0)
pico_enable_stdio_usb(rp_os 0)
pico_add_extra_outputs(rp_os)

target_link_options(rp_os PRIVATE -Xlinker --print-memory-usage)
