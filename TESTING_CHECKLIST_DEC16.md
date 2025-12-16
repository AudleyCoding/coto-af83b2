# Testing Checklist - December 16, 2025 Update
**Test Date:** December 16, 2025  
**Features Added:** Quick Add auto-remove, Scroll buttons, Removed Items restoration  
**Device:** iPhone/iPad  
**Goal:** Validate new UX improvements and bug fixes

---

## 🎯 New Features to Test

### Feature 60: Auto-Remove Quick Add Items When Checked
**Status:** ⬜ Not Tested | ⬜ Pass | ⬜ Fail

**Test Steps:**
1. [ ] Add item via Quick Add: "garlic paste 300g"
2. [ ] Verify item appears in Quick Add panel
3. [ ] Verify item appears in shopping list
4. [ ] Check off item in shopping list (mark as purchased)
5. [ ] **EXPECTED:** Item moves to Purchased section
6. [ ] **EXPECTED:** Item disappears from Quick Add panel automatically
7. [ ] **VERIFY:** No need to click X to remove it

**Edge Cases:**
- [ ] Add multiple Quick Add items, check one off → only that one removed from panel
- [ ] Add Quick Add item that matches recipe item → checking off removes from Quick Add panel
- [ ] Uncheck Quick Add item → does NOT re-appear in Quick Add panel (stays removed)

**Notes:**
```
[Record any issues or observations here]
```

---

### Feature 61: Scroll-to-Top Buttons on All Major Views
**Status:** ⬜ Not Tested | ⬜ Pass | ⬜ Fail

**Test Recipes View:**
1. [ ] Navigate to Recipes view
2. [ ] Scroll down past 10+ recipes
3. [ ] **EXPECTED:** Blue circular button appears in bottom-right corner
4. [ ] Tap the scroll button
5. [ ] **EXPECTED:** Page smoothly scrolls to top
6. [ ] Scroll back to top manually
7. [ ] **EXPECTED:** Button disappears when near top

**Test Shopping List:**
1. [ ] Select 3-4 recipes to generate long shopping list
2. [ ] Scroll down to bottom of list
3. [ ] **EXPECTED:** Scroll button appears
4. [ ] Tap button → scroll to top
5. [ ] **VERIFY:** Can access action buttons quickly

**Test Price History Detail:**
1. [ ] Go to Price History
2. [ ] Select ingredient with 5+ price entries
3. [ ] Scroll down to see all entries
4. [ ] **EXPECTED:** Scroll button appears
5. [ ] Tap button → return to statistics/chart at top

**Test Trips View:**
1. [ ] Navigate to Trips
2. [ ] If you have 5+ trips, scroll down
3. [ ] **EXPECTED:** Scroll button appears
4. [ ] Tap button → return to filters at top

**Button Appearance:**
- [ ] Button is blue with white up arrow icon
- [ ] Button size feels tappable (not too small)
- [ ] Button doesn't cover important content
- [ ] Button appears only after scrolling >300px
- [ ] Button position consistent across all views

**Notes:**
```
[Record any issues or observations here]
```

---

### Feature 62: Removed Items Restoration
**Status:** ⬜ Not Tested | ⬜ Pass | ⬜ Fail

**Basic Functionality:**
1. [ ] Select recipe with 5+ ingredients
2. [ ] All items should have blue bag icons (in shopping list)
3. [ ] Click bag icon on "turmeric powder" to remove it
4. [ ] **EXPECTED:** Bag icon turns gray
5. [ ] **EXPECTED:** Item stays visible in shopping list
6. [ ] Scroll down below shopping list
7. [ ] **EXPECTED:** "🗑️ Removed Items (1)" section appears
8. [ ] **VERIFY:** Section shows "turmeric powder (15 g)"
9. [ ] Click on turmeric powder in Removed Items section
10. [ ] **EXPECTED:** Item instantly returns to shopping list
11. [ ] **EXPECTED:** Bag icon turns blue again
12. [ ] **VERIFY:** Removed Items section now empty/hidden

**Multiple Removed Items:**
1. [ ] Remove 3 items from shopping list (click bag icons)
2. [ ] **VERIFY:** "Removed Items (3)" section shows all 3
3. [ ] Restore one item by clicking it
4. [ ] **VERIFY:** Count updates to "Removed Items (2)"
5. [ ] Restore remaining items one by one
6. [ ] **VERIFY:** Section disappears when count reaches 0

**Critical Bug Fix Test:**
1. [ ] Remove item: "shallot paste" (bag icon turns gray)
2. [ ] **VERIFY:** Shallot paste in Removed Items section
3. [ ] Check off different item: "palm sugar" (mark as purchased)
4. [ ] **EXPECTED:** Palm sugar moves to Purchased section
5. [ ] **EXPECTED:** Shallot paste STAYS in Removed Items (not restored)
6. [ ] **VERIFY:** This was the main bug - items should NOT auto-restore

**Removed vs Purchased Interaction:**
1. [ ] Remove item "A" (goes to Removed Items)
2. [ ] Check off item "B" (goes to Purchased)
3. [ ] Uncheck item "B" (remove from Purchased)
4. [ ] **EXPECTED:** Item "B" returns to shopping list (NOT Removed Items)
5. [ ] **VERIFY:** Item "A" still in Removed Items (unaffected)

**Recipe Selection Changes:**
1. [ ] Remove item from shopping list
2. [ ] **VERIFY:** Item in Removed Items section
3. [ ] Deselect the recipe that contained that item
4. [ ] **EXPECTED:** Item disappears completely (not in Removed Items)
5. [ ] Re-select the recipe
6. [ ] **EXPECTED:** Item auto-adds back to shopping list (not Removed Items)

**Quick Add Items:**
1. [ ] Add Quick Add item: "basil 50g"
2. [ ] Remove it from shopping list (gray bag icon)
3. [ ] **VERIFY:** Appears in Removed Items section
4. [ ] Restore it from Removed Items
5. [ ] **VERIFY:** Back in shopping list with blue bag icon

**Visual/UX:**
- [ ] Removed Items section has gray background
- [ ] Section header shows "🗑️ Removed Items (count)"
- [ ] "Click to restore" hint visible
- [ ] Each item shows ↩️ arrow icon
- [ ] Item names and quantities clearly visible
- [ ] Hover/tap feedback works on buttons
- [ ] Section auto-hides when empty (no clutter)

**Notes:**
```
[Record any issues or observations here]
```

---

## 🔧 Bug Fixes to Verify

### Fix: Multi-word Quick Add Parsing
**Status:** ⬜ Not Tested | ⬜ Pass | ⬜ Fail

**Test Cases:**
1. [ ] Quick Add: "garlic paste 300g"
   - **EXPECTED:** Name="garlic paste", Qty=300, Unit="g"
2. [ ] Quick Add: "garlic paste 300 g" (with space)
   - **EXPECTED:** Same parsing result
3. [ ] Quick Add: "fish sauce 500ml"
   - **EXPECTED:** Name="fish sauce", Qty=500, Unit="ml"
4. [ ] Quick Add: "palm sugar" (no quantity)
   - **EXPECTED:** Name="palm sugar", no quantity displayed

**Notes:**
```
[Record any issues or observations here]
```

---

### Fix: Unit Price-Based Price History
**Status:** ⬜ Not Tested | ⬜ Pass | ⬜ Fail

**Test Scenario:**
1. [ ] Go to Price History → Select "palm sugar"
2. [ ] Add three entries:
   - NT$39 for 6 pcs
   - NT$78 for 12 pcs
   - NT$195 for 30 pcs
3. [ ] **EXPECTED:** Chart shows FLAT LINE (all at NT$6.5/pc)
4. [ ] **VERIFY:** Statistics show "Current: NT$6.5/pc" (not NT$195)
5. [ ] **VERIFY:** Table has "Unit Price" column showing NT$6.5/pc for all entries
6. [ ] **VERIFY:** No false "400% increase" alarm

**Notes:**
```
[Record any issues or observations here]
```

---

## 📱 Full Workflow Test

### Real Shopping Trip Simulation
**Status:** ⬜ Not Tested | ⬜ Pass | ⬜ Fail

**Setup:**
1. [ ] Select 2-3 recipes you'll actually cook
2. [ ] Add 1-2 Quick Add items you need
3. [ ] Remove 1 item you already have (test Removed Items)
4. [ ] Verify shopping list looks correct

**At Market - Vendor 1:**
1. [ ] Open app on iPhone (PWA from home screen)
2. [ ] Check off items as you find them
3. [ ] **VERIFY:** Quick Add items disappear from panel when checked
4. [ ] Add unexpected item via Quick Add if needed
5. [ ] Use scroll button to return to top if list is long
6. [ ] Record total cost in Quick Log

**At Market - Vendor 2:**
1. [ ] Continue checking off items
2. [ ] **VERIFY:** Previously removed item stays in Removed Items (not auto-restored)
3. [ ] If you need removed item after all, restore it from Removed Items
4. [ ] Record second vendor's total in Quick Log

**After Shopping:**
1. [ ] Review Trips page
2. [ ] Verify both vendors logged correctly
3. [ ] Check total expenses
4. [ ] Reset shopping list for next time

**Notes:**
```
[Record any workflow issues or suggestions here]
```

---

## 🎨 UI/UX Validation

### Dark Mode
- [ ] All new features work in dark mode
- [ ] Removed Items section readable in dark mode
- [ ] Scroll button visible against dark background
- [ ] No color contrast issues

### Touch Targets
- [ ] Removed Items buttons easy to tap
- [ ] Scroll button size adequate (48px+)
- [ ] No accidental taps on nearby elements

### Performance
- [ ] Scroll-to-top animation smooth
- [ ] Removed Items section updates instantly
- [ ] Quick Add removal happens immediately
- [ ] No lag when checking off items

---

## 📝 Summary

**Test Results:**
- Total Tests: _____ / _____
- Passed: _____ 
- Failed: _____
- Issues Found: _____

**Critical Issues:**
```
[List any blocking issues that prevent normal use]
```

**Minor Issues:**
```
[List any cosmetic or non-blocking issues]
```

**Suggestions:**
```
[List any feature requests or improvements]
```

**Overall Assessment:**
⬜ Ready for Production  
⬜ Needs Minor Fixes  
⬜ Needs Major Fixes  

**Tester:** _________________  
**Date Completed:** _________________  
**Next Steps:** _________________
