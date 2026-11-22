# Lua (LUA.CVP): the Lua plugin. It runs .lua scripts from the card, and has
# an editor to write them on the console (docs/lua.md).
#
#   cmake -B build -G Ninja -DPICO_SDK_PATH=$HOME/pico-sdk
#   ninja -C build                      -> build/LUA.CVP
#
# Copy LUA.CVP into the card's /PLUGINS folder.
cmake_minimum_required(VERSION 3.13)
include(${CMAKE_CURRENT_LIST_DIR}/cmake/parrotcart.cmake)
project(parrotcart_lua C CXX ASM)
parrotcart_init()

# The same source makes the same file, whenever it's built: the compiler's
# __DATE__ and __TIME__ (the build date in the binary info) come from
# SOURCE_DATE_EPOCH, fixed here at the release build's day, 2026-11-21.
set(BUILD_EPOCH 1795262400)
set(CMAKE_C_COMPILER_LAUNCHER ${CMAKE_COMMAND} -E env SOURCE_DATE_EPOCH=${BUILD_EPOCH})
set(CMAKE_CXX_COMPILER_LAUNCHER ${CMAKE_COMMAND} -E env SOURCE_DATE_EPOCH=${BUILD_EPOCH})

add_executable(lua)
cvcart_features(lua PSRAM CARD PADS KEYBOARD MOUSE MIDI_IN)
parrotcart_lua(lua)
cvcart_plugin(lua ID parrotcart.lua NAME "Lua" VERSION 0.1.4 BY "Parrot Cart"
              HOME /LUA OPENS .lua USES standalone ICON lua/icon.txt FILE_ICON lua/file_icon.txt
              README CART-README.md FILE LUA.CVP)
