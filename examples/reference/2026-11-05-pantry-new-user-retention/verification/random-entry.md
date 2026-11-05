## ideas/random-entry.md

### 1. Shared-wall weeks

**Verdict:** ✅ Adherent and walkable
**Adherence:** Users who see their second planned week visibly cut waste and the shopping list have a reason to plan week three, the point where 40% stop now. That keeps them planning towards the two-month mark.
**Backward chain:**

1. New users get week plans where consecutive dinners share perishables, and the shopping list shows how much smaller it is.
2. The planner orders suggested dinners by shared perishable ingredients, and the list view compares the list against an unshared baseline.
3. Library recipes are tagged with which ingredients are perishable and in what pack sizes they are usually bought.
4. The 3,000 recipes already carry structured ingredient data, since Pantry builds shopping lists from them today. Two engineers can add perishable and pack-size tags and a sequencing rule within three months, with no hires and little spend.

### 2. Winter stores

**Verdict:** ✅ Adherent and walkable
**Adherence:** Filling two or three nights of weeks three and four from the freezer makes planning lighter right at the drop-off point, so more new users go on planning into month two.
**Backward chain:**

1. In weeks three and four, Pantry fills two or three nights from the user's logged freezer stock, and the user plans only the rest.
2. The app keeps a freezer stock per household, adding to it when a doubled dinner is marked cooked and removing from it when a frozen portion is planned.
3. In weeks one and two the planner suggests doubling two dinners and scales those recipes and the shopping list.
4. Library recipes are tagged as freezable or not.
5. The 3,000 recipes and their ingredient data exist today. The team can tag freezability (by rule plus manual review, or for a starter subset) and build the stock log within three months, with no hires and well under €10,000.

### 3. Nectar tray

**Verdict:** 🔧 Adherent, link to fix
**Adherence:** If planning day starts from a mostly drafted week, the blank-page effort that wears new users down after a week or two goes away, so more of them keep planning.
**Backward chain:**

1. On planning day, Pantry drafts most of the week from the items in the user's tray, and the user only confirms.
2. Each tray item (shared link, screenshot, typed craving, "on offer" note) is matched to library recipes.
3. Free-form captures, screenshots especially, are turned into ingredients or dishes by an image and language recognition service.
4. Pantry sends users' captured screenshots and notes to a third-party AI vendor for that recognition.
5. The app gets a share-sheet extension and a capture tray on iOS and Android.
6. Two engineers and a designer build the tray and the matching; the 3,000-recipe library is the matching target.

**Broken link:** Step 4: sending users' screenshots and personal notes to an outside AI vendor risks breaking "No selling or sharing user data". It also stretches the two engineers and the three-month deadline across capture on two platforms plus image recognition.
**Possible fix:** Limit the first version to typed text and shared recipe links, matched in-house against recipe titles and ingredients with keyword search, and leave screenshots out. No user content leaves Pantry, and the scope fits two engineers in a quarter.

### 6. Brood night

**Verdict:** ✅ Adherent and walkable
**Adherence:** In households with children, a weekly kids' night the children ask for brings the parent back to plan each week, which targets the drop-off directly. It does nothing for households without children, so the share of families among new users caps how far it moves "most new users".
**Backward chain:**

1. Children in user households look forward to their weekly night and ask about it, and the parent opens Pantry to plan it.
2. Each week the planner offers a "kids' night" slot, filled with a simple recipe shown as a kid-scaled card with big steps and jobs by age.
3. A set of simple library recipes (say 100 to 200) has kid-scaled steps and age-graded jobs written.
4. The designer has designed the kid-scaled card, and the recipes are tagged as simple and family-friendly.
5. The library, the designer and the engineers exist today. The content writing fits the team or a freelance writer well under €10,000, and the whole thing ships within three months.

### 7. Harvest frame

**Verdict:** ❌ Not adherent
**Adherence:** The first harvest frame arrives at the end of the first month, after the three-week window in which 40% of new users have already stopped opening the app. The users the brief is about never see it, so the drop-off is untouched.
**Backward chain:**

1. At each month's end, users see a harvest frame of dinners cooked, takeaway money saved and ingredients used up, and can export it as a fridge image.
2. The app estimates those figures from each user's plans, lists and cooked-dinner marks.
3. The team has defined estimation rules (for example an average takeaway cost per dinner and a waste estimate per unused ingredient).
4. Pantry already has plan and shopping-list data per user, and the team can build the summary and image export within three months.

**Actually solves:** Keeping users who have already made it through the first month motivated with a visible, shareable record of the value they have built up: month-two engagement among retained users, not the early drop-off.
