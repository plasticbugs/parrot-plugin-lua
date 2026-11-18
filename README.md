# Lua

Write programs for the ColecoVision in Lua, on the console, and run them. Lua is a small programming language that's easy to learn. A script can draw, move sprites, play sound and read the controllers.

Scripts are `.lua` files in the `/LUA` folder of the card. Open one from the cart's menu, or start Lua by itself to see the list and make a new one. You need a USB keyboard to type. Without one you can still open scripts and run them.

## Controls

In the editor, on a USB keyboard or the controller's keypad:

- Ctrl+R, or keypad 4: save the script and run it
- Ctrl+S, or keypad 1: save
- Ctrl+O, or keypad 2: open another script from `/LUA`
- Ctrl+N, or keypad 3: start a new script
- Arrow keys, Home, End, Page Up and Page Down, or the stick: move around

While a script runs:

- Esc, or the keypad's \* held for two seconds: stop it and go back to the editor
- RESET: back to the cart's menu, as always

If a script has a mistake, Lua stops it, puts the cursor on the line and shows what went wrong.

## What you need

- A USB keyboard to write scripts. Plug it into a powered USB hub, and the hub into the cart. Game pads and a mouse go in the same hub.
- Scripts and their saves live in `/LUA` on the card. Lua makes the folder the first time it saves a new script.

The first lines of a script might be:

```lua
function draw()
  cls()
  print("HELLO", 100, 90)
end
```

Every function is described in the guide: <https://github.com/plasticbugs/parrot-plugin-lua/blob/main/docs/lua.md>

## Credits

- Lua 5.4.8, by Roberto Ierusalimschy, Luiz Henrique de Figueiredo and Waldemar Celes at PUC-Rio, MIT: <https://www.lua.org>
- Parrot Cart plugin template and SDK, by the Parrot Cart contributors, MIT: <https://github.com/plasticbugs/parrot-plugin-template>
- TinyUSB, by Ha Thach and contributors, MIT: <https://github.com/hathach/tinyusb>
- Raspberry Pi Pico SDK, BSD 3-Clause: <https://github.com/raspberrypi/pico-sdk>

Source: <https://github.com/plasticbugs/parrot-plugin-lua>

## Examples

`lua/examples` has four scripts. Copy them into `/LUA` on the card.

| Script | What it shows |
|---|---|
| `hello.lua` | text, a shape that moves, the stick, a sound |
| `sprites.lua` | twelve sprites bouncing around |
| `colours.lua` | a pattern in all 15 colours, drawn a little at a time |
| `snake.lua` | a small game with a score that's saved on the card |

## Build it yourself

You need the Raspberry Pi Pico SDK 2.1.1, an Arm GNU toolchain, CMake,
Ninja, Python 3, sjasmplus and picotool. Releases are built with the Arm
GNU Toolchain 9-2019-q4 (GCC 9.2.1) and picotool 2.3.1. With those you get
the same file, byte for byte.

```sh
cmake -B build -G Ninja -DPICO_SDK_PATH=$HOME/pico-sdk
ninja -C build
```

This makes `build/LUA.CVP`. Copy it into the `/PLUGINS` folder on the card.

On Ubuntu, `tools/ci/setup.sh` installs the same tools that GitHub uses to
build each release.

`CART-README.md` is the text the cart shows on the plugin's page. It is
the start of this README, with its own short license section.

## License

The plugin is under the MIT license (`LICENSE`). Lua keeps its own MIT
license, in `lua/vendor/lua-5.4.8/LICENSE`. `THIRD-PARTY.md` lists the
parts that came from elsewhere, and their licenses.
