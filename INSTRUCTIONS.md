# Shopping List Aggregator - User Guide

## What is This?

A standalone web app for aggregating shopping lists from multiple batch recipes. Perfect for restaurant prep or meal planning. Works offline once loaded, stores everything locally on your device.

**IMPORTANT**: For offline use without needing your laptop running, you must use the "Add to Home Screen" method (see below). This saves the app to your phone so it works independently.

## Quick Start

### On Desktop/Laptop
1. Open `shopping-list.html` in any modern browser (Chrome, Safari, Firefox, Edge)
2. That's it! The app works immediately - no installation, no server needed

### On iPhone/iPad (Recommended for Offline Use)

#### Method 1: Home Screen Web App (REQUIRED for Offline)
This method makes the app work without your laptop running!

1. **One-Time Setup - Host the file**:
   - **Option A (Best)**: Upload `shopping-list.html` to iCloud Drive or Dropbox
   - **Option B**: Use Safari's "Open File" feature (Files app integration)
   - **Option C**: Email the file to yourself and open from Mail

2. **Open in Safari** (must be Safari, not Chrome)
   - Navigate to the file location or URL
   - Wait for the page to fully load (you'll see the Shopping List interface)

3. **Add to Home Screen**:
   - Tap the Share button (square with arrow up) at the bottom
   - Scroll down and tap "Add to Home Screen"
   - Give it a name (e.g., "Shopping List")
   - Tap "Add"

4. **Use like a native app**:
   - Tap the icon on your home screen
   - Runs in full screen without Safari UI
   - **Works offline** - no laptop or server needed!
   - All data persists between sessions
   - Updates automatically when online

#### Method 2: Local Server (Development/Testing Only)
**WARNING**: This requires your MacBook to be running and on the same WiFi network!
- Only use this for testing changes to the file
- Not suitable for daily restaurant use
- See "Advanced: Local Server Setup" section below

### On Android
1. Open `shopping-list.html` in Chrome
2. Tap the menu (three dots)
3. Select "Add to Home Screen"
4. Use like a native app

## How to Use

### Managing Recipes

#### Add a New Recipe
1. Click **"Manage Recipes"** button in the header
2. Click **"+ Add New Recipe"**
3. Fill in:
   - **Recipe Name** (required) - e.g., "Ayam Goreng Paste"
   - **Yield Unit** (optional) - e.g., "batch", "kg", "liters"
   - **Notes** (optional) - e.g., "500g equals 30 pieces" or "Needs 8 hour marination"
   - **Ingredients** (at least one required):
     - **Name** - Type and see suggestions from existing ingredients
       - Autocomplete dropdown shows ingredients you've used before
       - Helps maintain consistent naming (e.g., always "Beef broth" not "Beef powder")
       - Selecting a suggestion auto-fills the unit field
     - **Quantity** - leave blank if not measured yet
     - **Unit** - Type and see suggestions from existing units (g, ml, pcs, bunch, etc.)
       - Auto-filled when you select an ingredient suggestion
       - Autocomplete shows units you've used before
     - **Substitution** - optional, e.g., "or use fresh galangal"
4. Click **"Add Recipe"**

**TIP**: The autocomplete feature learns from your existing recipes, making it easier to maintain consistent ingredient names and units across all recipes. This ensures proper aggregation in your shopping list!

#### Edit a Recipe
1. Go to **"Manage Recipes"**
2. Click the blue **pencil icon** on any recipe
3. Make your changes
4. Click **"Update Recipe"**

#### Duplicate a Recipe
1. Go to **"Manage Recipes"**
2. Click the green **copy icon** on any recipe
3. Recipe opens in the form with " (Copy)" added to name
4. Modify as needed and save

#### Delete a Recipe
1. Go to **"Manage Recipes"**
2. Click the red **trash icon** on any recipe
3. Confirm deletion

#### Mark Favorites
- Click the **star icon** next to any recipe name
- Yellow star = favorite
- Favorites appear at the top of the list
- Great for your most-used recipes

### Backup & Restore Recipes

#### Export Recipes (Backup)
1. Go to **"Manage Recipes"**
2. Click **"Export"** button (download icon)
3. A JSON file downloads: `recipes-backup-YYYY-MM-DD.json`
4. **What's included**:
   - All your recipes (ingredients, notes, favorites, substitutions)
   - Price history (last known prices from shopping trips)
5. File location:
   - **iPhone/iPad**: Files app > Downloads (or iCloud Drive if configured)
   - **Mac**: Downloads folder
   - **Android**: Downloads folder
6. **Tip**: Move to a dedicated backup folder for organization

#### Import Recipes (Restore/Merge)
1. Go to **"Manage Recipes"**
2. Click **"Import"** button (upload icon)
3. Select your backup JSON file
4. If you have existing recipes:
   - Imported recipes are **merged** (added to existing)
   - Price history is **merged** (new prices added, existing updated)
   - Your current recipes stay intact
   - New IDs assigned to avoid conflicts
5. Success message shows how many recipes and prices were added
6. **Use case**: Sync data between devices (iPad, iPhone, Mac)

#### Replace All Recipes
1. Go to **"Manage Recipes"**
2. Click **"⚠️ Replace All Recipes"** (red warning button)
3. Select your backup JSON file
4. **WARNING**: This completely replaces all current recipes and price history
5. Confirm the action (cannot be undone)
6. Use this to:
   - Switch between different menu sets (e.g., summer/winter)
   - Restore from backup after data loss
   - Start fresh with a different recipe collection

#### Backup Best Practices
- **Export regularly**: Weekly or after adding important recipes
- **Keep multiple backups**: Different dates in case you need older versions
- **Organize backups**: Create a folder like "Recipe Backups" in Files app
- **Test restores**: Occasionally try importing to make sure backups work
- **Cross-device**: Export on one device, import on another to sync recipes
- **Before major changes**: Export before deleting or editing many recipes

#### File Management Tips
- **iOS/iPadOS**: 
  - Save exports to iCloud Drive to sync across devices
  - Use Files app to organize into folders
  - Share via AirDrop to other devices
- **Mac**:
  - Move from Downloads to Documents or iCloud
  - Keep dated backups for version history
- **Android**:
  - Use Files by Google or similar to organize
  - Consider backing up to Google Drive

### Creating Shopping Lists

#### Select Recipes
1. On the main screen, check the boxes next to recipes you want to make
2. Use the **+/- buttons** or type to set batch quantities
3. The shopping list updates automatically on the right

#### Search Recipes
- When you have 4+ recipes, a search bar appears
- Type to filter recipes by name
- Great for quickly finding specific recipes

#### Track Shopping
1. As you shop, **tap the checkbox** next to each ingredient
2. Checked items move to "Purchased" section with green background
3. Click **"Reset"** button to uncheck all items (e.g., for next shopping trip)

#### Add Market Prices
1. In the shopping list, each ingredient has price input fields
2. Enter **unit price** format: `NT$ [price] / [quantity] [unit]`
   - Example: `NT$ 50 / 600 g` (50 NT$ per 600 grams)
   - Example: `NT$ 30 / 1 bunch` (30 NT$ per bunch)
   - Example: `NT$ 15 / 1 pcs` (15 NT$ per piece)
3. The app **automatically calculates** total cost based on quantity needed
4. Prices are **automatically saved** as you enter them (with 2-second delay)
5. If you need 1200g and price is NT$50/600g, it shows: `= NT$ 100`

#### Price History & Tracking
1. **Automatic Price Memory**:
   - Every price you enter is automatically saved as "last known price"
   - Date is recorded so you know when you last bought it
   - No manual save needed - happens in the background

2. **Load Last Prices**:
   - Click **"Load Prices"** button at the top of shopping list
   - Fills in all price fields with your last known prices
   - Saves time - no need to re-enter everything

3. **Price Change Indicators**:
   - When you enter a new price, app shows if it changed
   - **Red arrow up (↑)**: Price increased (e.g., ↑15%)
   - **Green arrow down (↓)**: Price decreased (e.g., ↓10%)
   - Helps spot market trends and inflation

4. **Estimated Total**:
   - Appears at top of shopping list: **"Estimated: NT$ XXX"**
   - Calculated from last known prices
   - Shows **before** you go shopping - know how much cash to bring
   - Updates as you select/deselect recipes

5. **Price History Backup**:
   - Export includes your price history
   - Import merges price data across devices
   - Sync prices between iPad, iPhone, Mac

#### View Costs
- Enter prices as you shop to track spending in real-time
- Each item shows its calculated total cost
- **"Total Cost"** at bottom shows current session total
- **"Estimated Total"** at top shows budget based on last prices
- Helps budget your shopping trip and compare with actual spending

### Dark Mode
- Click the **moon/sun icon** in the header to toggle dark mode
- Perfect for late-night restaurant prep
- Your preference is saved automatically

## Tips & Tricks

### Restaurant Use
- **Before service**: Select recipes and batch quantities for the week
- **At the market**: Use your phone in the app, check off items as you buy
- **After shopping**: Click "Reset" to prepare for next week

### Managing Many Recipes
- **Use favorites** for your regular rotation (star icon)
- **Use search** to quickly find specific recipes
- **Use notes** to remember important details like marination times
- **Use substitutions** to remember backup options

### Cost Tracking
- **Enter prices while shopping** using the unit price format (e.g., NT$50/600g)
- **Load last prices** before shopping to see estimates
- **Watch price changes** with up/down indicators
- **Plan your budget** using the estimated total at top
- **Track actual spending** using the total cost at bottom
- App automatically saves all prices for next time
- Export your price history to backup or sync devices
- Match the pricing format used at the market:
  - If vegetables are priced per 600g, enter: `50 / 600 g`
  - If sold by bunch, enter: `30 / 1 bunch`
  - If sold per piece, enter: `15 / 1 pcs`
- App automatically calculates total cost based on recipe quantities
- **Prices are session-based** - they don't save to recipes, so update each trip
- Leave prices blank for items you haven't priced yet
- Use the estimated total to budget and compare with actual spending

### Batch Adjustments
- Quickly adjust quantities with +/- buttons
- Type directly for large batches (e.g., 10 or 20)
- Different recipes can have different batch counts
- Shopping list automatically recalculates everything

### Data Safety
- All data stored locally on your device (localStorage)
- **Includes**: recipes, favorites, notes, substitutions, and price history
- **IMPORTANT**: Use Export feature to backup recipes regularly
- Export creates JSON files you can restore anytime
- Clearing browser data will erase everything (but you'll have backups!)
- Data persists across app restarts and phone reboots
- Each browser/device has separate data (use Export/Import to sync)
- Price history syncs when you import/export between devices

## Advanced: Local Server Setup

If you want to test on your phone via local network:

### On Mac/Linux:
```bash
cd path/to/shopping_list_aggregator
python3 -m http.server 8000
```

Then on your phone (connected to same WiFi):
- Find your computer's IP address (System Settings > Network)
- Open Safari/Chrome and go to: `http://YOUR_IP:8000/shopping-list.html`
- Example: `http://192.168.1.100:8000/shopping-list.html`

### On Windows:
```cmd
cd path\to\shopping_list_aggregator
python -m http.server 8000
```

## Troubleshooting

### "My recipes disappeared!"
- Check if you accidentally cleared browser/app data
- Make sure you're using the same browser/method (Safari home screen vs Chrome)
- Each browser stores data separately

### "Dark mode doesn't save"
- Make sure you're not in Private/Incognito mode
- Check browser settings allow localStorage

### "Can't add to home screen"
- On iPhone: Must use Safari browser, not Chrome
- Make sure the page fully loaded before trying
- Try refreshing the page first

### "App won't open offline"
- First load requires internet (to load React/Tailwind from CDN)
- After first load, works offline
- If stuck, reload once while online

### "Search bar missing"
- Search only appears when you have 4+ recipes
- Add more recipes to see it

### "Prices not showing"
- Make sure you entered prices when creating/editing recipes
- Prices are optional - blank is normal
- Check that quantity is also filled in (prices need quantities)

## File Information

- **Single HTML File**: `shopping-list.html` (no other files needed)
- **File Size**: ~30-40 KB
- **No Internet Required**: After first load
- **No Account/Login**: Everything stays on your device
- **Privacy**: Zero tracking, zero external data collection

## Support

This is a simple standalone tool. If something's not working:
1. Try refreshing the page
2. Check browser console for errors (F12 on desktop)
3. Clear localStorage and start fresh (will delete all recipes)
4. Make sure you're using a modern browser (last 2 years)

## License

This is your file - use it however you want! Modify, share, improve as needed.
