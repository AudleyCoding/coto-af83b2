# Shopping List Aggregator - User Guide

## What is This?

A standalone web app for aggregating shopping lists from multiple batch recipes. Perfect for restaurant prep or meal planning. Works offline once loaded, stores everything locally on your device.

## Quick Start

### On Desktop/Laptop
1. Open `shopping-list.html` in any modern browser (Chrome, Safari, Firefox, Edge)
2. That's it! The app works immediately - no installation, no server needed

### On iPhone/iPad (Recommended)

#### Method 1: Home Screen Web App (Best Experience)
1. **Host the file** - Choose one option:
   - Upload to Dropbox/iCloud and get a sharing link
   - Email the file to yourself and save to Files app
   - Use a local server (see Advanced section)

2. **Open in Safari** (must be Safari, not Chrome)
   - Navigate to the file location or URL
   - Wait for the page to fully load

3. **Add to Home Screen**:
   - Tap the Share button (square with arrow up) at the bottom
   - Scroll down and tap "Add to Home Screen"
   - Give it a name (e.g., "Shopping List")
   - Tap "Add"

4. **Use like a native app**:
   - Tap the icon on your home screen
   - Runs in full screen without Safari UI
   - All data persists between sessions
   - Works offline after first load

#### Method 2: Quick Access (No Installation)
- Open the file directly in Safari whenever needed
- Bookmark it for quick access
- Less convenient but still works perfectly

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
     - Name - e.g., "shallot paste"
     - Quantity - leave blank if not measured yet
     - Unit - e.g., "g", "ml", "pcs"
     - Price - optional, in NT$ (e.g., 150)
     - Substitution - optional, e.g., "or use fresh galangal"
4. Click **"Add Recipe"**

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

#### View Costs
- If you added prices, each ingredient shows its cost in NT$
- **"Estimated Total"** appears at the bottom
- Helps budget your shopping trip

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
- Add prices to frequently bought items
- Leave prices blank for items that vary
- Update prices when they change significantly
- Use the total to compare with actual spending

### Batch Adjustments
- Quickly adjust quantities with +/- buttons
- Type directly for large batches (e.g., 10 or 20)
- Different recipes can have different batch counts
- Shopping list automatically recalculates everything

### Data Safety
- All data stored locally on your device (localStorage)
- **Back up important recipes**: Copy the text from recipes periodically
- Clearing browser data will erase recipes
- Data persists across app restarts and phone reboots

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
