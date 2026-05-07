# How to add custom audio and images to effects

> **Want to add your own music or images to drug effects? Just drop files in the right folder**

The script automatically scans the asset folders and shows all valid files in the effect editor dropdown. No code changes needed.

## Adding custom audio files

1. Open your server files and navigate to: `drugs_creator/html/assets/audio/`
2. Place your audio files in this folder
3. Restart the script or the server

That's it! The new audio files will now appear in the **Music** effect dropdown when editing drug effects

### Supported audio formats

`mp3`, `ogg`, `wav`, `flac`, `aac`, `m4a`

## Adding custom images

1. Open your server files and navigate to: `drugs_creator/html/assets/img/`
2. Place your image files in this folder
3. Restart the script or the server

The new images will appear in the **Trip Screen Image** and **3D World Image** effect dropdowns

### Supported image formats

`jpg`, `jpeg`, `png`, `gif`, `webp`

## Important notes

- File names are used directly as labels in the dropdown, so use descriptive names (e.g. `space_trip.jpg` instead of `img1.jpg`)
- If you add files while the server is running, restart the script for changes to appear
- Keep file sizes reasonable: large images or audio files can affect loading times for players
