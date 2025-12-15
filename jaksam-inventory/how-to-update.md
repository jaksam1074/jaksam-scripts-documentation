# How to Update Jaksam Inventory

This guide shows you how to update without losing your custom items, settings, and configurations

{% hint style="danger" %}
**Always backup before updating!** You'll lose all your customizations if you skip this step
{% endhint %}

## What to Backup

**Always backup these folders:**
- `_data/` - Your items and settings
- `_hooks/` - Crafting recipes and custom logic
- `_images/` - Items images
- `_modules` - Integration with external scripts
- `integrations/` - Some settings
- `current_config.json` - Settings file

**Only if you modified them:**
- `_images/` - Custom item images
- `dist/assets/variables.css` - Custom theme colors
- `_locales/` - Translations
- `dist/menu_translations/` - Menu translations

## Update Steps

1. **Stop your server**

2. **Backup your files**
   - Copy the folders to backup from the server to a safe location (like your Desktop)

3. **Remove the old inventory from server**
   - Remove the entire `jaksam_inventory` folder from your server

4. **Install the new version**
   - Download the latest version
   - Extract and copy the new `jaksam_inventory` folder to your server

5. **Restore your backups**
   - Copy your backup folders back into the new `jaksam_inventory` folder:
     - Replace `_data/` with your backup `_data/`
     - Replace `_hooks/` with your backup `_hooks/`
     - Replace `integrations/` with your backup `integrations/`
     - Replace `_images/` with your backup `_images/`
     - Replace `dist/menu_translations/` with your backup `dist/menu_translations/`
     - Replace `current_config.json` with your backup `current_config.json`
     - Replace `dist/assets/variables.css` with your backup `dist/assets/variables.css`

6. **Start your server and test**

## Quick Reference

| Folder/File | When to backup |
|-------------|----------------|
| `_data/` | ✅ Always |
| `_defaults/` | ✅ Always |
| `_hooks/` | ✅ Always |
| `_modules_/` | ✅ Always |
| `integrations/` | ✅ Always |
| `current_config.json` | ✅ Always |
| `dist/assets/variables.css` | Only if you customized default theme globally |
| `_images/` | Only if you added custom images |
| `_locales/` | Only if you added custom translations |
| `dist/menu_translations/` | Only if you added custom menu translations |

## Troubleshooting

**Items disappeared?**
- Restore the `_data/` folder from your backup

**Crafting recipes missing?**
- Restore the `_hooks/` folder from your backup

**Settings reset?**
- Restore the `current_config.json` file from your backup

**Theme colors reset?**
- Restore `dist/assets/variables.css` from your backup

**Server won't start?**
- Wait 30 seconds (database is updating automatically)
- If still broken, restore your entire backup and contact support

{% hint style="info" %}
Keep your backup folder for a few days after updating, just in case
{% endhint %}
