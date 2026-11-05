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

### 6. Dinner calendar feed

**Verdict:** 🔧 Adherent, link to fix
**Adherence:** Realised, the plan sits in the household's everyday calendar, so Pantry stays visible between sessions and is one tap away when a dinner needs adjusting. That supports users still planning with Pantry after two months.
**Backward chain:**

1. New users' household calendars show each planned dinner, and tapping one opens Pantry to swap or adjust it.
2. Each event carries a prep note and, by default, a calendar alert before the evening so the cook is reminded.
3. Pantry publishes a per-user subscribable iCalendar feed of the planned week, with deep links back into the app.
4. The engineers build the feed endpoint and deep links, a small job within the quarter, team and budget. This is achievable today.

**Broken link:** Step 2: default per-dinner calendar alerts make the feed an automated reminder channel on the user's device. In effect it is a push-notification campaign, which is Out of bounds.
**Possible fix:** Publish events with no alarms (no VALARM in the feed) and leave any alerts to the user's own calendar settings. The feed then gives visibility, not notifications.

### 7. Skip-proof week

**Verdict:** ✅ Adherent and walkable
**Adherence:** Realised, a week that didn't go to plan no longer reads as a failure. This removes a direct trigger for new users abandoning after their first or second planned week, so more stay to the two-month Desired state.
**Backward chain:**

1. New users' weeks absorb skipped dinners: uncooked dinners roll forward with their ingredients, and the summary celebrates what was cooked.
2. Flex nights, automatic roll-forward of uncooked dinners and ingredients, and a positive weekly summary ship in the planner.
3. Each dinner has a cooked/not-cooked state, and the designer has redrawn the week view and summary copy without "missed" markers.
4. The team scopes these planner and copy changes for the quarter with the current four people and no spend. This is achievable today.

### 8. Cook-swap pairs

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
