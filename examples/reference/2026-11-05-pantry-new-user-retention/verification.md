# Verification

## ideas/scamper.md

### 1. Household planning rota

**Verdict:** ✅ Adherent and walkable
**Adherence:** Once the rota runs, the household's account keeps planning dinners week after week, and the new user's cost drops to one turn in two or three. That reaches the Desired state of still planning with Pantry at two months for multi-person households, though it does nothing for users who live alone.
**Backward chain:**

1. Two months after sign-up, new households are still planning through Pantry, with the weekly planning turn passing between members.
2. Invited partners, flatmates or teenagers have joined the household account and taken at least one planning turn.
3. After week one, new users get a "who plans next week?" prompt with an invite link, and the plan screen shows whose turn it is and what they picked.
4. Shared household accounts with multiple members, an invite link and a rota view are built and shipped by the two engineers and the designer within three months. The plans stay inside the household the user chose to invite, so no user data is sold or shared. Achievable today.

### 2. Leftover-led second week

**Verdict:** ✅ Adherent and walkable
**Adherence:** Every new week opens with a concrete, waste-saving reason to plan in Pantry, and it lands exactly on weeks two and three when users drop off. Because leftovers come back every week, the pull can last until the two-month mark.
**Backward chain:**

1. When users start planning a new week, Pantry lists last week's unused items and proposes library dinners that use them up, and new users keep planning this way past week eight.
2. Pantry can estimate what is left over (bought quantity minus what the planned recipes used, with a quick "which dinners did you skip?" confirmation) and find recipes in the library that contain those ingredients.
3. The recipe library's structured ingredient quantities, which already drive the shopping list, are paired with typical pack sizes, and an ingredient-overlap search is built.
4. The two engineers add pack-size data and the matching logic, and the designer reworks the start of week-two planning, all within three months and well under €10,000. Achievable today.

### 3. Four-week cooking seasons

**Verdict:** ✅ Adherent and walkable
**Adherence:** A four-week arc with a visible episode count and a finale gives weeks two and three a reason to come back, and offering the next season at week four carries users into and through the second month, which is the Desired state.
**Backward chain:**

1. New users join a season at sign-up, and most finish it and start a second one, so they are still planning at two months.
2. A catalogue of themed four-week seasons exists in the app, with an episode counter, a finale dinner and an offer of the next season when one ends.
3. The product lead and designer have curated six to eight seasons from the existing 3,000 recipes, and the engineers have built the season layer on top of weekly planning.
4. The four-person team curates the seasons and ships the feature within three months, with no new hires and next to no spend. Achievable today.

### 4. Plan once, rotate a month

**Verdict:** ✅ Adherent and walkable
**Adherence:** It goes straight at the weekly planning effort behind the drop-off: keeping going means a one-minute swap instead of a full session, so staying with Pantry for two months becomes the easy path. Users still plan each week's dinners and get the shopping list through Pantry.
**Backward chain:**

1. New users plan in one session, then make quick weekly swaps on a four-week rotating menu, and are still doing so at two months.
2. Pantry turns one planning session into a four-week rotation with small variations, and offers a quick swap flow each week.
3. The library's recipes are tagged well enough to pick close variants (same base, different protein or vegetable), and a rotation generator and swap screen are designed and built.
4. The two engineers and the designer build the generator and swap flow within three months using existing recipe data. Achievable today.

### 5. The household's own cookbook

**Verdict:** 🔧 Adherent, link to fix
**Adherence:** A cookbook that grows more valuable each week would keep users planning with Pantry into the second month, which matches the Desired state. As described, though, its pull only builds up after the weeks when users leave.
**Backward chain:**

1. By week eight, the household's personal cookbook is its go-to source for planning, and leaving Pantry would mean losing it.
2. The household has cooked, rated and annotated weeks' worth of dinners in Pantry.
3. The household kept planning through weeks two and three, when its cookbook held only a handful of dinners.
4. Pantry asks after each dinner whether it was cooked and how it went, and saves rated dinners with notes into a cookbook view.
5. The engineers and designer build the rating prompt, notes and cookbook view within three months. Achievable today.

**Broken link:** Step 3: the brief's Problem says users leave after their first or second week, when a cookbook of five or so dinners has too little value to hold them. The idea pays off only after the drop-off window it needs to get through.
**Possible fix:** Fill the cookbook at sign-up with the household's own regular dinners and family recipes (typed in or matched to library recipes), so it is already worth keeping in week one and the weekly ratings add to it from there.

### 6. Library-free first month

**Verdict:** ✅ Adherent and walkable
**Adherence:** Early weeks built on dinners the household already cooks are easy wins that take away the overreaching first plan that leads to quitting. Users keep planning past week three, and the library opening gradually gives them something new as they reach the second month.
**Backward chain:**

1. For their first four weeks, new users plan only from their own dozen regular dinners and still get a full shopping list, then see one library suggestion a week from week five onwards.
2. Each regular dinner entered at sign-up has an ingredient list, so the shopping list can still be built.
3. At sign-up, each dinner typed in a few words is matched to the closest library recipe (for example "spaghetti bolognese"), and users can adjust the ingredients.
4. The engineers build the name-to-recipe matching, a library-free planning mode for the first month and the gradual library unlock, within three months. Achievable today.

### 7. Cooked-it check-in first

**Verdict:** 🔧 Adherent, link to fix
**Adherence:** If users really did a five-second daily check-in and got next week's plan from it, they would still be planning with Pantry at two months, so the end state matches the Desired state.
**Backward chain:**

1. Two months after sign-up, new users still tap a daily "what did you eat last night?" check-in, and Pantry builds next week's plan from those taps.
2. New users open Pantry every day during the first weeks and the check-in becomes a habit.
3. Something brings users back to the app every day, before the habit has formed.
4. A daily reminder sends users to the check-in.
5. The app's opening screen is redesigned around yesterday's check-in, and a plan generator is built from check-in history. The engineers and designer can ship this within three months. Achievable today.

**Broken link:** Step 4: a daily reminder in practice means a push-notification campaign, which is Out of bounds. Without it, step 2 relies on new users opening the app daily on their own, the very behaviour that is failing.
**Possible fix:** Attach the check-in to moments when users already open Pantry or look at it without being pushed: a home-screen widget showing tonight's dinner with a "cooked it" tap, the check-in shown when they open tonight's recipe to cook, and a one-tap "what did you eat this week?" link in the weekly planning email.

## ideas/challenge.md

### 1. Basket-first week

**Verdict:** ✅ Adherent and walkable
**Adherence:** Realised, new users plan their dinners in a two-minute sort after the shop they already do. The weekly chore that drives drop-off after the first or second week is gone, so they keep planning with Pantry into month two, which is the Desired state.
**Backward chain:**

1. New users plan each week's dinners in Pantry after shopping, from what they bought.
2. A "plan from my basket" flow ships: a quick ingredient grid, plus a receipt photo read by on-device text recognition (the free iOS/Android OCR frameworks, so no receipt data leaves the phone). It then suggests dinners from the 3,000-recipe library.
3. The recipe library is tagged by main ingredients so recipes can be matched against a basket, and the designer has mocked up the grid.
4. The two engineers and the designer schedule the grid and matching for this quarter, with OCR as a second step. This fits the team, the €10,000 budget and the three-month window, and is achievable today.

### 2. Three-night horizon

**Verdict:** ✅ Adherent and walkable
**Adherence:** Realised, new users never face the heavy seven-dinner session they abandon after a week or two. Short, low-effort re-plans keep them planning with Pantry continuously, which is the Desired state.
**Backward chain:**

1. New users plan the next three dinners in Pantry every few days and are still doing so after two months.
2. A rolling three-night plan mode ships as the default for new users. It re-plans from what was marked cooked and builds a shopping list for those nights.
3. The planner and shopping-list logic accept a variable horizon instead of a fixed week, and a "cooked" tick exists on each dinner.
4. The team scopes the planner change and the cooked tick as a quarter's work for two engineers and the designer. This is achievable today within the constraints.

### 3. Family veto link

**Verdict:** ✅ Adherent and walkable
**Adherence:** Realised, the planner has household members waiting on and reacting to each draft week. That gives a recurring reason to open Pantry and finalise the plan, so planning continues past week three towards the two-month Desired state.
**Backward chain:**

1. New users share each week's draft through a link, household members vote or claim cooking nights, and the planner finalises the week in Pantry.
2. A plain web page for a draft week ships, reachable by an unguessable link the planner chooses to share. It records thumbs-up, veto and "my turn" taps and shows them back in the app. Only the planner shares it, so Pantry sells or shares no user data.
3. A lightweight web view of a plan and a votes endpoint are built on the existing backend.
4. The two engineers and the designer schedule the web view and votes for the quarter, with hosting costs well under €10,000. This is achievable today.

### 4. Dinner calendar feed

**Verdict:** 🔧 Adherent, link to fix
**Adherence:** Realised, the plan sits in the household's everyday calendar, so Pantry stays visible between sessions and is one tap away when a dinner needs adjusting. That supports users still planning with Pantry after two months.
**Backward chain:**

1. New users' household calendars show each planned dinner, and tapping one opens Pantry to swap or adjust it.
2. Each event carries a prep note and, by default, a calendar alert before the evening so the cook is reminded.
3. Pantry publishes a per-user subscribable iCalendar feed of the planned week, with deep links back into the app.
4. The engineers build the feed endpoint and deep links, a small job within the quarter, team and budget. This is achievable today.

**Broken link:** Step 2: default per-dinner calendar alerts make the feed an automated reminder channel on the user's device. In effect it is a push-notification campaign, which is Out of bounds.
**Possible fix:** Publish events with no alarms (no VALARM in the feed) and leave any alerts to the user's own calendar settings. The feed then gives visibility, not notifications.

### 5. Skip-proof week

**Verdict:** ✅ Adherent and walkable
**Adherence:** Realised, a week that didn't go to plan no longer reads as a failure. This removes a direct trigger for new users abandoning after their first or second planned week, so more stay to the two-month Desired state.
**Backward chain:**

1. New users' weeks absorb skipped dinners: uncooked dinners roll forward with their ingredients, and the summary celebrates what was cooked.
2. Flex nights, automatic roll-forward of uncooked dinners and ingredients, and a positive weekly summary ship in the planner.
3. Each dinner has a cooked/not-cooked state, and the designer has redrawn the week view and summary copy without "missed" markers.
4. The team scopes these planner and copy changes for the quarter with the current four people and no spend. This is achievable today.

### 6. Cook-swap pairs

**Verdict:** 🔧 Adherent, link to fix
**Adherence:** Realised, new users have a standing weekly commitment to another household built into their plan. That is an outside reason to keep planning with Pantry for months, which is the Desired state.
**Backward chain:**

1. Pairs of nearby households each cook a double batch of one planned dinner a week and swap portions, with the swap scheduled in Pantry.
2. Opted-in new users have each been matched with another household close enough to hand over food weekly.
3. Pantry matches opted-in users by location and discloses each household's name and rough address to its match so they can meet.
4. An opt-in, a location field and a matching and shared-schedule feature are built.
5. The engineers and designer scope the opt-in, matching and shared schedule for the quarter. This is achievable today.

**Broken link:** Step 3: Pantry matching strangers means passing one user's identity and location to another household. That breaks "no selling or sharing user data". With 18,000 users spread out, it also leaves many new users with no nearby match.
**Possible fix:** Drop Pantry-run matching and let a user invite a household they already know (a friend, neighbour or relative) through an invite link. The pair is formed by the users themselves and Pantry shares nothing.

## ideas/provocation.md

### 1. Everyone owns a night

**Verdict:** ✅ Adherent and walkable
**Adherence:** Once household members own nights, the week's plan no longer hangs on one person's motivation: others expect their night to be on it and their picks to show up on the list. That gives new account holders a reason to keep planning weekly past the first two weeks, which is the brief's Desired state. It does carry a risk: it only helps multi-person households, so single-person users get no retention gain from it.
**Backward chain:**

1. New users regularly hand nights to partners or children through a no-account link. Pantry's week view shows each person's name on their night, and their picks go straight into the shopping list.
2. The feature is live in the app: the account holder can generate a per-night link, a lightweight web page lets the guest choose from a shortlist without signing up, and the chosen recipe is merged into the plan and the shopping list. It is built by the two engineers within the three-month window, with no new hires and essentially no spend beyond existing hosting.
3. The designer has designed the guest picker page and the named-night week view, and the product lead has set the rules. The shortlist is drawn from the existing 3,000-recipe library, links expire after the night is planned, and links are only shared by the user through their own channels, so nothing goes out as a push campaign and no user data is sold or shared with third parties.
4. The product lead has scoped the feature as a small, link-based extension of the existing planner and put it on the quarter's roadmap for the current team of four. This is achievable today.

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

### 4. Brood night

**Verdict:** ✅ Adherent and walkable
**Adherence:** In households with children, a weekly kids' night the children ask for brings the parent back to plan each week, which targets the drop-off directly. It does nothing for households without children, so the share of families among new users caps how far it moves "most new users".
**Backward chain:**

1. Children in user households look forward to their weekly night and ask about it, and the parent opens Pantry to plan it.
2. Each week the planner offers a "kids' night" slot, filled with a simple recipe shown as a kid-scaled card with big steps and jobs by age.
3. A set of simple library recipes (say 100 to 200) has kid-scaled steps and age-graded jobs written.
4. The designer has designed the kid-scaled card, and the recipes are tagged as simple and family-friendly.
5. The library, the designer and the engineers exist today. The content writing fits the team or a freelance writer well under €10,000, and the whole thing ships within three months.

### 5. Harvest frame

**Verdict:** ❌ Not adherent
**Adherence:** The first harvest frame arrives at the end of the first month, after the three-week window in which 40% of new users have already stopped opening the app. The users the brief is about never see it, so the drop-off is untouched.
**Backward chain:**

1. At each month's end, users see a harvest frame of dinners cooked, takeaway money saved and ingredients used up, and can export it as a fridge image.
2. The app estimates those figures from each user's plans, lists and cooked-dinner marks.
3. The team has defined estimation rules (for example an average takeaway cost per dinner and a waste estimate per unused ingredient).
4. Pantry already has plan and shopping-list data per user, and the team can build the summary and image export within three months.

**Actually solves:** Keeping users who have already made it through the first month motivated with a visible, shareable record of the value they have built up: month-two engagement among retained users, not the early drop-off.
