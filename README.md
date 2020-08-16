# system-summary

Get general system information, useful to display in a status bar for instance

## Usage

system-summary [options]

## Options

```
-c,--color <auto|never|always|pango>   use pango for sway-bar (default: auto)
-h,--help                              print this message
-i,--icons                             use unicode symbols instead of plain text
-s,--separator <separator>             what to print between each value (default: newline)
```

## Currently supported

- backlight level
- battery level & status
- bluetooth connections
- fan speed
- home disk usage
- network connections
- song playing
- time and date
- top cpu task
- connected usb devices
- volume level & status
- wifi link quality

# Sample Output

## Terminal

```
sh$ system-summary
WH-1000XM3
vlc: 5%
song: KOAN Sound - Elevator Machine Room
Maison
wifi: 75%
fans: 2881
backlight: 70%
vol: 100%
bat: 100%
home: 36G/157G
15:24:57 16/08/2020
```

## Sway bar

### Config

```
bar {
    position bottom
    # escape colors codes aren't supported, the only way to print colors with
    # "status_command" is to use pango markup
    pango_markup enabled

    status_command while system-summary --icons --color pango --separator \ \|\ ; do sleep 5; done

    colors {
        statusline #ffffff
        background #323232
        inactive_workspace #32323200 #32323200 #5c5c5c
    }
}
```

### Ouput

![sway bar screenshot](./sway-bar-screenshot.png)
