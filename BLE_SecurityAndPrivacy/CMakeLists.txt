# Copyright (c) 2020 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_executable(BLE_SecurityAndPrivacy source/main.cpp)
target_link_libraries(BLE_SecurityAndPrivacy mbed-os mbed-ble-utils mbed-ble)
mbed_set_post_build(BLE_SecurityAndPrivacy)