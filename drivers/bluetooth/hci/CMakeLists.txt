# SPDX-License-Identifier: Apache-2.0

# Remove after 3.7.0 is released
if(CONFIG_BT_RPMSG)
	message(FATAL_ERROR  "CONFIG_BT_RPMSG has been renamed to CONFIG_BT_HCI_IPC")
endif()

# Remove after 3.7.0 is released
if(CONFIG_BT_HCI_IPC)
  dt_chosen(chosen_hci_rpmsg PROPERTY "zephyr,bt-hci-rpmsg-ipc")
  if(DEFINED chosen_hci_rpmsg)
	message(FATAL_ERROR  "zephyr,bt-hci-rpmsg-ipc has been renamed to zephyr,bt-hci-ipc")
  endif()
endif()

zephyr_library_sources_ifdef(CONFIG_BT_B91         hci_b91.c)
zephyr_library_sources_ifdef(CONFIG_BT_CYW43XXX    cyw43xxx.c)
zephyr_library_sources_ifdef(CONFIG_BT_ESP32       hci_esp32.c)
zephyr_library_sources_ifdef(CONFIG_BT_H4          h4.c)
zephyr_library_sources_ifdef(CONFIG_BT_H5          h5.c)
zephyr_library_sources_ifdef(CONFIG_BT_HCI_IPC     ipc.c)
zephyr_library_sources_ifdef(CONFIG_BT_SPI         spi.c)
zephyr_library_sources_ifdef(CONFIG_BT_STM32_IPM   ipm_stm32wb.c)
zephyr_library_sources_ifdef(CONFIG_BT_USERCHAN    userchan.c)
zephyr_library_sources_ifdef(CONFIG_BT_SILABS_HCI  slz_hci.c)
zephyr_library_sources_ifdef(CONFIG_BT_PSOC6_BLESS hci_psoc6_bless.c)
zephyr_library_sources_ifdef(CONFIG_SOC_NRF5340_CPUAPP nrf53_support.c)
