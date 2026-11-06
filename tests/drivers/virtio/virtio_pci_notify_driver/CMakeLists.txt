# SPDX-FileCopyrightText: Copyright The Zephyr Project Contributors
# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.28.0)
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(virtio_pci_notify_driver)

target_sources(app PRIVATE src/main.c)
target_include_directories(app PRIVATE ${ZEPHYR_BASE}/drivers/virtio)

if(NOT DEFINED HAVE_NOTIFY_LEN)
  set(HAVE_NOTIFY_LEN 1)
endif()

target_compile_definitions(app PRIVATE HAVE_NOTIFY_LEN=${HAVE_NOTIFY_LEN})
