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
37. Enhanced Button Tooltips with Detailed Descriptions
38. Comprehensive Help Modal with Button Guide
39. Enhanced Ingredient Visibility in Dark Mode
40. Alphabetically Sorted Ingredients in Edit Recipe
41. Expandable Recipe View in Shopping List
42. Vendor Syncing Between Recipes and Trips
43. Automatic Price Loading (No Button Needed!)
44. Contextual Help Button in Shopping List
45. Smart Ingredient Search in Edit Recipe
46. Smart Ingredient Search in Price Management
47. Intelligent Search Filtering (Starts-With Prioritization)
48. iPhone Scroll Stability Fix
49. Context-Aware Vendor Suggestion
50. Price History Search and Filtering
51. Price History Sort Options (Newest/Alphabetical)
52. Edit Price History Entries
53. Delete Price History Entries
54. Manual Price Entry Addition
55. Quick Log Flat Price Calculation
56. Quick Add Item Support in Quick Log
57. Recipe Scaling with Decimal Batches
58. Whole Package Cost Calculation
59. Unit Price-Based Price History
60. Auto-Remove Quick Add Items When Checked
61. Scroll-to-Top Buttons on All Major Views
62. Removed Items Restoration
63. Edit Shopping Trips

---

### 37. Enhanced Button Tooltips with Detailed Descriptions
**What it does**: Every button in the app now has a helpful tooltip that appears on hover, explaining exactly what the button does and when to use it.

**How to use**:
- Hover over any button to see its tooltip
- Tooltips include emoji icons for visual recognition
- Each tooltip explains:
  - What the button does
  - When to use it
  - What happens when you click it
- Examples:
  - **Load Prices**: "📊 Auto-fill prices from your last shopping trip..."
  - **Update Prices**: "💲 Enter/edit prices for ingredients..."
  - **Quick Log**: "💰 Save checked items as a shopping trip..."

---

### 38. Comprehensive Help Modal with Button Guide
**What it does**: A dedicated help system accessible via the Help (?) button that provides a complete reference guide for all buttons and features.

**How to use**:
- Click the **Help (?)** button in the main navigation (blue icon with question mark)
- Browse organized sections:
  - **Main Navigation Buttons**: All header buttons explained with color-coded examples
  - **Shopping List Action Buttons**: Load Prices, Quick Log, Reset with before/after context
  - **Common Questions**: Answers to frequent confusion points
- Each button explanation includes:
  - Icon and color for visual reference
  - Clear description of function
  - Real-world usage examples
  - When to use it in your workflow
- Special FAQ section answers:
  - "What's the difference between Update Prices and Load Prices?"
  - "When should I use Quick Log?"
  - "What does Reset do exactly?"
- Click "Got it!" or anywhere outside to close

**Key clarifications in Help**:
- **Update Prices**: Save NEW prices after shopping (permanent storage)
- **Load Prices**: Fill shopping list with OLD prices for estimation (temporary)
- Real examples: "Enter total NT$297, click Quick Log, done!"

---

### 39. Enhanced Ingredient Visibility in Dark Mode
**What it does**: Ingredient name fields in Edit Recipe now have distinctive blue backgrounds and bolder, larger text for better visibility and easier differentiation from vendor/substitution fields.

**How to use**:
- When editing or adding recipes, ingredient name fields now stand out with:
  - **Dark Mode**: Deep blue background (bg-blue-900), bright blue text (text-blue-100)
  - **Light Mode**: Light blue background (bg-blue-50), dark blue text (text-blue-900)
  - **Bold, larger text**: font-bold text-lg for prominence
- Makes it easier to:
  - Quickly scan and identify ingredient names
  - Distinguish ingredients from metadata (vendor, substitution)
  - Edit recipes in low-light conditions (at restaurant/market)

---

### 40. Alphabetically Sorted Ingredients in Edit Recipe
**What it does**: When viewing or editing a recipe, ingredients are automatically sorted alphabetically by name for easier scanning and organization.

**How to use**:
- Ingredients automatically sort when you:
  - Save a new recipe
  - Update an existing recipe
  - Duplicate a recipe
- Benefits:
  - Find specific ingredients faster
  - Identify duplicates easily
  - More professional recipe organization
  - Consistent across all recipes

---

### 41. Expandable Recipe View in Shopping List
**What it does**: In the shopping list, when a recipe has many ingredients, they're initially collapsed with "and X more..." text. Click to expand and see all ingredients.

**How to use**:
- Long recipes show first few ingredients
- Click "and X more..." link to expand full ingredient list
- Helps keep shopping list compact and scannable
- Each recipe section can be expanded independently

---

### 42. Vendor Syncing Between Recipes and Trips
**What it does**: Vendor names in recipe locations automatically sync with the vendor list used in Quick Log and Trip History. Add vendors in one place, use everywhere.

**How to use**:
- Click **Vendors** button in main navigation (purple icon)
- Add, edit, or remove vendors from master list
- Vendors appear in:
  - Recipe ingredient location dropdown (Edit Recipe)
  - Quick Log vendor selection
  - Quick Add vendor grouping
- Changes sync automatically across all features
- Benefits:
  - Consistent vendor naming
  - No duplicate vendor names
  - Quick Add items automatically group by existing vendors
  - Easier expense tracking and reporting

---

### 43. Automatic Price Loading (No Button Needed!)
**What it does**: Prices from your last shopping trip automatically appear in the shopping list the moment you select recipes. No manual "Load Prices" button needed anymore!

**How it works**:
- Select any recipe → Prices instantly auto-fill
- Uses your saved price history (from Update Prices)
- Happens automatically in the background
- Shows estimated total cost immediately
- One less button to remember!

**Benefits**:
- **Faster workflow**: No extra clicking required
- **Always ready**: Estimated costs appear instantly
- **Less confusion**: No need to understand Load vs Update Prices
- **Better UX**: Prices are there when you need them

**Example**:
1. Check "Ayam Goreng" recipe
2. Prices auto-fill instantly (if you've bought these before)
3. See estimated total: "NT$ 450"
4. Go shopping!

---

### 44. Contextual Help Button in Shopping List
**What it does**: A dedicated Help button next to Quick Log and Reset that opens the Help modal and automatically scrolls to the relevant "Shopping List Action Buttons" section.

**How to use**:
- Look at the action buttons at the top of shopping list
- See the small **? (Help)** button next to Reset
- Click it → Help modal opens AND auto-scrolls to action buttons section
- No need to scroll through navigation button explanations
- Get help exactly where you need it

**Benefits**:
- **Contextual**: Help appears right where you're working
- **Smart scrolling**: Jumps to the relevant section automatically
- **Quick reference**: Reminds you what Quick Log and Reset do
- **Better discoverability**: Help is visible when you need it most

---

### 45. Smart Ingredient Search in Edit Recipe
**What it does**: When editing recipes with 6+ ingredients, a search field appears at the top allowing you to quickly filter and find specific ingredients.

**How to use**:
- Search field appears automatically when recipe has 6+ ingredients
- Type to filter ingredients in real-time
- Shows "Showing X of Y ingredients" count
- Ingredients that START with your search appear first
- Then ingredients that CONTAIN your search
- Clear search to see all ingredients again

**Example**:
- Recipe has 20 ingredients
- Type "g" → "garlic" and "ginger" appear first
- Then "turmeric" (contains 'g') appears after
- Type "garlic" → Shows only "garlic" and "garlic powder"

**Benefits**:
- Find ingredients instantly in large recipes
- Edit specific items without scrolling through entire list
- Smart sorting shows most relevant matches first

---

### 46. Smart Ingredient Search in Price Management
**What it does**: Search field in Update Prices view allows filtering through all your ingredients (great for lists with 50+ items!).

**How to use**:
- Open Update Prices view
- Use search field at top of page
- Type to filter ingredients in real-time
- Same smart filtering: starts-with matches appear first
- Shows count: "Showing X of Y ingredients"
- Search clears automatically when closing Price Management

**Example**:
- You have 51 ingredients in Price Management
- Type "on" → "onion" appears before "lemon"
- Type "garlic" → Shows "garlic" and "garlic powder" only
- Clear search to update all prices

**Benefits**:
- Navigate large ingredient lists quickly
- Update specific prices without scrolling
- Green focus ring matches Update Prices theme

---

### 47. Intelligent Search Filtering (Starts-With Prioritization)
**What it does**: Both Edit Recipe and Price Management searches use smart filtering that prioritizes ingredients starting with your search term.

**How it works**:
1. Type search term (case-insensitive)
2. Ingredients are filtered to those containing the term
3. Results are sorted:
   - First: Ingredients that START with search term (alphabetical)
   - Second: Ingredients that CONTAIN search term (alphabetical)
   - Last: Empty ingredient names (if any)

**Example scenarios**:
- Search "t":
  - First: "tamarind", "turmeric" (start with 't')
  - Then: "butter", "coconut milk" (contain 't')
- Search "garlic":
  - First: "garlic", "garlic powder" (start with 'garlic')
  - Then: (nothing else contains 'garlic')

**Benefits**:
- More intuitive search - finds what you're looking for faster
- Reduces scrolling to find the right ingredient
- Matches natural user expectations
- Works consistently across Edit Recipe and Price Management

---

### 48. iPhone Scroll Stability Fix
**What it does**: Prevents the screen from sliding/bouncing horizontally while scrolling vertically on iPhone/iPad.

**Technical implementation**:
- Viewport meta tag includes: `maximum-scale=1.0, user-scalable=no`
- Prevents pinch-to-zoom (not needed for this app)
- Eliminates horizontal scroll drift
- Provides stable, native app-like experience

**Benefits**:
- No more accidental horizontal sliding while scrolling shopping list
- Stable touch interactions
- Feels like a native iOS app
- Better usability at the market

---

### 49. Context-Aware Vendor Suggestion
**What it does**: When clicking Quick Log after shopping, the vendor field defaults to the location where you're currently shopping (based on ingredient locations), not your last trip.

**How it works**:
1. You check off items while shopping at a store
2. Click Quick Log button
3. Vendor field auto-fills with the most common location from checked items
4. If items have "PX Mart" as location → defaults to "PX Mart"

**Old behavior**: Defaulted to vendor from last shopping trip
**New behavior**: Defaults to location field of currently checked items

**Benefits**:
- One less field to change when logging trips
- Vendor matches WHERE you are, not where you WERE
- More intuitive workflow
- Faster trip logging

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

**Recent Updates (December 2025)**:
- ✅ Full price history storage in priceHistoryData
- ✅ **Save Prices button** in Update Prices view for manual saving
- ✅ Auto-save on checkout when checking off purchased items
- ✅ Proper duplicate detection (won't save same price twice on same day)
- ✅ Data format simplified to packageQuantity/packageUnit only
- ✅ Backward compatibility removed for cleaner codebase

**How to use**:
- **Save prices manually**: Go to "Update Prices" → enter prices → click "Save Prices" button
- **Save prices on checkout**: Check off items after purchase (if prices are filled in)
- **View history**: Tap "Price History" button in main header (trending up icon)
- View all ingredients with price data, sorted by most recent update
- See trend indicators: ↑ (>10% above average - red), ↓ (>10% below average - green), → (stable - gray)
- Tap any ingredient to view detailed price history
- **Detail view shows**:
  - Interactive line chart of last 12 months (powered by Chart.js)
  - Current price, 6-month average, min/max prices
  - Percentage change vs average
  - Full price history table (reverse chronological)
  - Min and max points highlighted on chart (green/red dots)

**Data Format**:
```javascript
{
  "bananas": [
    {
      "date": "2025-12-10",
      "price": 30,
      "packageQuantity": 600,
      "packageUnit": "g"
    }
  ]
}
```

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
- Price history is included in recipe exports (priceHistoryData field)
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

### 50. Price History Search and Filtering
**What it does**: Search for specific ingredients in the Price History view to quickly find the items you need.

**How to use**:
- In Price History view, use the search box at the top
- Type any part of an ingredient name (e.g., "tom" finds "tomato")
- Results filter in real-time as you type
- Clear the search to see all ingredients again

**Benefits**:
- Quickly find specific ingredients in long lists
- Check price trends for specific items
- No need to scroll through entire history

---

### 51. Price History Sort Options (Newest/Alphabetical)
**What it does**: Sort the Price History list either by most recently updated items or alphabetically by name.

**How to use**:
- Use the dropdown next to the search box
- Choose **"Sort: Newest First"** to see recently updated prices at top
- Choose **"Sort: A-Z"** to see ingredients alphabetically
- Default is Newest First to prioritize recent changes

**Benefits**:
- Newest First: See what you've updated recently
- A-Z: Find items by name more easily

---

### 52. Edit Price History Entries
**What it does**: Modify existing price entries if you made a mistake or need to correct historical data.

**How to use**:
1. Click on an ingredient in Price History
2. Find the entry you want to edit in the table
3. Click the **Edit** button
4. Modify any of the fields:
   - Date
   - Price
   - Package Quantity
   - Package Unit
5. Click **Save** or **Cancel**

**Benefits**:
- Fix typos or data entry errors
- Correct dates if entered wrong
- Update package sizes that changed

---

### 53. Delete Price History Entries
**What it does**: Remove incorrect or duplicate price entries from history.

**How to use**:
1. Click on an ingredient in Price History
2. Find the entry you want to remove
3. Click the **Delete** button
4. Confirm the deletion
5. If it's the last entry, the entire ingredient is removed from history

**Benefits**:
- Clean up mistakes or test data
- Remove duplicate entries
- Maintain accurate price history

---

### 54. Manual Price Entry Addition
**What it does**: Add historical price entries manually, allowing you to backdate prices or add entries from written notes.

**How to use**:
1. Click on an ingredient in Price History
2. Click the **Add Entry** button (top right of history table)
3. A form appears with fields pre-filled from the latest entry
4. Modify as needed:
   - **Date**: Change to backdate the entry
   - **Price**: Enter the price you paid
   - **Quantity**: Package size
   - **Unit**: Package unit (g, ml, kg, etc.)
5. Click **Save** or **Cancel**

**Use cases**:
- Restore prices lost during data migration
- Add prices from written shopping notes when you didn't have your phone
- Backdate entries to build historical data
- Correct gaps in price history

---

### 55. Quick Log Flat Price Calculation
**What it does**: Quick Log now uses flat package prices (what you paid at the store) instead of calculating proportional costs based on recipe quantities.

**How it works**:
- **Old behavior**: If you bought coconut water (500ml) with a 1000ml package price of $79, it calculated 500/1000 × $79 = $39.50
- **New behavior**: It shows $79 (the full package price you paid at the store)
- **Calculated Total** shows the sum of all package prices
- **Actual Total** field pre-fills with this calculated sum

**Why this matters**:
- Quick Log is for tracking what you spent at the store, not recipe costs
- You bought 3 items for $1007 total → that's what it should show
- Recipe cost calculations happen when viewing recipes, not when logging trips

**Benefits**:
- Accurate expense tracking
- Matches your receipt total
- Clear separation between "what I spent" vs "what the recipe costs"

---

### 56. Quick Add Item Support in Quick Log
**What it does**: Quick Add items (items added without recipes) now work correctly in Quick Log calculations.

**How it works**:
- Quick Add items only need a **price** (no package quantity/unit required)
- They're included in the Quick Log calculated total
- No "Incomplete" warning shown if only price is entered

**Example**:
- Add "underwear" as Quick Add item with price $529
- Enter prices for recipe items (coconut water $79, honey $399)
- Quick Log shows: $79 + $399 + $529 = **$1007**

**Benefits**:
- Flexible item tracking without creating recipes
- One-off purchases included in trip totals
- Cleaner interface (no false warnings)

---

### 57. Recipe Scaling with Decimal Batches
**What it does**: Allows you to make half recipes, 1.5x recipes, or any fractional batch size instead of only whole numbers.

**How it works**:
- Batch selector now accepts decimal values (0.5, 1.5, 2.5, etc.)
- Minimum batch size is 0.5 (half a recipe)
- Increment/decrement buttons adjust by 0.5
- Number input allows precise decimal entry
- All ingredient quantities scale proportionally

**How to use**:
1. Select a recipe in "Recipes" section
2. Use the **-** button to decrease by 0.5 batches
3. Use the **+** button to increase by 0.5 batches
4. Or type directly: `0.5`, `1.5`, `2.5`, etc.
5. Shopping list updates automatically with scaled quantities

**Examples**:
- **0.5 batches**: Testing a new recipe? Make half to avoid waste
- **1.5 batches**: Need more than 1 but less than 2? Perfect for medium demand
- **2.5 batches**: Weekend rush? Scale up precisely

**Benefits**:
- Flexible portion control for varying demand
- Reduce waste when testing new recipes
- Precise scaling for optimal ingredient usage
- No need to calculate fractions manually

---

### 58. Whole Package Cost Calculation
**What it does**: Shopping list costs now round UP to whole packages, reflecting what you actually have to buy at the store.

**The Problem**:
- Recipe needs 500ml coconut milk, package is 1000ml at NT$150
- Old calculation: 0.5 packages × $150 = **$75** ❌ (can't buy half a package!)
- New calculation: 1 package × $150 = **$150** ✅ (must buy full package)

**How it works**:
- Calculates packages needed: recipe quantity ÷ package quantity
- Rounds UP to next whole number using `Math.ceil()`
- Multiplies by package price
- Displays package count: "2 pkgs" instead of "1.73 units"

**Where it applies**:
- **Estimated Total** (top of shopping list): Sum of all items you plan to buy
- **Last Known Prices total**: Based on your most recent prices
- **Planned Purchase Cost**: What you'll actually spend
- **Individual item costs**: Shows per-item cost with package count

**Examples**:

| Scenario | Recipe Needs | Package Size | Package Price | Packages | Total Cost |
|----------|-------------|--------------|---------------|----------|------------|
| Coconut milk | 500ml | 1000ml | NT$150 | 1 pkg | NT$150 |
| Soy sauce | 250ml | 500ml | NT$80 | 1 pkg | NT$80 |
| Oyster sauce | 750ml | 500ml | NT$120 | 2 pkgs | NT$240 |
| Rice vinegar | 1.2L | 500ml | NT$60 | 3 pkgs | NT$180 |

**Benefits**:
- **Accurate budgeting**: See what you'll actually spend, not theoretical recipe cost
- **No surprises**: Estimated total matches your cart total
- **Clear package counts**: Know exactly how many bottles/cartons to grab
- **Prevents underestimation**: Especially important for expensive ingredients

**UI Improvements**:
- Clean package display: "2 pkgs" instead of decimal units
- Browser spinner arrows hidden (uses -/+ buttons only)
- Consistent rounding across all cost displays

---

### 59. Unit Price-Based Price History
**What it does**: Price History now tracks and displays **unit prices** instead of raw package prices, showing accurate price trends even when you buy different package sizes.

**The Problem (Before)**:
- Bought palm sugar: NT$39 for 6 pcs, NT$78 for 12 pcs, NT$195 for 30 pcs
- Chart showed: NT$39 → NT$78 → NT$195 (looks like 400% increase! 📈)
- Statistics: "Current: NT$195, Highest: NT$195, +87% vs average" 😱
- **Reality**: Unit price stayed constant at NT$6.5/pc (no increase!)

**The Solution (After)**:
- Chart shows: NT$6.5 → NT$6.5 → NT$6.5 (flat line = stable price! —)
- Statistics: "Current: NT$6.5/pc, vs Average: 0%" 😊
- **Truth revealed**: Price per piece hasn't changed

**How it works**:
1. **Calculates unit price**: `price ÷ packageQuantity`
2. **Plots unit price**: Chart Y-axis shows NT$/unit (not raw price)
3. **Statistics use unit prices**: Min/max/average all based on cost per unit
4. **Comparison across sizes**: Fairly compares 6-pack vs 30-pack purchases

**Where you see unit prices**:

1. **Update Prices Modal** (already had this):
   - Real-time unit price as you type
   - "NT$195 for 30 pcs = **NT$6.5 per pc**"

2. **Price History Statistics**:
   - **Current Unit Price**: NT$6.5/pc (not NT$195)
   - **6-Month Average**: NT$6.5/pc
   - **Lowest**: NT$6.0/pc (best deal you've found)
   - **Highest**: NT$7.0/pc (most expensive)
   - **vs Average**: Shows if current unit price is higher/lower

3. **Price History Chart**:
   - Y-axis: "Unit Price (NT$ per [unit])"
   - Plots cost per piece/gram/liter over time
   - Shows TRUE price trends (not package size changes)

4. **Price History Table**:
   - New **"Unit Price"** column added
   - Example row:
     * Date: December 13, 2025
     * Price: NT$195
     * Package: 30 pcs
     * **Unit Price: NT$6.5/pc** ← NEW!
     * Actions: Edit | Delete
   - Unit price shown in green for easy scanning
   - Edit mode shows calculated unit price too

**Real-world examples**:

| Ingredient | Purchase 1 | Purchase 2 | Purchase 3 | Unit Price Trend |
|------------|-----------|-----------|-----------|------------------|
| Palm sugar | NT$39/6pcs | NT$78/12pcs | NT$195/30pcs | NT$6.5 (stable) |
| Coconut milk | NT$75/1L | NT$150/2L | NT$360/5L | NT$75, NT$75, NT$72 (↓ bulk discount!) |
| Fish sauce | NT$80/500ml | NT$90/500ml | NT$95/500ml | NT$0.16, NT$0.18, NT$0.19 (↑ inflation!) |
| Beef powder | NT$200/1kg | NT$100/500g | NT$400/2kg | NT$0.20 (stable) |

**Benefits**:
- **Accurate trends**: See real price changes, not package size changes
- **Fair comparisons**: Compare 6-pack vs 30-pack fairly
- **Bulk discount visibility**: Spot when buying larger packages saves money per unit
- **Inflation tracking**: Detect when suppliers raise prices per unit
- **Better decisions**: Know if you're paying more or less per actual unit
- **No false alarms**: Don't panic when the chart shows "increases" that are just larger purchases

**Technical details**:
- All calculations use: `unitPrice = price / packageQuantity`
- Chart plots unit prices chronologically
- Statistics (min/max/avg) calculated from unit prices
- Table shows both raw price AND unit price for complete context
- Non-breaking change: Works with all existing price history data
- Update Prices modal already had this (now consistent everywhere)

**Use cases**:
1. **Bulk buying analysis**: "Is the 30-pack actually cheaper per piece?"
2. **Vendor comparison**: "Big King charges NT$6.5/pc, Carrefour charges NT$7/pc"
3. **Seasonal pricing**: "Limes cost NT$30/kg in summer, NT$50/kg in winter"
4. **Inflation monitoring**: "Cooking oil went from NT$150/L to NT$180/L over 6 months"
5. **Package size changes**: "Supplier switched from 1kg to 900g bags—am I paying more per gram?"

---

### 60. Auto-Remove Quick Add Items When Checked
**What it does**: Quick Add items automatically disappear from the Quick Add panel when you check them off as purchased, keeping your shopping list clean and organized.

**The Problem (Before)**:
- Added "garlic paste 300g" via Quick Add
- Item appeared in shopping list ✓
- Checked it off as purchased ✓
- Item stayed in Quick Add panel ✗
- Had to manually remove it with X button
- Quick Add panel got cluttered with purchased items

**The Solution (After)**:
- Add "garlic paste 300g" via Quick Add
- Item appears in shopping list
- Check it off as purchased → **automatically removed from Quick Add panel**
- Quick Add stays clean and shows only items you haven't bought yet

**How it works**:
1. Add item via Quick Add (appears in both Quick Add panel and shopping list)
2. Check off item in shopping list
3. Item moves to Purchased section
4. Item automatically removed from Quick Add items array
5. Quick Add panel updates instantly

**Benefits**:
- **Cleaner interface**: No need to manually clean up Quick Add items
- **Less confusion**: Purchased items don't clutter the Quick Add panel
- **Faster workflow**: One action (checking off) handles both marking as purchased and cleanup
- **Automatic maintenance**: Shopping list stays organized without extra steps

**Technical details**:
- Triggered in `togglePurchased()` function when checking item
- Filters Quick Add items array to remove checked item
- Only affects Quick Add items (recipe items unaffected)
- Maintains price history for removed Quick Add items

---

### 61. Scroll-to-Top Buttons on All Major Views
**What it does**: Every major view (Recipes, Shopping List, Price History detail, Trips) now has a floating scroll-to-top button that appears when you scroll down, making it easy to return to the top on long lists.

**The Problem (Before)**:
- Long shopping lists required tedious scrolling back to top
- Price History details with many entries hard to navigate
- Recipe lists became difficult to scan from bottom
- No quick way to return to filters/controls at top

**The Solution (After)**:
- Scroll down on any major view
- Blue circular button appears in bottom-right corner
- Click button → instantly scroll to top
- Button auto-hides when near top of page

**Where it appears**:
1. **Shopping List**: Navigate back to Planned Purchase summary and action buttons
2. **Recipes View**: Return to search bar and filters
3. **Price History Detail**: Jump back to statistics and chart
4. **Trips View**: Access vendor filters and summary quickly

**How it works**:
- Button appears when scrolled >300px down
- Smooth scroll animation to top
- Fixed position (stays visible while scrolling)
- Blue color matches app theme
- Up arrow icon for clear meaning

**Benefits**:
- **Faster navigation**: One click vs many swipes
- **Better UX on long lists**: Especially helpful with 20+ items
- **Consistent behavior**: Same button style/position across all views
- **Mobile-friendly**: Large 48px touch target
- **Non-intrusive**: Only shows when needed (auto-hides near top)

---

### 62. Removed Items Restoration
**What it does**: Items accidentally removed from your shopping list now appear in a dedicated "Removed Items" section where you can easily restore them with one click, preventing lost items and shopping mistakes.

**The Problem (Before)**:
- Accidentally clicked bag icon to remove item
- Item disappeared from shopping list completely
- No way to restore it without re-selecting recipe or re-adding via Quick Add
- Could forget needed items at the market
- Risk of buying incomplete ingredients

**The Solution (After)**:
- Click bag icon to remove item → moves to "Removed Items" section
- Section appears below shopping list with count
- Click any removed item → instantly restored to shopping list
- Section auto-hides when empty (no clutter)

**How it works**:

1. **Removing items**:
   - Click gray bag icon next to any ingredient
   - Item removed from planned purchases
   - Appears in "Removed Items (1)" section below list

2. **Restoring items**:
   - Click removed item in the section
   - Item immediately added back to shopping list
   - Bag icon turns blue again
   - Can be checked off or removed again

3. **Smart filtering**:
   - Only shows items NOT in shopping list AND NOT purchased
   - Purchased items never appear here (they're in Purchased section)
   - Automatically updated when items restored

**Visual design**:
- 🗑️ Trash icon with item count: "Removed Items (3)"
- Gray background to distinguish from active list
- "Click to restore" hint for clarity
- ↩️ Arrow icon on each item
- Shows ingredient name and quantity
- Hover effect for clear interactivity

**Example workflow**:
1. Shopping list shows: shallot paste, turmeric powder, palm sugar
2. Accidentally click bag on turmeric powder (oops!)
3. Turmeric disappears from list
4. "Removed Items (1)" section appears below
5. See "↩️ turmeric powder (15 g)"
6. Click it → back in shopping list instantly
7. No items removed → section hides automatically

**Benefits**:
- **Undo functionality**: Fix accidental removals instantly
- **Safety net**: Never lose items from your list
- **Visible feedback**: Clear section shows what's been removed
- **One-click restore**: Faster than re-adding manually
- **Smart filtering**: Only shows truly removed items (not purchased)
- **Auto-cleanup**: Section disappears when empty
- **Peace of mind**: Shop confidently knowing you can undo mistakes

**Edge cases handled**:
- Removed items stay removed when checking off other items
- Checking off item doesn't move it to Removed Items (goes to Purchased)
- Unchecking purchased item adds back to shopping list (not Removed Items)
- Deselecting recipe removes items completely (not to Removed Items)
- New recipe items auto-add to shopping list (don't trigger removals)

**Technical details**:
- Filters `aggregatedIngredients` for items NOT in `planToBuyItems` AND NOT in `purchasedItems`
- Uses existing `togglePlanToBuy()` function for restoration
- Conditional rendering: only shows when `removedItems.length > 0`
- Tracks previous ingredient list to prevent auto-restoration of explicitly removed items
- Works with both recipe items and Quick Add items

---

### 63. Edit Shopping Trips
**What it does**: Made a mistake entering trip information? You can now edit the vendor, total amount, and date for any shopping trip directly in Trip History, or delete and re-log items without errors.

**The Problem (Before)**:
- Entered wrong total in Quick Log (typo, wrong calculation)
- Trip saved with incorrect amount
- No way to fix it - only Delete button
- If deleted trip, couldn't re-log same items
- Got "already logged" error when trying to re-log
- Had to manually track corrections outside the app

**The Solution (After)**:
- **Edit button** on every trip
- Click Edit → modify vendor, total, or date
- Save changes instantly
- OR delete trip → items unmarked → can re-log correctly

**How it works:**

**Option A - Edit in place:**
1. Go to Trip History
2. Find trip with incorrect information
3. Click ✏️ Edit button
4. Modify:
   - **Vendor** (dropdown with all your vendors)
   - **Total** (NT$ amount - fix typos)
   - **Date** (if logged wrong day)
5. Click **Save** or **Cancel**

**Option B - Delete and re-log:**
1. Delete the incorrect trip
2. Items automatically unmarked as "logged"
3. Return to Shopping List
4. Items still checked off (in Purchased section)
5. Click Quick Log again
6. Enter correct information
7. **No more "already logged" error!**

**Real-world scenarios:**

| Problem | Solution |
|---------|----------|
| Entered NT$297 instead of NT$279 | Edit trip → change total to 279 → Save |
| Logged to wrong vendor | Edit trip → select correct vendor → Save |
| Forgot to log yesterday's trip | Edit trip → change date to yesterday → Save |
| Total completely wrong | Delete trip → Re-log with correct amount |
| Accidentally logged twice | Delete duplicate trip → Items can be re-logged |

**Visual design:**
- **Edit mode**: Shows three input fields (Vendor dropdown, Total input, Date picker)
- **Save button**: Green, confirms changes
- **Cancel button**: Gray, discards changes
- **Edit icon**: Blue pencil next to Delete (X) button
- **Inline editing**: No modal - edit directly in trip card

**Benefits:**
- **Fix typos instantly**: No need to delete and re-create
- **Correct mistakes**: Update wrong vendor or date
- **No data loss**: Edit preserves trip items and history
- **Re-logging works**: Deleted items can be logged again
- **Accounting accuracy**: Keep your expense records correct
- **Time-saver**: Edit in place vs. delete + re-enter all items

**Technical details:**
- Edit updates: `vendor`, `total`, and `date` fields
- Items list preserved during edit (not editable)
- Delete now clears `loggedItems` status for trip's items
- Prevents "already logged" error on re-logging
- Edit state stored in `editingTrip` with trip ID
- Changes saved to `shoppingTrips` array in localStorage

**Edge cases handled:**
- Can't edit while another trip is being edited (one at a time)
- Cancel restores original values
- Delete asks for confirmation
- Re-logging after delete works immediately
- Edit doesn't affect other trips' data

**Workflow example:**
```
Morning: Quick Log NT$350 at Big King
Afternoon: Check receipt - actually NT$380! 
Solution: Trip History → Edit → Change 350 to 380 → Save ✓

OR

Morning: Quick Log NT$500 at wrong vendor
Afternoon: Need to fix for accounting
Solution: Delete trip → Items unmarked → Quick Log again with correct vendor ✓
```

---

## Summary

This app combines 63 features into a simple, offline-capable shopping list tool designed specifically for restaurant batch cooking workflows. The key innovations are:

1. **Offline-first**: Works without internet after initial setup
2. **Location-based organization**: Groups shopping by purchase location for efficient multi-stop trips
3. **Smart cost calculator**: Calculate total only for items you plan to buy, hide items you already have
4. **Price analytics**: Track historical prices, visualize trends, identify seasonal patterns, search and edit history
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
16. **Comprehensive price history management**: Search, sort, edit, delete, and manually add price entries
17. **Accurate expense tracking**: Quick Log uses flat prices to match your actual spending
18. **Decimal recipe scaling**: Make 0.5x, 1.5x, or any fractional batch size for flexible portioning
19. **Whole package costing**: Rounds up to actual packages you must buy for accurate budgeting
20. **Unit price tracking**: Charts show cost per unit (not package price) for accurate trend analysis
21. **Auto-cleanup Quick Add**: Checked items automatically removed from Quick Add panel
22. **Easy navigation**: Scroll-to-top buttons on all major views for long lists
23. **Mistake prevention**: Removed Items section lets you restore accidentally removed ingredients
24. **Trip editing**: Edit or correct shopping trip details after logging

Perfect for Coto Makassar's daily market shopping needs!
