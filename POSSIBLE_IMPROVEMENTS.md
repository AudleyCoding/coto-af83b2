# Shopping List App - Possible Future Improvements

This document tracks potential features and enhancements for future development, organized by priority.

---

## High Priority (High Impact, Relatively Easy)

### 1. Bulk Price Update from Last Shopping Trip
Currently there's a "Load Prices" button, but you could enhance it:
- Add a "Load Package Sizes" button that fills in package quantities/units from last time
- Useful when you buy from same vendors with consistent package sizes
- Saves time vs re-entering "400g" every week

### 2. Quick Add Common Ingredients
- Dropdown or autocomplete to add ingredients directly to shopping list (without creating a recipe)
- Useful for one-off items: "Need to grab salt, forgot to add to recipe"
- **Very good idea!**
- Could have a "Quick Items" section

### 3. Shopping Trip History/Log
- Save snapshots of completed shopping trips with date and total cost
- View history: "Nov 15: NT$2,450 (25 items)"
- Track spending trends over weeks/months
- Export shopping logs to CSV for accounting

### 4. Vendor/Market Field per Ingredient
- Add optional "Vendor" field to price entry
- Track which market/store had each price
- Helps remember: "Big King had cheapest coconut milk last time"
- Could group shopping list by vendor instead of just location

---

## Medium Priority (Nice to Have)
**Might be good**

### 5. Recipe Categories/Tags
- Tag recipes: "Breakfast", "Lunch Special", "Vegetarian", "Spicy"
- Filter recipes by category when selecting
- Helps organize large recipe collections
- **Maybe later**

### 6. Ingredient Photo Upload
- Optional photo attachment for ingredients
- Helps identify exact products at market
- Visual reference: "This brand, this packaging"
- **I don't want to clutter the UI, but a separate "Photo Reference" page might be good**

### 7. Seasonal Price Alerts
- Based on price history, notify when ingredient is at seasonal low
- "Ginger is 15% below average - good time to buy extra!"
- Helps with strategic purchasing
- **Could be good in a later update**

### 8. Recipe Yield Scaling
- Currently scales by batches (1x, 2x, 3x)
- Add custom yield: "Recipe serves 10, but I need to serve 35"
- Auto-calculate: 35÷10 = 3.5 batches
- **This might be very helpful, but I'm not sure now**

### 9. Multi-Currency Support
- Add currency selector (NT$, USD, EUR, etc.)
- Useful if traveling or comparing international prices
- Store currency with price history
- **Not necessary for my personal use now, but maybe in the future**

### 10. Smart Shopping Route Optimization
- Based on location categorization, suggest optimal route
- "Start at Street Market, then Supermarket, end at Big King"
- Could integrate with map apps
- **This is definitely a far in the future addition**

---

## Lower Priority (Nice but Complex)

### 11. Shared Shopping Lists
- Multiple devices sync in real-time
- Useful if multiple staff members shop
- Would require backend/cloud service
- **Not needed for my personal use, but could be useful in the far future**

### 12. Barcode Scanner Integration
- Scan product barcodes to track exact items
- Auto-fill product names and package sizes
- Requires camera API access
- **This wouldn't help at the market, but could be handy when shopping at stores**

### 13. Budget Planning
- Set weekly/monthly budget
- Track spending vs budget
- Alerts when approaching limit
- **Maybe in the future, but not really necessary for my use case**

### 14. Ingredient Substitution Suggestions
- When checking off purchased items, suggest alternatives
- "Couldn't find X? Try Y instead"
- Based on your previous substitutions

### 15. Recipe Costing
- Show cost per serving for each recipe
- Helps with menu pricing decisions
- "Coto Makassar costs NT$45 per bowl to make"
- **Maybe in the future if I turn this into a full featured restaurant app**

---

## Top 3 Recommended Next Features

Based on effort vs value analysis:

1. **Shopping Trip History** - Low effort, high value for tracking spending
2. **Vendor Field** - Simple addition, very practical for price comparison
3. **Bulk Package Size Loading** - Saves repetitive data entry

---

*Last updated: December 10, 2025*

## Completed Features (December 2025)

### ✅ Price History Tracking (Dec 9-10, 2025)
- Full price history storage in priceHistoryData
- Save Prices button in Update Prices view
- Auto-save on checkout flow
- Price history visualization with dates
- Proper duplicate detection

### ✅ Code Cleanup (Dec 10, 2025)
- Removed migration code
- Simplified data format to packageQuantity/packageUnit only
- Eliminated backward compatibility fallbacks
- Reduced codebase by ~52 lines

