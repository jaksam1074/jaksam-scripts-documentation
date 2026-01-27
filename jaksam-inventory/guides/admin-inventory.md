# How to open admin inventory (omnipack)
If you already have admin permissions (you can see it by typing `/inventory` in-game), you can open the omnipack by simply opening your inventory (F2), and then pressing F1.

Moving an item **TO** omnipack, will **delete** it

<figure><img src="../../.gitbook/assets/omnipack_screenshot.png" alt="Omnipack screenshot"><figcaption></figcaption></figure>

## Omnipack-only access
If you want to give access **only** to the omnipack without granting access to the admin menu and commands, use the specific permission:

```bash
add_ace identifier.license:26240584e4v4ca31b22d247b8be6921a8d22j6m1 jaksam_inventory.omnipack allow # Allows only omnipack permission
```

With this permission, the player will be able to:
- Use the omnipack (F1 in inventory)

But will **NOT** be able to:
- Open the admin menu (`/inventory`)
- Use admin commands (`/giveitem`, `/removeitem`, etc.)