# Shopping List Aggregator - Features & Offline Setup

## How to Get the App Running Offline

### The Problem
By default, if you access the app through a local server (like `python3 -m http.server`), it requires your MacBook to be running and connected to the same WiFi network. This is not practical for daily restaurant use at the market.

### The Solution: Progressive Web App (PWA) via "Add to Home Screen"

The app is designed as a Progressive Web App that can work completely offline once properly installed on your iPhone/iPad. Here's how:

#### Step-by-Step Offline Setup

**1. Choose a Hosting Method**

You need to host the file in a location accessible to your iPhone. Pick ONE of these options:

- **Option A: iCloud Drive (Recommended)**
  1. On your Mac, copy `shopping-list.html` to iCloud Drive
  2. On your iPhone, open Files app → iCloud Drive
  3. Tap on `shopping-list.html`
  4. It will open in Safari

- **Option B: Dropbox/Google Drive**
  1. Upload `shopping-list.html` to your cloud storage
  2. Get a public sharing link
  3. Open the link in Safari on your iPhone
  4. Wait for page to fully load

- **Option C: Email to Yourself**
  1. Email `shopping-list.html` as an attachment to yourself
  2. On iPhone, open the email in Mail app
  3. Tap the attachment
  4. Choose "Open in Safari"

- **Option D: Local Network (One-time setup only)**
  1. On Mac: `python3 -m http.server 8000` (in the project folder)
  2. Find Mac's IP: System Settings → Network (e.g., 192.168.1.100)
  3. On iPhone (same WiFi): Safari → `http://192.168.1.100:8000/shopping-list.html`
  4. Proceed immediately to Step 2 below before closing the server

**2. Add to Home Screen (CRITICAL STEP)**

This is what makes it work offline:

1. With the app open in Safari on your iPhone/iPad
2. Tap the **Share** button (square with arrow pointing up) at the bottom
3. Scroll down and tap **"Add to Home Screen"**
4. Name it (e.g., "Shopping List" or "Coto Shopping")
5. Tap **"Add"**

**3. Verify Offline Functionality**

1. Close Safari completely
2. Turn off WiFi or disconnect from your Mac
3. Tap the new app icon on your home screen
4. The app should open and work perfectly!

#### Why This Works

When you "Add to Home Screen":
- Safari caches the entire HTML file on your device
- React and Tailwind CSS libraries are cached from their CDNs
- All your data is stored in localStorage (never leaves your device)
- The app becomes a standalone web app (no Safari UI)
- Works exactly like a native iOS app
- Survives phone restarts, iOS updates, etc.

#### Important Notes

- **First load requires internet**: To download React/Tailwind from CDNs
- **After that, 100% offline**: No internet or server needed
- **Data is local only**: Each device stores its own data
- **Use Export/Import**: To sync recipes between devices (iPad ↔ iPhone ↔ Mac)
- **Updates to the file**: If you modify `shopping-list.html`, you need to remove and re-add the home screen icon

---

## Feature List

1. Recipe Management (Add, Edit, Delete, Duplicate)
2. Batch Recipe Selection and Scaling
3. Automatic Shopping List Aggregation
4. Ingredient Purchase Tracking (Checkboxes)
5. Search and Filter Recipes
6. Recipe Notes Field
7. Favorite/Star Recipes
8. Ingredient Substitutions
9. Unit-Based Price Tracking (NT$)
10. Last Known Price Memory
11. Price Change Indicators
12. Estimated Total Cost (Pre-Shopping)
13. Dark Mode
14. Export Recipes with Price History
15. Import Recipes (Merge Mode)
16. Replace All Recipes (Clean Import)
17. Ingredient Name Autocomplete
18. Unit Autocomplete
19. Auto-Fill Unit from Previous Usage
20. Offline Progressive Web App (PWA)
21. iOS Home Screen Optimization
22. Touch-Friendly Mobile Interface
23. Responsive Design (Mobile-First)
24. localStorage Data Persistence
25. Shopping List Reset Function

---

## Detailed Feature Descriptions

### 1. Recipe Management (Add, Edit, Delete, Duplicate)
**What it does**: Complete CRUD operations for recipes with ingredients, quantities, units, and metadata.

**How to use**:
- **Add**: Tap "Manage Recipes" → "+ Add New Recipe" → Fill form → "Add Recipe"
- **Edit**: In Manage Recipes, tap blue pencil icon on any recipe
- **Delete**: Tap red trash icon → Confirm deletion
- **Duplicate**: Tap green copy icon → Recipe opens with "(Copy)" suffix → Modify and save

---

### 2. Batch Recipe Selection and Scaling
**What it does**: Select multiple recipes and set how many batches of each you need to make.

**How to use**:
- Check the box next to any recipe on the main screen
- Use +/- buttons to adjust batch count
- Or type directly into the number field for large quantities
- Shopping list updates automatically with scaled quantities

---

### 3. Automatic Shopping List Aggregation
**What it does**: Combines ingredients from all selected recipes, automatically adding quantities of the same ingredient together.

**How to use**:
- Select recipes → Shopping list appears on the right
- Ingredients with same name are automatically combined
- Shows total quantity needed across all recipes
- Example: Recipe A needs 500g salt + Recipe B needs 300g salt = 800g salt in shopping list

---

### 4. Ingredient Purchase Tracking (Checkboxes)
**What it does**: Check off items as you buy them at the market. Checked items move to a "Purchased" section.

**How to use**:
- Tap checkbox next to each ingredient as you buy it
- Checked items move to bottom with green background and strikethrough
- Tap "Reset" button when done shopping to uncheck all items for next trip

---

### 5. Search and Filter Recipes
**What it does**: Quickly find recipes by typing part of the recipe name. Appears automatically when you have 4+ recipes.

**How to use**:
- Type in the search bar at the top
- Recipe list filters in real-time as you type
- Clear search to see all recipes again

---

### 6. Recipe Notes Field
**What it does**: Add custom notes to any recipe (e.g., preparation time, yield info, special instructions).

**How to use**:
- When adding/editing a recipe, fill in the "Notes" field
- Examples: "500g equals 30 pieces", "Needs 8 hour marination", "Spicy version for weekend menu"
- Notes appear in italic text below the recipe name

---

### 7. Favorite/Star Recipes
**What it does**: Mark frequently-used recipes as favorites. They appear at the top of the list with a yellow star.

**How to use**:
- Tap the star icon next to any recipe name
- Yellow star = favorited, gray star = not favorited
- Favorites automatically sort to the top of the recipe list

---

### 8. Ingredient Substitutions
**What it does**: Document alternative ingredients for each item (e.g., "or use fresh galangal instead").

**How to use**:
- When adding/editing ingredients, fill in the "Substitution" field
- Text appears below the main ingredient info
- Helpful when market is out of specific items

---

### 9. Unit-Based Price Tracking (NT$)
**What it does**: Enter market prices in realistic format: price per quantity per unit (e.g., NT$50 per 600g).

**How to use**:
- In shopping list, enter three values per ingredient:
  - Price: e.g., 50 (in NT$)
  - Unit Qty: e.g., 600
  - Unit Type: e.g., g
- App calculates total cost automatically
- Example: Need 1200g, price is NT$50/600g → Total: NT$100

---

### 10. Last Known Price Memory
**What it does**: Automatically saves every price you enter with a date stamp. Remembers prices across shopping trips.

**How to use**:
- Just enter prices normally - saving happens automatically (2-second delay)
- Prices are stored in localStorage
- Below each ingredient, you'll see: "Last: NT$50/600g (2025-11-17)"
- Click "Load Prices" button to fill all fields with saved prices

---

### 11. Price Change Indicators
**What it does**: When you enter a new price different from the last saved price, shows % increase/decrease.

**How to use**:
- Enter a price that differs from your last known price
- Red arrow up (↑) with percentage = price increased (e.g., ↑15%)
- Green arrow down (↓) with percentage = price decreased (e.g., ↓10%)
- Helps you spot market trends and inflation

---

### 12. Estimated Total Cost (Pre-Shopping)
**What it does**: Shows estimated shopping cost based on last known prices BEFORE you go to the market.

**How to use**:
- Select your recipes for the shopping trip
- At the top of shopping list: "Estimated: NT$ XXX (based on last prices)"
- Tells you how much cash to bring
- Updates automatically as you add/remove recipes

---

### 13. Dark Mode
**What it does**: Dark gray/black color scheme for nighttime or low-light use.

**How to use**:
- Tap the moon/sun icon in the header
- Toggle between light and dark themes
- Preference is saved automatically
- Perfect for late-night restaurant prep

---

### 14. Export Recipes with Price History
**What it does**: Downloads all recipes AND price history as a JSON backup file.

**How to use**:
- Go to "Manage Recipes"
- Tap "Export" button (download icon)
- File downloads: `recipes-backup-YYYY-MM-DD.json`
- Includes: recipes, ingredients, notes, favorites, substitutions, AND all last known prices
- Store in iCloud/Dropbox for backup

---

### 15. Import Recipes (Merge Mode)
**What it does**: Imports recipes from backup file, merging with existing data. Updates recipes with same name, adds new ones.

**How to use**:
- Go to "Manage Recipes" → "Import"
- Select your JSON backup file
- **Merge logic**:
  - If recipe name exists: updates it with imported version
  - If recipe is new: adds it with new ID
  - Price history: merges (adds new prices, updates existing)
- Shows: "X updated, Y added, Z prices"
- Perfect for syncing between devices (iPad → iPhone)

---

### 16. Replace All Recipes (Clean Import)
**What it does**: Completely replaces all recipes and price history with imported data. Destructive operation.

**How to use**:
- Go to "Manage Recipes" → "⚠️ Replace All Recipes" (red button)
- Select JSON backup file
- Confirm warning (cannot be undone)
- All existing recipes and prices are deleted and replaced
- Use case: Switching between different menu sets (summer/winter menus)

---

### 17. Ingredient Name Autocomplete
**What it does**: Shows dropdown of existing ingredient names as you type, preventing typos and naming inconsistencies.

**How to use**:
- Start typing an ingredient name in recipe form
- Dropdown appears with matching ingredients from your existing recipes
- Click/tap a suggestion to auto-fill the exact name
- Ensures "Beef broth" is always "Beef broth" (not "beef broth" or "Beef powder")
- Critical for proper aggregation in shopping list

---

### 18. Unit Autocomplete
**What it does**: Shows dropdown of units you've used before (g, ml, pcs, bunch, Tbsp, etc.).

**How to use**:
- Click into the Unit field when adding an ingredient
- Dropdown shows all units from existing recipes, sorted alphabetically
- Select one to auto-fill
- Maintains consistency (always "g" not sometimes "grams")

---

### 19. Auto-Fill Unit from Previous Usage
**What it does**: When you select an ingredient from autocomplete, automatically fills in the unit you used last time.

**How to use**:
- Type ingredient name and select from dropdown
- Unit field automatically fills with the same unit you used before
- Example: Select "Shallot paste" → unit auto-fills as "g"
- Saves time and ensures consistency

---

### 20. Offline Progressive Web App (PWA)
**What it does**: Works completely offline after installation, no internet or server required.

**How to use**:
- Follow "Add to Home Screen" instructions (see Offline Setup section above)
- After installation, works without WiFi, cellular data, or laptop running
- All functionality available offline except initial CDN downloads

---

### 21. iOS Home Screen Optimization
**What it does**: Custom app icon, full-screen mode, no Safari UI when launched from home screen.

**How to use**:
- Add to home screen (see above)
- Tap the icon
- Opens in full-screen mode without Safari address bar/buttons
- Blue icon with shopping cart emoji
- Looks and feels like a native iOS app

---

### 22. Touch-Friendly Mobile Interface
**What it does**: All buttons, checkboxes, and inputs are sized for finger taps (minimum 44x44px per iOS guidelines).

**How to use**:
- No special action needed
- Everything is sized for easy thumb/finger interaction
- No tiny click targets that require precision

---

### 23. Responsive Design (Mobile-First)
**What it does**: Layout adapts to screen size. Mobile (vertical stacking) → Desktop (side-by-side panels).

**How to use**:
- No action needed
- On phone: Recipe list and shopping list stack vertically
- On tablet/desktop: Side-by-side layout
- All features work on any screen size

---

### 24. localStorage Data Persistence
**What it does**: All data (recipes, prices, preferences) is stored in browser's localStorage. Survives app closes, phone restarts.

**How to use**:
- Automatic - no action needed
- Data saves continuously as you work
- Persists across sessions
- **Important**: Each device/browser has separate storage
- Use Export/Import to sync between devices

---

### 25. Shopping List Reset Function
**What it does**: Unchecks all purchased items with one tap, preparing for the next shopping trip.

**How to use**:
- After shopping trip is complete (all items checked)
- Tap "Reset" button at top of shopping list
- All checkboxes uncheck, items move back to "remaining items"
- Ready for next shopping trip
- Does NOT delete or change recipes or prices

---

## Summary

This app combines 25 features into a simple, offline-capable shopping list tool designed specifically for restaurant batch cooking workflows. The key innovations are:

1. **Offline-first**: Works without internet after initial setup
2. **Consistent naming**: Autocomplete prevents aggregation errors
3. **Price tracking**: Remembers prices across trips, shows estimates before shopping
4. **Mobile-optimized**: Built for iPhone use at the market
5. **Data portability**: Export/import for backup and cross-device sync

Perfect for Coto Makassar's daily market shopping needs!
