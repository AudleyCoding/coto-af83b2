# Weekend Testing Checklist - Shopping List Aggregator
**Test Date:** This Weekend  
**Location:** Taiwan Street Markets + Supermarket  
**Device:** iPhone  
**Goal:** Validate real-world workflow vs current Siri method

---

## Pre-Market Setup (Friday Evening)

### PWA Installation
- [ ] Open https://audleycoding.github.io/coto-af83b2/shopping-af83b2.html on iPhone
- [ ] Tap Share → Add to Home Screen
- [ ] Name it "Shopping" or "Coto Shopping"
- [ ] Verify icon appears on home screen

### Offline Test
- [ ] Enable Airplane Mode
- [ ] Open app from home screen
- [ ] Verify app loads (should work offline)
- [ ] Disable Airplane Mode

### Recipe Selection
- [ ] Select 3-4 recipes you're actually cooking this weekend
- [ ] Check quantities make sense
- [ ] Note any ingredients that look wrong

### Data Reset
- [ ] Clear any test shopping trips from history
- [ ] Clear any test Quick Add items
- [ ] Verify last known prices are accurate (or clear them)
- [ ] Set dark mode preference

---

## Market Testing - Vendor 1 (e.g., Big King)

### Shopping Phase
- [ ] Check off items as you find them
  - [ ] Note: How easy is it to tap checkboxes?
  - [ ] Issue: Any accidental taps?
  - [ ] Speed: Faster or slower than mental checklist?

### Quick Add Test (if needed)
- [ ] Tap "Quick Add Item"
- [ ] Enter: `ginger 500g`
- [ ] Verify it parses correctly (name, quantity, unit)
- [ ] Try: `fresh chilies 200g`
- [ ] Check if it appears in shopping list

### Purchase Recording
- [ ] Get receipt/total: NT$ _______
- [ ] Tap "Quick Log" button
  - [ ] Expected: Modal opens instantly
  - [ ] Issue: Any delay or blank page?
  
- [ ] Enter total in "Trip Total" field
  - [ ] Issue: Keyboard type correct (numeric)?
  - [ ] Issue: Decimal point accessible?

- [ ] Check "Vendor" dropdown
  - [ ] Expected: "Big King" suggested automatically?
  - [ ] Actual: _______________
  - [ ] Issue: Was suggestion accurate?

- [ ] Verify "Date" field
  - [ ] Expected: Today's date pre-filled
  - [ ] Actual: _______________

- [ ] Check "Items Being Logged" section
  - [ ] Expected: Only items you checked off
  - [ ] Count: _____ items
  - [ ] Issue: Any wrong items listed?

- [ ] Tap "Save Trip"
  - [ ] Expected: Success message appears
  - [ ] Expected: Modal closes
  - [ ] Expected: Items stay checked (for multi-stop trips)
  - [ ] Issue: Any error messages?

---

## Market Testing - Vendor 2 (e.g., Street Market Veggies)

### Shopping Phase
- [ ] Continue to next vendor
- [ ] Check off NEW items you're buying here
  - [ ] Note: Previous items should still be checked
  - [ ] Issue: Are previously checked items interfering?

### Purchase Recording
- [ ] Get receipt/total: NT$ _______
- [ ] Tap "Quick Log" button

- [ ] Enter total

- [ ] Check vendor dropdown
  - [ ] Expected: "Street Market - Veggies" suggested?
  - [ ] Actual: _______________
  - [ ] Issue: Wrong suggestion? Why?

- [ ] **CRITICAL TEST:** Check "Items Being Logged" list
  - [ ] Expected: ONLY new items from this vendor
  - [ ] Expected: NOT items from previous vendor
  - [ ] Actual items listed: _______________
  - [ ] Count: _____ items
  - [ ] ❌ Issue: Duplicates from Vendor 1?
  - [ ] ✅ Success: Only new items?

- [ ] Save trip

---

## Market Testing - Vendor 3 (e.g., Vietnamese Vendor)

### Repeat Process
- [ ] Buy items from third vendor
- [ ] Check them off
- [ ] Quick Log: NT$ _______
- [ ] Verify vendor suggestion: _______________
- [ ] Verify items logged: _______________
- [ ] Save trip

### Multi-Stop Verification
- [ ] After saving 3rd trip, tap "Trip History"
- [ ] Expected: See 3 separate trips
- [ ] Verify each trip:
  - [ ] Trip 1: _____ items, NT$ _____
  - [ ] Trip 2: _____ items, NT$ _____
  - [ ] Trip 3: _____ items, NT$ _____
- [ ] ❌ Issue: Any duplicate items across trips?
- [ ] ✅ Success: Each trip shows only its items?

---

## Supermarket Testing (e.g., RT-Mart)

### Price Recording Test
- [ ] Buy at least 5 items with known per-unit prices
- [ ] After checkout, tap "Update Prices" button
  
### For Each Item:
Item 1: _______________
- [ ] Package quantity shown: _______
- [ ] Package unit shown: _______
- [ ] Enter package price: NT$ _______
- [ ] Wait 2 seconds
- [ ] Expected: Auto-saved (green checkmark?)
- [ ] Issue: Any save confirmation?

Item 2-5: Repeat process

### Load Prices Test
- [ ] Next shopping trip, select same recipes
- [ ] Tap "Load Prices" button
- [ ] Expected: Prices auto-fill for items you just saved
- [ ] Actual: _____ out of 5 items got prices
- [ ] Issue: Any missing prices? Why?

---

## Post-Shopping Analysis (Saturday Evening)

### Trip History Review
- [ ] Open app
- [ ] Tap "Trip History" button
- [ ] Expected: All trips from today listed
- [ ] Count trips: _____ (should match number of stops)

### For Each Trip Listed:
Trip 1:
- [ ] Date shown: _______________
- [ ] Vendor shown: _______________
- [ ] Total shown: NT$ _______
- [ ] Item count shown: _____ items
- [ ] Tap "View Details"
- [ ] Check: All items listed correctly?
- [ ] Issue: Any missing items?

Trip 2-3+: Repeat

### CSV Export Test
- [ ] In Trip History, tap "Export to CSV"
- [ ] Expected: File downloads (shopping-trips-YYYY-MM-DD.csv)
- [ ] Check Files app or Downloads
- [ ] File found? _______________
- [ ] Open in Apple Numbers/Excel
- [ ] Verify columns:
  - [ ] Date
  - [ ] Vendor
  - [ ] Mode
  - [ ] Total
  - [ ] Item Count
  - [ ] Items
- [ ] Issue: Any formatting problems?

### Delete Trip Test
- [ ] Back in app Trip History
- [ ] Find a trip to delete
- [ ] Tap "Delete" button
- [ ] Expected: Confirmation prompt?
- [ ] Confirm deletion
- [ ] Expected: Trip removed from list
- [ ] Issue: Any error?

### Reset Test
- [ ] After shopping complete, tap "Reset" button
- [ ] Expected: Confirmation prompt
- [ ] Confirm reset
- [ ] Expected: All checkmarks cleared
- [ ] Expected: Shopping list refreshed
- [ ] Issue: Anything not reset?

---

## Sunday Testing - Second Market Day

### Full Workflow Test
- [ ] Select different recipes for Sunday cooking
- [ ] Use Quick Add to add 2-3 ad-hoc items
- [ ] Go shopping (even if just 1-2 items)
- [ ] Test Quick Log workflow again
- [ ] Verify vendor suggestions work
- [ ] Check Trip History shows both days

### Price Verification
- [ ] For items you bought Saturday
- [ ] Check if "Load Prices" button works
- [ ] Expected: Saturday's prices auto-fill
- [ ] Actual: _______________
- [ ] Issue: Prices from previous day persisting?

---

## Edge Case Testing

### Zero Quantity Test
- [ ] Try adding Quick Add item: `salt 0g`
- [ ] Expected behavior: _______________
- [ ] Issue: App crash? Error? Accepts it?

### Negative Price Test
- [ ] In Update Prices, try entering: NT$ -10
- [ ] Expected behavior: _______________
- [ ] Issue: Accepts negative? Validation?

### Zero Dollar Trip Test
- [ ] Quick Log with NT$ 0
- [ ] Expected behavior: _______________
- [ ] Issue: Allows it? Makes sense for free samples?

### Duplicate Quick Add Test
- [ ] Quick Add: `tomatoes 500g`
- [ ] Quick Add again: `tomatoes 1kg`
- [ ] Expected: Both appear? Or merged?
- [ ] Actual: _______________

### Vendor Change After Auto-Suggest Test
- [ ] Start Quick Log (vendor auto-suggested)
- [ ] Manually change vendor dropdown
- [ ] Save trip
- [ ] Expected: Saves with manually selected vendor
- [ ] Issue: Reverts to suggestion?

### Empty Trip Log Test
- [ ] Don't check off any items
- [ ] Try to Quick Log
- [ ] Expected: Error message? Grayed out button?
- [ ] Actual: _______________

---

## Performance Testing

### Responsiveness
- [ ] Opening app from home screen
  - Speed: ⚡ Instant | ⏱️ 1-2s | 🐌 3+ seconds
  
- [ ] Switching between views (Recipes → Price → History)
  - Speed: ⚡ Instant | ⏱️ 1-2s | 🐌 3+ seconds
  
- [ ] Checking off items in shopping list
  - Speed: ⚡ Instant | ⏱️ Slight lag | 🐌 Noticeable delay
  
- [ ] Opening Quick Log modal
  - Speed: ⚡ Instant | ⏱️ 1-2s | 🐌 3+ seconds
  
- [ ] Loading Trip History with 10+ trips
  - Speed: ⚡ Instant | ⏱️ 1-2s | 🐌 3+ seconds

### Battery Impact
- [ ] Battery % at start of shopping: _____%
- [ ] Battery % at end of shopping: _____%
- [ ] Screen-on time for app: _____ minutes
- [ ] Issue: Excessive battery drain?

### Mobile Data Usage (if not on WiFi)
- [ ] App works completely offline? ✅ Yes | ❌ No
- [ ] Any network requests during use? _______________

---

## User Experience Assessment

### Compared to Current Siri Method

**Current Method:**
1. After vendor, say "Hey Siri, 297 veggies"
2. Later, manually enter in spreadsheet
3. Look up individual items
4. Calculate totals

**New Method:**
1. Check items as shopping
2. Quick Log at vendor
3. Auto-captures items + total
4. Export CSV → paste in Numbers

### Questions:

**Time Savings:**
- Current method time per shopping trip: ~_____ minutes
- New method time per shopping trip: ~_____ minutes
- Time saved: _____ minutes per trip

**Accuracy:**
- With Siri: Did you ever forget to log a vendor? _______________
- With app: Any missed vendors? _______________
- Issue: Any incorrect item logging?

**Ease of Use:**
- Siri method difficulty: 😊 Easy | 😐 Okay | 😫 Tedious
- App method difficulty: 😊 Easy | 😐 Okay | 😫 Tedious
- Preference: Siri | App | No clear winner

**Workflow Friction:**
- What was annoying about the app? _______________
- What worked really well? _______________
- What's still confusing? _______________

---

## Feature Requests / Ideas

### Missing Features
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________

### Nice-to-Have Improvements
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________

### Bugs Found
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________

---

## Dark Mode Testing

- [ ] Toggle dark mode ON
  - [ ] All text readable?
  - [ ] Any contrast issues?
  - [ ] Buttons visible?
  
- [ ] Toggle dark mode OFF
  - [ ] All text readable?
  - [ ] Any contrast issues?

- [ ] Preferred mode: ⬛ Dark | ⬜ Light | 🔄 Switch based on time

---

## Button Visibility Test (iPhone)

### Main Header Buttons
- [ ] Dark Mode toggle - Visible? _______________
- [ ] Price History - Visible? _______________
- [ ] Update Prices - Visible? _______________
- [ ] Manage Recipes - Visible? _______________
- [ ] Trip History - Visible? _______________

### Navigation Behavior
- [ ] On portrait mode: Buttons wrap to 2nd row? _______________
- [ ] On landscape mode: Buttons fit in 1 row? _______________
- [ ] Issue: Any buttons hidden or cut off?

### Action Buttons (Load Prices, Quick Log, Reset)
- [ ] All 3 visible when scrolled to bottom? _______________
- [ ] Disabled state clear (grayed out)? _______________
- [ ] Enabled state clear (colored)? _______________
- [ ] Issue: Confusion about when buttons are usable?

---

## Overall Assessment

### Would You Use This App Long-Term?
⭐⭐⭐⭐⭐ Definitely  
⭐⭐⭐⭐ Probably  
⭐⭐⭐ Maybe  
⭐⭐ Probably not  
⭐ No

### Main Reason:
_______________________________________________

### One Thing to Fix First:
_______________________________________________

### One Thing That Exceeded Expectations:
_______________________________________________

---

## Data Collection for Analysis

### Trip Summary
- Total trips logged: _____
- Total amount spent: NT$ _______
- Total items purchased: _____
- Vendors visited: _______________

### Time Tracking
- Time spent setting up: _____ min
- Time spent shopping with app: _____ min
- Time saved vs manual entry: _____ min

### Error Count
- App crashes: _____
- Wrong data logged: _____
- Confusing UX moments: _____
- Button press misses: _____

---

## Next Steps (To Discuss Monday)

### Critical Fixes Needed
1. _______________________________________________
2. _______________________________________________

### Enhancements Worth Doing
1. _______________________________________________
2. _______________________________________________

### Code Refactoring Priority
Based on CODE_AUDIT.md:
- [ ] High priority: useLocalStorage hook
- [ ] High priority: Extract QuickLogModal
- [ ] Medium priority: Button style helpers
- [ ] Low priority: Other refactors

### Decision: Single-File vs Multi-File?
Keep single file? ✅ Yes | ❌ No, go multi-file

**Reason:** _______________________________________________

---

## Final Thoughts

**What worked best:**
_______________________________________________

**What needs work:**
_______________________________________________

**Surprising discovery:**
_______________________________________________

**Would recommend to other restaurant owners?**
✅ Yes, definitely  
🤔 Yes, with some improvements  
❌ Not yet  

---

*Testing completed: _______________ (date)*  
*Next review: After 2 weeks of regular use*
