# What in this repository came from elsewhere

The plugin's own code, in `lua/`, is under the MIT license (`LICENSE`).
The copy of the cart's SDK in `sdk/` is under the MIT license
(`sdk/LICENSE`). These parts came from elsewhere and keep their own terms.

| Where | What | License |
|---|---|---|
| `lua/vendor/lua-5.4.8/` | [Lua](https://www.lua.org) 5.4.8 (Roberto Ierusalimschy, Luiz Henrique de Figueiredo and Waldemar Celes, PUC-Rio), with two lines of `luaconf.h` changed, listed in its `VENDORED.md` | MIT (`lua/vendor/lua-5.4.8/LICENSE`) |
| `cmake/parrotcart.cmake`, `lib/wired.h`, `tools/lua-embed.py` | from the [Parrot Cart plugin template](https://github.com/plasticbugs/parrot-plugin-template) | MIT |
| `sdk/firmware/revc/sdk/tinyusb/` | [TinyUSB](https://github.com/hathach/tinyusb) (Ha Thach and contributors), with the cart's fixes, listed in its `VENDORED.md` | MIT (`sdk/firmware/revc/sdk/tinyusb/LICENSE`) |
| `cmake/pico_sdk_import.cmake` | from the [Raspberry Pi Pico SDK](https://github.com/raspberrypi/pico-sdk) | BSD 3-Clause |

The built plugin also contains Lua (MIT), the Raspberry Pi Pico SDK's
runtime (BSD 3-Clause) and TinyUSB (MIT).

The editor's 6x8 font was drawn for the cart's SDK
(`sdk/firmware/revc/sdk/cvfont.c`).
The 8x8 screen font's letter shapes come from the 1982 arcade game Mr. Do!
