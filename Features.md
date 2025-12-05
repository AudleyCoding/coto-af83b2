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
  2. Find Mac's IP: System Settings → Network (e.g., 10.0.4.101)
  3. On iPhone (same WiFi): Safari → `http://10.0.4.101:8000/shopping-list.html`
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
17. Ingredient Name Autocomplete (Custom Searchable)
18. Standardized Unit Dropdown
19. Auto-Fill Unit from Previous Usage
20. Automatic Lowercase for Ingredient Names
21. Shopping Location Categorization
22. Planned Purchase Cost Calculator
23. Offline Progressive Web App (PWA)
24. iOS Home Screen Optimization
25. Touch-Friendly Mobile Interface
26. Responsive Design (Mobile-First)
27. localStorage Data Persistence
28. Shopping List Reset Function
29. Keyboard Navigation for Autocomplete
30. Quick Add Items (Add one-off items without recipes)
31. Price Management (Update all prices in one place)
32. Shopping Trip History (Track expenses across multiple vendors)
33. Quick Log for Multi-Stop Shopping Trips
34. Vendor Management and Auto-Suggestion
35. CSV Export for Accounting Integration
36. Always-Visible Action Buttons with Disabled States

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
**What it does**: Check off items as you buy them at the market. Checked items move to a "Purchased" section. Action buttons (Quick Log, Reset) are always visible and become enabled when items are checked.

**How to use**:
- Tap checkbox next to each ingredient as you buy it
- Checked items move to bottom with green background and strikethrough
- Action buttons at the top activate:
  - **Quick Log (💰)** - Becomes green when items are checked, click to save trip
  - **Reset (🔄)** - Becomes red when items are checked, click to uncheck all
  - **Load Prices (🔄)** - Becomes blue when you have saved prices
- Buttons are always visible but grayed out when disabled (consistent UI layout)

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

### 9. Package-Based Price Tracking (NT$)
**What it does**: Enter actual package prices based on what you buy at the market, separate from recipe amounts. Supports flexible data entry and automatic unit conversions.

**How to use**:
- **Recipe amount shown as reference**: "Need: 360 g" displays what your recipe requires
- **Enter package information**: The actual package size you purchased
  - Price: e.g., 45 (in NT$)
  - Package Qty: e.g., 400 (the size of package you bought)
  - Package Unit: e.g., g (with dropdown suggestions: g, kg, 斤, ml, L, pcs, pack, bag, bottle, etc.)
- **All fields are optional and independent**: Enter what you know, leave the rest blank
- **Visual feedback**:
  - ✓ Complete data: Shows total cost and packages needed
  - ⚠ Partial data: "Need price" or "Need package size" warnings
  - Unit price displayed: "NT$0.11/g" when complete
- **Smart calculations**: 
  - App calculates packages needed: "(0.90 pkg)" if you need less than 1 package
  - Automatic unit conversions: Buy in kg, recipe in g? No problem!
  - Only includes items with complete data in cost totals

**Example scenarios**:

*Complete entry:*
```
coconut palm sugar(6 pucks) - as needed
Need: 360 g
NT$ [45] / [400] [g] (package)
= NT$ 41 (0.90 pkg)
NT$0.11/g
```

*Partial entry (know package size, not price yet):*
```
ginger paste - as needed
Need: 400 g
NT$ [___] / [500] [g] (package)
⚠ Need price
```

*Different units (buy kg, recipe needs g):*
```
shallot paste - as needed
Need: 800 g
NT$ [95] / [1] [kg] (package)
= NT$ 76 (0.80 pkg)
NT$95.00/kg
```

**Why package-based pricing?**
- Reflects reality: You buy packages, not exact recipe amounts
- Accurate tracking: Compare prices across different package sizes
- Flexible: Enter what you know, fill in the rest later
- Future-proof: Price history stays accurate even if package sizes change

**Unit conversions supported**:
- Weight: g ↔ kg (×1000), 斤 ↔ g (×600), lb ↔ g, oz ↔ g
- Volume: ml ↔ L (×1000)

---

### 10. Last Known Price Memory (Package-Based)
**What it does**: Automatically saves every price you enter with package information and date stamp. Remembers prices across shopping trips.

**How to use**:
- Just enter prices normally - saving happens automatically (2-second delay)
- Requires complete data: price + package quantity + package unit
- Prices are stored in localStorage with package details
- Price history tracks package sizes for accurate comparisons

**What's saved**:
```javascript
{
  price: 45,
  packageQuantity: 400,
  packageUnit: "g",
  date: "2025-11-20"
}
```

---

### 11. Price Change Indicators (Unit Price Based)
**What it does**: Compares current unit price to last known unit price, shows % increase/decrease. Accounts for different package sizes.

**How to use**:
- Enter a price with package information
- If last known price exists, app calculates unit prices and compares
- Red arrow up (↑) with percentage = unit price increased (e.g., ↑15%)
- Green arrow down (↓) with percentage = unit price decreased (e.g., ↓10%)
- Accurate even if package sizes differ (e.g., comparing 400g package to 500g package)

**Example**:
- Last time: NT$50 / 500g = NT$0.10/g
- This time: NT$48 / 400g = NT$0.12/g
- Shows: ↑20% (unit price increased despite lower package price)

---

### 12. Estimated Total Cost (Pre-Shopping, Package-Based)
**What it does**: Shows estimated shopping cost based on last known package prices BEFORE you go to the market.

**How to use**:
- Select your recipes for the shopping trip
- At the top of shopping list: "Estimated: NT$ XXX (based on last prices)"
- Calculation uses saved package information
- Tells you how much cash to bring
- Updates automatically as you add/remove recipes
- Handles unit conversions automatically

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
**What it does**: Shows a searchable dropdown of existing ingredient names as you type, preventing typos and naming inconsistencies.

**How to use**:
- Start typing an ingredient name in recipe form (automatically converted to lowercase)
- Custom dropdown appears with up to 10 matching ingredients from your existing recipes
- Results filtered in real-time: exact matches first, then starts-with, then contains
- Each suggestion shows: ingredient name, unit, and typical quantity
- **Select with mouse**: Click any suggestion
- **Select with keyboard**: 
  - Arrow Down/Up to navigate suggestions
  - Enter to select highlighted suggestion
  - Escape to close dropdown
- Keep typing to add a new ingredient if it doesn't exist in suggestions
- Selecting a suggestion auto-fills both name and unit
- Critical for proper aggregation - ensures "beef broth" is always "beef broth"

---

### 18. Unit Autocomplete
**What it does**: Standardized dropdown with 18 common units organized by category (weight, volume, count).

**How to use**:
- Click the Unit dropdown when adding an ingredient
- Select from standardized options:
  - **Weight**: g, kg, lb, oz
  - **Volume**: ml, L, cup, Tbsp, tsp
  - **Count**: pcs, bag, bunch, can, jar, bottle, box
  - **Other**: batch, as needed
- Uses `<select>` dropdown (not text input) for consistency
- Auto-selected when you choose an ingredient from autocomplete
- Ensures all recipes use same unit names (always "g" not "grams" or "G")

---

### 19. Auto-Fill Unit from Previous Usage
**What it does**: When you select an ingredient from autocomplete, automatically fills in the unit you used last time.

**How to use**:
- Type ingredient name and select from dropdown
- Unit field automatically fills with the same unit you used before
- Example: Select "Shallot paste" → unit auto-fills as "g"
- Saves time and ensures consistency

---

### 20. Automatic Lowercase for Ingredient Names
**What it does**: Automatically converts all ingredient names to lowercase to ensure consistent aggregation across recipes.

**How to use**:
- No action needed - happens automatically!
- Type "Beef Broth" → automatically becomes "beef broth"
- Applies when:
  - Typing in ingredient field (real-time conversion)
  - Saving/updating recipes
  - Importing recipes from JSON
  - Replacing all recipes
- Only applies to ingredient names, NOT recipe names
- Ensures "beef broth" and "Beef Broth" aggregate together properly
- Critical for accurate shopping list totals

---

### 21. Shopping Location Categorization
**What it does**: Organizes shopping list by purchase location (Street Market, Supermarket, Big King, etc.) with collapsible sections. Helps optimize multi-stop shopping trips.

**How to use**:
- **Add location to ingredients**: When creating/editing a recipe, fill in the "Purchase location" field for each ingredient
- **Autocomplete suggestions**: Dropdown shows existing locations from your recipes
- **Shopping list grouping**: Ingredients automatically group by location
- **Section headers**: Each location has a header showing count (e.g., "🛒 Street Market (5 items)")
- **Expand/collapse**: Tap section header to show/hide items (all expanded by default for easy scanning)
- **Unspecified category**: Ingredients without location appear in "📍 Unspecified" section at bottom
- **Statistics summary**: Top of shopping list shows item counts per location
- **Purchased items**: Location appears next to checked-off items
- **Smart merging**: When same ingredient in multiple recipes, uses first non-empty location
- **Backward compatible**: Existing recipes work fine without location data

**Example workflow**:
1. Tuesday morning: Select recipes for the week
2. Shopping list shows: Street Market (8 items), Supermarket (12 items), Big King (3 items)
3. First stop: Street Market - expand that section, shop, check items off
4. Second stop: Supermarket - expand that section, etc.
5. Optimizes route and ensures you don't miss items at each location

---

### 22. Planned Purchase Cost Calculator
**What it does**: Allows users to mark which ingredients they actually plan to buy and calculates total cost only for those items. Hides items not planned for purchase to reduce clutter.

**How to use**:
- **Toggle items**: Tap the shopping bag icon in the top-right corner of each ingredient card
  - Blue bag = Plan to Buy (included in cost, visible)
  - Gray bag = Not planning to buy (excluded from cost, HIDDEN from view)
- **Default state**: All items start as "Plan to Buy" when recipes are selected
- **Cost summary**: Blue box at top shows total cost for planned items only
- **Item counts**: Shows how many items selected, how many have prices, how many don't
- **Location breakdown**: See subtotals per shopping location (Street Market: NT$850, etc.)
- **Quick actions**:
  - "Select All" button: Shows all items (marks all for purchase)
  - "Deselect All" button: Hides all items (removes all from planned purchase)
- **Price warnings**: Lists items marked for purchase but missing price data

**Three states per ingredient**:
1. **Plan to Buy + Not Purchased**: Blue bag icon, normal appearance, included in cost, visible
2. **Plan to Buy + Purchased**: Blue bag icon, green background with strikethrough, included in total, visible
3. **NOT Plan to Buy**: Gray bag icon, HIDDEN from view, excluded from cost

**Real-world example**:
- Tuesday prep: Select 5 recipes → 30 ingredients appear
- You already have: oil, salt, garlic → Tap their bag icons (turns gray, items disappear)
- 27 items remain visible, total shows: "NT$ 2,450 (18 with prices, 9 without)"
- Breakdown: Street Market NT$850 (8 items), Supermarket NT$1,200 (7 items), Big King NT$400 (3 items)
- Missing prices: Shows which 9 items need prices entered
- Go shopping: Check items off as you buy them
- Return: Total still shows NT$2,450 for what you actually purchased

**Benefits**:
- Only calculate cost for items you actually need to buy
- Hide items you already have at the restaurant
- See accurate shopping budget before leaving
- Cleaner list with fewer distractions
- Location subtotals help plan multi-stop route
- Track what you spent vs what you planned

---

### 23. Offline Progressive Web App (PWA)
**What it does**: Works completely offline after installation, no internet or server required.

**How to use**:
- Follow "Add to Home Screen" instructions (see Offline Setup section above)
- After installation, works without WiFi, cellular data, or laptop running
- All functionality available offline except initial CDN downloads

---

### 24. iOS Home Screen Optimization
**What it does**: Custom app icon, full-screen mode, no Safari UI when launched from home screen.

**How to use**:
- Add to home screen (see above)
- Tap the icon
- Opens in full-screen mode without Safari address bar/buttons
- Blue icon with shopping cart emoji
- Looks and feels like a native iOS app

---

### 25. Touch-Friendly Mobile Interface
**What it does**: All buttons, checkboxes, and inputs are sized for finger taps (minimum 44x44px per iOS guidelines).

**How to use**:
- No special action needed
- Everything is sized for easy thumb/finger interaction
- No tiny click targets that require precision

---

### 26. Responsive Design (Mobile-First)
**What it does**: Layout adapts to screen size. Mobile (vertical stacking) → Desktop (side-by-side panels).

**How to use**:
- No action needed
- On phone: Recipe list and shopping list stack vertically
- On tablet/desktop: Side-by-side layout
- All features work on any screen size

---

### 27. localStorage Data Persistence
**What it does**: All data (recipes, prices, preferences) is stored in browser's localStorage. Survives app closes, phone restarts.

**How to use**:
- Automatic - no action needed
- Data saves continuously as you work
- Persists across sessions
- **Important**: Each device/browser has separate storage
- Use Export/Import to sync between devices

---

### 28. Shopping List Reset Function
**What it does**: Unchecks all purchased items with one tap, preparing for the next shopping trip.

**How to use**:
- After shopping trip is complete (all items checked)
- Tap "Reset" button at top of shopping list
- All checkboxes uncheck, items move back to "remaining items"
- Ready for next shopping trip
- Does NOT delete or change recipes or prices

---

### 29. Keyboard Navigation for Autocomplete
**What it does**: Full keyboard support for ingredient autocomplete dropdown navigation.

**How to use**:
- Type in ingredient field to open autocomplete suggestions
- **Arrow Down**: Move to next suggestion
- **Arrow Up**: Move to previous suggestion
- **Enter**: Select currently highlighted suggestion
- **Escape**: Close autocomplete dropdown
- Highlighted suggestion shows in blue
- Great for desktop users and power users
- Also works on iPad with external keyboard

---

### 30. Price History Tracking and Visualization
**What it does**: Automatically tracks ingredient prices over time and visualizes trends with interactive charts and statistics.

**How to use**:
- Tap "Price History" button in main header (trending up icon)
- View all ingredients with price data, sorted by most recent update
- See trend indicators: ↑ (>10% above average - red), ↓ (>10% below average - green), → (stable - gray)
- Tap any ingredient to view detailed price history
- **Detail view shows**:
  - Interactive line chart of last 12 months (powered by Chart.js)
  - Current price, 6-month average, min/max prices
  - Percentage change vs average
  - Full price history table (reverse chronological)
  - Min and max points highlighted on chart (green/red dots)
- **Automatic logging**: Prices auto-save to history when you update them on shopping list
- Works offline - all data stored locally in browser localStorage

**Why it's useful**:
- Identify seasonal price patterns (when is ginger cheapest?)
- Make informed purchasing decisions (is this a good price?)
- Track budget changes over time
- Spot price increases early
- Historical data helps negotiate with vendors
- Plan shopping trips around price trends

**Mobile optimized**:
- Canvas-based Chart.js rendering (smooth on mobile)
- Responsive charts adapt to portrait/landscape
- Touch-friendly interactions and tooltips
- Clean scrolling on price history tables
- Dark mode support for all charts and graphs
- 44px+ tap targets throughout

**Export/Import**:
- Price history is included in recipe exports
- Transfer data between devices using Export → Import
- View JSON in browser if download doesn't work, copy/paste into text editor, save, then import

---

### 30. Quick Add Items
**What it does**: Quickly add one-off items directly to your shopping list without creating a recipe. Perfect for non-recipe items like salt, paper towels, cleaning supplies, or anything you forgot to add to a recipe. **Now supports smart parsing** - type "salt 1000g" and it automatically extracts name, quantity, and unit!

**How to use**:
1. In the "⚡ Quick Add Items" section above the shopping list
2. Type the item name with optional quantity and unit:
   - Simple: `salt` (just the name)
   - With quantity: `salt 1000g` (parses to: name="salt", qty=1000, unit="g")
   - With space: `sugar 2 kg` (parses to: name="sugar", qty=2, unit="kg")
   - Numbers only: `flour 500` (parses to: name="flour", qty=500)
3. Press Enter or tap "+ Add" button
4. Item appears in Quick Items list showing the quantity (e.g., "salt 1000g")
5. Items appear in your shopping list with ⚡ badge
6. In Price Management view, quantity and unit are **pre-filled** - just add the price!

**Supported formats**:
- `salt 1000g` → name: "salt", qty: 1000, unit: "g"
- `sugar 2kg` → name: "sugar", qty: 2, unit: "kg"
- `flour 500 g` → name: "flour", qty: 500, unit: "g"
- `oil 1.5L` → name: "oil", qty: 1.5, unit: "L"
- `salt` → name: "salt" (no quantity)

**Example use cases**:
- Market prep: Add all items with quantities beforehand, then just fill in prices at market
- Forgot to add "salt 1000g" to a recipe, need to grab it anyway
- One-time items: "batteries", "paper towels 6pk", "cleaning spray 500ml"
- Test ingredients you're considering for new recipes
- Items you need to buy but don't want to create a full recipe for

**Features**:
- **Smart parsing**: Automatically extracts quantity and unit from input
- **Visual display**: Shows "salt 1000g" in Quick Items list (quantity in blue)
- **Price Management integration**: Quantity/unit pre-filled when updating prices
- Autocomplete from all known ingredient names
- Persists in localStorage like all other data
- Integrates seamlessly with shopping list
- Visual ⚡ badge distinguishes them from recipe items
- Can enter prices and track purchases just like recipe ingredients
- Removes automatically when you delete them (won't reappear)

**Smart behavior**:
- Prevents duplicates (alerts if item already in quick list)
- Merges with recipe ingredients if same name (combines quantities)
- Survives between shopping trips until manually removed
- Includes in Planned Purchase Cost calculations
- Shows in location-grouped shopping list sections

---

### 31. Price Management
**What it does**: Dedicated view to update prices for all ingredients in one place. Perfect for price-checking trips to the market where you're just gathering price information without shopping.

**How to use**:
1. Click the green **"Update Prices"** button at the top of the main screen
2. See master list of ALL unique ingredients from all recipes (alphabetically sorted)
3. For each ingredient, enter:
   - **Price (NT$)**: Package price at the market
   - **Qty**: Package quantity/size
   - **Unit**: Package unit (g, kg, 斤, ml, L, etc.)
4. Prices auto-save after 2 seconds (same as shopping list)
5. Click **"Back to Shopping List"** when done

**Display information**:
- **Ingredient name**: Bold at top of each card
- **📊 button**: Quick access to price history charts (if available)
- **Last known price**: Shows previous price, quantity, unit, and date
- **Calculated unit price**: Auto-displays when price + quantity entered (e.g., "= NT$0.11/g")

**Example workflow - Market price checking trip**:
1. Go to market with iPad (no shopping, just checking prices)
2. Open app → Click "Update Prices"
3. Walk through vendors:
   - Street Market: Update shallot paste, garlic paste, ginger prices
   - Supermarket: Update oil, coconut milk, spice prices  
   - Big King: Update bulk items
4. All prices automatically saved and ready for next shopping trip
5. Return home → Shopping list now shows updated estimates

**Features**:
- **Auto-prefill package sizes**: Quantity/unit fields automatically filled from:
  1. Quick Add items (if you typed "salt 1000g", it pre-fills 1000g)
  2. Last known prices (if you bought this before, shows previous package size)
  3. Priority: Quick Add > Last Known > Empty
- **Time saver**: You buy same package sizes every week - no need to re-enter
- **Compact mobile layout**: 3 input fields in one row, minimal padding
- **No scrolling needed**: See many ingredients on one screen
- **Touch-friendly**: Input sizes optimized for finger tapping
- **Smart placeholders**: "NT$", "Qty", unit suggestions
- **History access**: Tap 📊 to see price trends for any ingredient
- **Auto-sync**: Updates lastKnownPrices, price history, and shopping list estimates
- **Includes quick add items**: All ingredients in one place

**Mobile optimization**:
- Ultra-compact cards (p-2 instead of p-4)
- Horizontal input layout (3 fields side-by-side)
- Small text sizes (text-sm, text-xs)
- Minimal labels (placeholders only)
- One-line last price display
- Icon-only history button (📊)

**Perfect for**:
- Weekly price-checking trips before big shopping
- Comparing prices across multiple vendors
- Updating seasonal ingredient costs
- Building accurate shopping budgets

---

### 32. Shopping Trip History

**What it does**: Records every shopping trip with total spent, vendor, date, and items purchased. Provides monthly expense tracking and historical data export.

**How to use**:
1. After purchasing items (checked off in shopping list), tap the green "💰 Quick Log" button
2. Enter the total amount spent (e.g., 297)
3. Select vendor (auto-suggested based on what you bought)
4. Confirm date (defaults to today)
5. Tap "Save Trip"
6. Items you just logged are tracked - next Quick Log only saves newly checked items

**Viewing history**:
- Tap blue "Trip History" button in navigation
- See monthly summary (trip count + total spent)
- Each trip shows: vendor, date, total, item count
- Tap "View items" to expand and see what you bought
- Delete trips with X button (with confirmation)

**Benefits**:
- Track total monthly grocery expenses
- See spending patterns by vendor
- Historical record for tax/accounting purposes
- Identify price changes over time
- Export data to spreadsheet apps

---

### 33. Quick Log for Multi-Stop Shopping Trips

**What it does**: Handles real-world market shopping where you visit multiple vendors in one trip. Each vendor stop can be logged separately without re-checking items.

**Multi-stop workflow**:
1. **Stop 1 - Big King**: Check palm sugar, terasi → Quick Log → Enter NT$108 → Save
2. **Stop 2 - Street Market Veggies**: Check tomatoes → Quick Log → Enter NT$124 → Save
3. **Stop 3 - Vietnamese Vendor**: Check fish sauce → Quick Log → Enter NT$85 → Save

**Smart tracking**:
- Items stay checked after logging (don't need to re-check)
- App remembers which items already saved to a trip
- Each Quick Log only saves NEW items since last log
- Shows: "2 new items to log (3 already logged previously)"
- Prevents duplicate items across vendor trips

**When finished shopping**:
- Tap "Reset" button to clear all checked items
- Clears both purchase checkmarks and logged-items tracker
- Ready for next shopping trip

**Perfect for**:
- Street markets with multiple specialty vendors
- Shopping trips across several stores
- Bundle purchases where you can't split prices
- Quick expense tracking without detailed price entry

---

### 34. Vendor Management and Auto-Suggestion

**What it does**: Manages your list of shopping locations and intelligently suggests which vendor based on what you're buying.

**Default vendors**:
- Street Market - Veggies
- Street Market - Vietnamese
- Street Market - Shallot
- Big King
- RT-Mart

**Auto-suggestion algorithm**:
When you click Quick Log, the app:
1. Looks at what items you've checked off
2. Analyzes your last 10 shopping trips
3. Finds which vendor you most frequently bought these items from
4. Pre-selects that vendor in the dropdown
5. You can change it if the suggestion is wrong

**Adding vendors**:
- **During Quick Log**: Select "+ Add New Vendor..." from dropdown → Type name → Press Enter
- **In Trip History**: Click "+ Add Vendor" button → Enter name
- **Bulk edit**: Click "✏️ Manage Vendors" → Opens modal with multi-line editor
  - See all vendors at once (12-row textarea)
  - Easy visual scanning and editing
  - Add, remove, or reorder vendors
  - One vendor per line format

**Benefits**:
- Faster logging (fewer clicks)
- Learns your shopping patterns
- Separate multiple vendors at same market
- Custom names for your regular stops

---

### 35. CSV Export for Accounting Integration

**What it does**: Exports all shopping trip data to a CSV file that can be imported into spreadsheet apps like Apple Numbers, Excel, or Google Sheets.

**How to use**:
1. Open "Trip History" view
2. Click "Export to CSV" button
3. File downloads: `shopping-trips-2025-12-04.csv`
4. Open in Apple Numbers (or Excel/Sheets)
5. Data includes: Date, Vendor, Total (TWD), Items, Item Count

**CSV format**:
```
Date,Vendor,Total (TWD),Items,Item Count
2025-12-04,Big King,108,"palm sugar; terasi",2
2025-12-04,Street Market - Veggies,124,"tomatoes",1
2025-12-03,RT-Mart,567,"flour; sugar; oil; eggs",4
```

**Integration with Apple Numbers**:
1. Open your existing P&L spreadsheet
2. Import the CSV file
3. Map columns to your expense categories
4. All trip data flows into your accounting

**Benefits**:
- Seamless integration with existing workflows
- No manual re-entry of shopping data
- Historical expense records preserved
- Easy sharing with accountants
- Format compatible with all major spreadsheet apps

**Perfect for**:
- Restaurant P&L tracking
- Monthly expense reports
- Tax preparation documentation
- Cost analysis and budgeting
- Sharing data with business partners

---

### 36. Always-Visible Action Buttons with Disabled States

**What it does**: Shopping list action buttons (Load Prices, Quick Log, Reset) are always visible for consistent UI layout. They use disabled states (grayed out) when not applicable instead of hiding/showing.

**Button behavior**:

**Load Prices (Blue 🔄)**
- **Disabled (gray bg-gray-300)**: No saved prices yet
- **Enabled (blue bg-blue-600)**: Have saved prices, can load them
- Loads last known prices for all ingredients

**Quick Log (Green 💰)**  
- **Disabled (gray bg-gray-300)**: No items checked off
- **Enabled (green bg-green-600)**: At least 1 item checked
- Opens trip logging modal

**Reset (Red 🔄)**
- **Disabled (gray bg-gray-300)**: No items checked off
- **Enabled (red bg-red-600)**: At least 1 item checked
- Unchecks all items and clears logged-items tracker

**Benefits**:
- **Consistent layout**: Buttons don't appear/disappear (no layout jumping)
- **Predictable positions**: Always in the same spot
- **Clear affordance**: Grayed out = not usable yet, colored = ready to use
- **Discoverable**: Users can see what actions exist before they're usable
- **Better mobile UX**: No shifting elements on narrow screens
- **Visual feedback**: Color change indicates when action becomes available

**Design pattern**:
```javascript
disabled={condition}
className={condition 
  ? 'bg-blue-600 text-white' // Enabled state
  : 'bg-gray-300 text-gray-500 cursor-not-allowed' // Disabled state
}
```

This pattern is superior to conditional rendering (`{condition && <button>}`) for frequently-used actions where users benefit from seeing what's available.

---

## Summary

This app combines 36 features into a simple, offline-capable shopping list tool designed specifically for restaurant batch cooking workflows. The key innovations are:

1. **Offline-first**: Works without internet after initial setup
2. **Location-based organization**: Groups shopping by purchase location for efficient multi-stop trips
3. **Smart cost calculator**: Calculate total only for items you plan to buy, hide items you already have
4. **Price analytics**: Track historical prices, visualize trends, identify seasonal patterns
5. **Consistent naming**: Autocomplete + automatic lowercase prevents aggregation errors
6. **Standardized units**: Dropdown ensures uniform unit naming across all recipes
7. **Price tracking**: Remembers prices across trips, shows estimates before shopping
8. **Mobile-optimized**: Built for iPhone use at the market with 44px touch targets
9. **Data portability**: Export/import for backup and cross-device sync
10. **Quick add flexibility**: Add one-off items without creating recipes
11. **Trip tracking**: Record multi-vendor shopping trips with expense totals
12. **Smart vendor suggestions**: Auto-suggests where to shop based on purchase history
13. **CSV export**: Integrates with Apple Numbers for P&L tracking
14. **Centralized price updates**: Update all ingredient prices in one dedicated view
15. **Always-visible actions**: Buttons show disabled states instead of hiding for consistent UX

Perfect for Coto Makassar's daily market shopping needs!
