# Change doors icon

## How to change the color

To change the icon colors, you can edit `doors_creator/integrations/cl_integrations.lua` file and edit the lines about color

```lua
-- r = red, g = green, b = blue, a = opacity
-- All values are from 0 to 255
-- If all colors are to 255, the image will have the default color
color = {
    r = 50,
    g = 255,
    b = 50,
    a = 255,
}
```

## How to change the icon/image

To change the icon/image, you can simply replace the images in `doors_creator/icons/` folder, be sure to use the same exact names

## How to change the size

The scale can be edited directly in the in-game menu, but you can also adjust the x and y values in case you need it in `doors_creator/integrations/cl_integrations.lua` file

```lua
-- image width
x = 0.03,

-- image height
y = 0.04,
```
