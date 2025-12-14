# Adding custom weapon attachments/components

## Why this guide exists

In GTA V, each weapon has different component IDs for the same attachment type. For example:
- A suppressor for a Pistol uses `COMPONENT_AT_PI_SUPP`
- A suppressor for a Combat Pistol uses `COMPONENT_AT_PI_SUPP_02`

**The inventory system simplifies this:** You can create ONE item (like "suppressor") that automatically works with all compatible weapons by mapping multiple component IDs to it

## Step-by-step guide

### Step 1: Check if the item exists

First, check if an item for your attachment type already exists in your database

**For vanilla GTA weapons:**
- Most common attachments (suppressor, extended clip, flashlight, etc.) should already exist
- Use `/inventory` command in-game to check existing items

**For modded weapons:**
- You'll need to create a new item OR add the modded weapon's component hash to an existing item
- Example: If you have a modded AK47 with a suppressor, you can add its suppressor hash to the existing "suppressor" item

**Creating/Editing the item:**
1. Open the inventory management UI (`/inventory`)
2. Create a new item or edit an existing one
3. **IMPORTANT:** Set the correct item type:
   - `barrel` for suppressors, muzzle brakes
   - `clip` for magazines
   - `scope` for sights and optics
   - `flashlight` for tactical lights
   - `grip` for foregrips

<figure><img src="../../.gitbook/assets/edit-item-component-example.jpg" alt="Edit default suppressor item component example"><figcaption>Example with default suppressor</figcaption></figure>

### Step 2: Add component hashes

Now you need to add the component hash(es) that this item should apply to weapons

**Where to find component hashes:**

**For vanilla GTA weapons:**
- Check the [wiki](https://docs.fivem.net/docs/game-references/weapon-models/)
- Or search online for "GTA V weapon components list"

**For modded weapons:**
- Most likely your modded weapon script contains a text file, with the component hashes
- An example for component names, may be that they start with `COMPONENT_`
- Contact the weapon's creator/documentation if you can't find it

**How to add them:**
1. In the item edit screen for the attachment item, find the "Component Hashes" section
2. Click "Add Component Hash"
3. Enter the component hash (e.g., `COMPONENT_AT_PI_SUPP`)
4. Repeat for all components you want this attachment to work with

{% hint style="info" %}
The menu will show you what weapons are compatible with each component hash you add
{% endhint %}

<figure><img src="../../.gitbook/assets/edit-item-component-hashes-list.jpg" alt="Edit item hashes list example"><figcaption>Edit item hashes list example</figcaption></figure>

### Step 3: Test in-game
1. Give yourself the attachment item: `/giveitem [your_id] [item_name] 1` or through omnipack (`F1` while inventory is open)
2. Give yourself a compatible weapon
3. Try to attach the component

**That's it!** The system will automatically apply the correct component based on the weapon

## Complete Example

Let's say you want to add a suppressor for a modded weapon called "WEAPON_MODDEDAK47":

1. **Check existing items:** Open `/inventory` and search for "suppressor" - it exists!
2. **Edit the item:** Click edit on the suppressor item
3. **Add the hash:** Add `COMPONENT_MODDEDAK47_SUPP` to the component hashes list
4. **Save**
5. **Test:** Give yourself the suppressor and the modded AK47, then try attaching it

