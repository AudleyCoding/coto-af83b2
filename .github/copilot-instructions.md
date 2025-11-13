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
- Ingredient names are case-sensitive for aggregation
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
   
6. **Cost Tracking** ✅
   - Optional `price` field per ingredient (NT$)
   - Calculates: price × quantity × batches
   - Shows individual costs under each item
   - Displays "Estimated Total" at bottom (NT$ with zh-TW formatting)
   
7. **Dark Mode** ✅
   - Moon/Sun toggle button in header
   - Persists preference in localStorage
   - Dark gray backgrounds (bg-gray-900/800)
   - Yellow sun icon in dark mode

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
      price: number | null     // Cost in NT$
    }
  ]
}
```

## AI Model Configuration

When working on this project, prioritize:
- Mobile UX patterns over desktop conventions
- Code simplicity over architectural "best practices"
- Practical shopping workflows over comprehensive feature sets
