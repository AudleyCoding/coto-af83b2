# Shopping List Aggregator - AI Coding Instructions

## Project Overview
**Purpose**: Standalone HTML file for iPhone home screen - a mobile shopping companion for batch recipe aggregation.  
**Design Philosophy**: Maximum simplicity while maintaining robustness for long shopping lists. No build tools, no deployment complexity, just open and use.

## Architecture & Key Patterns

### Single-File Structure (Critical - Do Not Split)
- **File**: `<!DOCTYPE html>.ts` - Despite `.ts` extension, this is a standalone HTML file with embedded JSX
- **Must remain single-file** - designed for iPhone home screen use (saved as bookmark/web clip)
- Uses React 18 production CDN + Babel standalone for JSX transformation
- Tailwind CSS via CDN for styling
- Zero build process - file works directly in any browser

### State Management (localStorage-based)
```javascript
// Recipes persist automatically via useEffect - survives browser/home screen closes
localStorage.setItem('restaurantRecipes', JSON.stringify(recipes))
// Initial load: localStorage → INITIAL_RECIPES fallback
// Works offline once page is loaded/cached
```

### Data Model
```javascript
Recipe: {
  id: number,
  name: string,
  yieldUnit: string,           // e.g., "batch", "g", "kg"
  ingredients: [
    {
      name: string,
      quantity: number | null,   // null = unmeasured ingredient
      unit: string
    }
  ]
}
```

### Component Hierarchy
1. `ShoppingAggregator` (main) - Recipe selection + shopping list display
2. `RecipeForm` - Add/edit recipe interface
3. Icon components (ShoppingCart, Plus, Minus, Edit, Trash, X, Settings, RefreshCw) - SVG wrappers

## Core Features & Implementation

### Recipe Batch Calculation
- `selectedRecipes` state: `{ [recipeId]: batchCount }`
- `aggregatedIngredients` memoized: multiplies each ingredient by batch count and aggregates by name
- Handles `null` quantities gracefully (displays "–" in UI)

### Shopping List State
- `purchasedItems` as `Set<string>` - ingredient names only
- Two sections: remaining items (unchecked) vs purchased items (checked, green background, strikethrough)
- Reset button clears all purchased state

### Recipe Management Views
Three view states controlled by boolean flags:
1. Main shopping list (`showManageRecipes=false, showRecipeForm=false`)
2. Manage recipes list (`showManageRecipes=true`)
3. Recipe form (`showRecipeForm=true`)

## Development Conventions

### Simplicity First
- **Resist feature creep** - every addition must justify itself against "keep it simple"
- **Mobile-first** - all UI must work on iPhone screen sizes
- **Touch-friendly** - buttons/checkboxes sized for fingers, not mouse clicks
- **No external dependencies** beyond CDNs - keeps file standalone

### File Extension Issue
**Known quirk**: File named `<!DOCTYPE html>.ts` for VS Code syntax highlighting
- Rename to `.html` if needed: `mv "<!DOCTYPE html>.ts" shopping-list.html`
- Can be served as-is via local server or cloud storage (Dropbox, iCloud, etc.)

### Component Pattern
- All components as function components with hooks
- Props destructured in function signature
- No TypeScript types (plain JSX via Babel)

### Styling Approach
- Tailwind utility classes only (no custom CSS)
- Color scheme: Blue primary (`blue-600`), red for delete, green for purchased
- Responsive: `md:` breakpoints for desktop, but mobile is primary target
- Touch targets: Minimum 44x44px for buttons/checkboxes (iOS guideline)
- Padding: `p-4 md:p-8` pattern - generous spacing for thumb navigation

### State Updates
- All state updates use functional form: `setState(prev => ...)`
- Number parsing: `parseInt(batches) || 0` with `Math.max(0, ...)` for safety
- Confirmations for destructive actions: `confirm('Are you sure...')`
- **Ingredient names**: Always converted to lowercase for consistency (`.toLowerCase()`)

## Common Tasks

### When Asked to Add Features
**FIRST: Question if it's necessary.** Ask:
- Does this simplify shopping or add complexity?
- Will it work on a small phone screen?
- Does it keep the file standalone?

### Adding a New Recipe Field
1. Update `INITIAL_RECIPES` constant with new field
2. Add to `RecipeForm` state and form inputs
3. Update `handleSubmit` to include in saved recipe object
4. **Keep form inputs large enough for mobile typing**
5. **Remember**: Ingredient names must be lowercase in `INITIAL_RECIPES`

### Adding New Icon Component
```javascript
const IconName = ({ className }) => (
  <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="..." />
  </svg>
);
```

### Modifying Aggregation Logic
Edit `aggregatedIngredients` useMemo - centralized calculation for all shopping list features

## Testing & Debugging

### Mobile Testing Workflow
1. **Desktop development**: Edit in VS Code, test in Chrome DevTools mobile view
2. **iOS testing**: 
   - Save file to iCloud Drive or host locally
   - Open in Safari on iPhone
   - Tap Share → Add to Home Screen
   - Test with actual finger taps (not mouse)
3. **localStorage persistence**: Close/reopen home screen app to verify data survives

### Local Development
- Open file directly in browser (no build step required)
- Python simple server: `python3 -m http.server 8000`
- VS Code Live Server extension works perfectly
- Use browser DevTools React extension for component inspection

### Common Issues
- **Babel transformation errors**: Check JSX syntax in `<script type="text/babel">`
- **State not persisting**: Verify `localStorage.setItem` in useEffect dependencies
- **Calculation errors**: Check `aggregatedIngredients` memo and null quantity handling

## Key Files & Sections

- **Lines 18-77**: Recipe data structure (`INITIAL_RECIPES`)
- **Lines 82-114**: Icon components
- **Lines 116-353**: Main `ShoppingAggregator` component
- **Lines 211-232**: Aggregation logic (core business logic)
- **Lines 560-705**: `RecipeForm` component

## Restaurant-Specific Context
- Indonesian recipes (Ayam Goreng, Bumbu Coto, Ayam Bakar)
- Batch-based scaling for commercial kitchen operations
- Mix of measured (weight/volume) and unmeasured ingredients
- **Ingredient names are automatically converted to lowercase** - enforced throughout the app for consistent aggregation
- **Real-world use**: User takes phone to market, checks off items while shopping

## Design Constraints (DO NOT VIOLATE)

1. **Single-file requirement** - Never suggest splitting into multiple files
2. **No build process** - Must work by opening HTML directly
3. **Mobile-first** - If it doesn't work on iPhone, it's broken
4. **Simplicity over features** - When in doubt, don't add it
5. **Offline-capable** - localStorage only, no external APIs/databases

## Completed Features

### Core Features (All Implemented ✅)
1. **Search/Filter Recipes** ✅
   - Search bar appears when 4+ recipes exist
   - Filters by recipe name in real-time
   - Shows "No recipes match" message when needed
   
2. **Notes Field** ✅
   - Optional `notes` field per recipe
   - Text area in RecipeForm for adding notes
   - Displays in italic gray text below ingredient count
   
3. **Favorite/Frequent Recipes** ✅
   - `isFavorite: boolean` field in recipe data
   - Star icon button (yellow when favorited)
   - Auto-sorts: favorites first, then alphabetical
   - Click star to toggle favorite status
   
4. **Duplicate Recipe Function** ✅
   - Green copy button in manage recipes view
   - Copies all recipe data including ingredients
   - Appends " (Copy)" to name, resets favorite status
   - Opens RecipeForm pre-filled with copied data
   
5. **Ingredient Substitutions** ✅
   - Optional `substitution` field per ingredient
   - Two-row layout in form: main info + substitution
   - Placeholder: "or use fresh galangal instead"
   
6. **Unit Price Cost Tracking** ✅
   - Session-based pricing (not saved to recipes)
   - Unit price format: `NT$ [price] / [qty] [unit]`
   - Example: `NT$ 50 / 600 g` = 50 NT$ per 600 grams
   - Auto-calculates total: (ingredient_qty / unit_qty) × unit_price
   - Three inputs per ingredient: price, unit quantity, unit type
   - Shows calculated total: `= NT$ [amount]`
   - Displays "Estimated Total" at bottom (zh-TW formatting)
   - Prices stored in `ingredientPrices` state object
   
7. **Dark Mode** ✅
   - Moon/Sun toggle button in header
   - Persists preference in localStorage
   - Dark gray backgrounds (bg-gray-900/800)
   - Yellow sun icon in dark mode

8. **Export/Import Recipes** ✅
   - Export: Downloads `recipes-backup-YYYY-MM-DD.json`
   - **Includes price history**: Exports both recipes and lastKnownPrices
   - Import (Merge): Adds recipes and merges price history to existing
   - Replace All: Overwrites all recipes and price history with imported file
   - JSON format v1.1: `{version, exportDate, recipes, lastKnownPrices}`
   - File validation and error handling
   - Success/error messages with recipe and price counts
   - Use case: Sync data between iPad, iPhone, Mac

9. **iOS Home Screen Optimization** ✅
   - Custom app icon (shopping cart emoji on blue)
   - Full-screen web app mode (no Safari UI)
   - App title: "Shopping List"
   - Black translucent status bar
   - Theme color for mobile browsers

10. **Price History & Tracking** ✅
   - **Last Known Prices**: Auto-saves prices with date as you enter them
   - **Price Memory**: `lastKnownPrices` state persists in localStorage
   - **Load Prices Button**: Fills all price fields from last shopping trip
   - **Price Change Indicators**: Shows ↑/↓ with percentage when price changes
   - **Estimated Total**: Displays at top of shopping list before entering prices
   - **Auto-save**: 2-second debounce when entering prices
   - **Display**: Shows last price/date below each ingredient
   - **Export/Import**: Price history included in JSON backups
   - Use case: Know how much cash to bring before shopping

11. **Collapsible Price Inputs** ✅
   - **Hidden by Default**: Price input fields collapsed for cleaner shopping view
   - **$ Toggle Button**: Click to show/hide price entry fields
   - **Mobile-Optimized**: Easier to read list while shopping without clutter
   - **Quick Access**: Toggle on when prices change, off for scanning items
   - Yellow highlight when price inputs are visible
   
12. **Shopping List Export/Share** ✅
   - **Copy to Clipboard**: One-click export to clipboard
   - **Text Format**: Clean, readable format with checkboxes
   - **Grouped by Location**: Organizes items by vendor/location
   - **Checkbox Status**: Shows ✅ for purchased, ☐ for remaining
   - **Share Anywhere**: Paste into LINE, Notes, WhatsApp, messaging apps
   - **Date Stamp**: Includes export date in output
   - Use case: Share list with family or staff members

13. **Complete Shopping Trip** ✅
   - **Reset Button**: Clear all items after shopping
   - **Deselect Recipes**: Removes all recipe selections
   - **Clear Prices**: Resets session price inputs
   - **Keep Quick Add**: Preserves Quick Add items for next trip
   - **Confirmation Dialog**: Prevents accidental resets
   - Use case: Start fresh for next shopping trip

14. **Select All Recipes** ✅
   - **Bulk Selection**: One-click to select all recipes
   - **Default Batches**: Sets all recipes to 1 batch
   - **Time Saver**: Useful for weekly meal prep shopping
   - Button appears in Recipe Selection panel header

### Data Structure
```javascript
Recipe: {
  id: number,
  name: string,
  yieldUnit: string,
  notes: string,              // "500g equals 30 pieces"
  isFavorite: boolean,         // Star status
  ingredients: [
    {
      name: string,
      quantity: number | null,
      unit: string,
      substitution: string,    // "or use fresh galangal"
      price: number | null     // NOT USED - prices now session-based
    }
  ]
}

// Session-based pricing (separate from recipe data)
ingredientPrices: {
  [ingredientName]: {
    price: number,            // Unit price in NT$
    unitQty: number | '',     // Quantity at that price (e.g., 600)
    unitType: string          // Unit type (e.g., "g", "bunch", "pcs")
  }
}

// Price history (persists in localStorage)
lastKnownPrices: {
  [ingredientName]: {
    price: number,            // Last known unit price in NT$
    unitQty: number | '',     // Last known quantity (e.g., 600)
    unitType: string,         // Last known unit (e.g., "g", "bunch")
    date: string              // ISO date string (YYYY-MM-DD)
  }
}

// Export format (v1.1)
{
  version: "1.1",
  exportDate: "2025-01-15T10:30:00.000Z",
  recipes: Recipe[],
  lastKnownPrices: lastKnownPrices
}
```

### Price Calculation Logic
- User enters: `NT$ 50 / 600 g`
- If recipe needs 1200g: cost = (1200 / 600) × 50 = NT$ 100
- Empty unitQty defaults to 1 in calculations (not in state)
- Handles empty/deleted values without forcing "1" to appear

### Price History Flow
1. **Entry**: User enters price in shopping list
2. **Auto-save**: Debounced 2 seconds, then saves to `lastKnownPrices`
3. **Persistence**: `lastKnownPrices` → localStorage
4. **Display**: Shows "Last: NT$50/600g (2025-01-15)" below ingredient
5. **Load**: "Load Prices" button copies `lastKnownPrices` → `ingredientPrices`
6. **Compare**: Shows ↑15% (red) or ↓10% (green) when current ≠ last
7. **Estimate**: Calculates total from `lastKnownPrices` at top of list
8. **Export/Import**: Price history included in JSON v1.1 format

## AI Model Configuration

When working on this project, prioritize:
- Mobile UX patterns over desktop conventions
- Code simplicity over architectural "best practices"
- Practical shopping workflows over comprehensive feature sets
