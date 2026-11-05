# Report: Pantry new-user retention

## Techniques

| Technique | Skill | Why |
| --- | --- | --- |
| SCAMPER | `lateral-scamper` | Pantry already exists, so the problem is reworking its weekly planning loop rather than starting from nothing. |
| Challenge | `lateral-challenge` | Planning a whole week of dinners before shopping is an established habit of the category whose reasons nobody questions. |
| Provocation | `lateral-provocation` | The obvious solution is an incremental tweak (better onboarding, more emails), and the brief rests on taken-for-granted assumptions about who plans and in what order. |
| Random Entry | `lateral-random-entry` | App-retention thinking is stuck inside one frame; an outside stimulus breaks it. |

**Skipped:** none

## Shortlist

### 1. Basket-first week

**Card:** ideas/challenge.md › 1. Basket-first week
**Source:** Challenge, Provocation (converged)
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and the furthest from the baseline: it reverses the order of planning and shopping instead of coaching users through the existing order; reached by Challenge and Provocation.
**Movement:** Replaced: the order plan-then-buy was swapped for buy-then-plan, so the shopping list stops being the output and the groceries become the input, which removes the effort barrier that appears once the novelty of the first week fades. / Provocation: Special circumstances: buying first is already what many households do on a busy week, which is exactly when a plan-first app gets abandoned. An off-the-shelf OCR service fits the budget and lets the app meet those weeks instead of losing them.
**First step:** Ask 15 users who stopped after week two to photograph their next supermarket receipt, and hand-build a week of dinners from each to see how many they would cook.

### 2. Plan once, rotate a month

**Card:** ideas/scamper.md › 4. Plan once, rotate a month
**Source:** SCAMPER, Challenge, Provocation, Random Entry (converged)
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and removes the weekly planning session altogether; the strongest convergence of the session (four techniques).
**Movement:** Applied to the weekly planning session: making it much rarer (monthly) and the weekly task much smaller (swap, don't build) removes the repeated effort that users abandon after a week or two. / Challenge: Dropped: without novelty as the value, the 3,000-recipe library stops being a search burden and becomes an occasional extra, while the real household habit (eating the same favourites) becomes the core of the plan. / Provocation: Extract a principle: if past meals write the plan, the past is the planner. Most households eat about ten dinners on repeat; making that repertoire the starting point turns the weekly effort into a two-tap confirmation. / Random Entry: A comb is a small, reused structure that grows at its edge, not a fresh build every season. Most households eat a rotation of familiar meals, so the plan could reuse what works and add one new cell at a time.
**First step:** Prototype a "turn this week into a four-week rotation" button in Figma and test it with five new users in their second week.

### 3. Everyone owns a night

**Card:** ideas/provocation.md › 5. Everyone owns a night
**Source:** Provocation, Random Entry (converged)
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and changes the actor: planning no longer rests on one person's motivation; reached by Provocation and Random Entry.
**Movement:** Positive aspects: if eaters plan, the planner is no longer alone with the chore and others start to expect the app's week to exist. Keeping that good means splitting nights, so the habit lives in the household rather than in one tired person. / Random Entry: No single bee builds the comb; the whole hive adds cells. Weekly planning often falls on one person, who burns out, so spreading the cells across the household shares the load and the ownership.
**First step:** Ship a no-account web link that lets one other household member pick one dinner, behind a flag for 5% of new sign-ups.

### 4. Library-free first month

**Card:** ideas/scamper.md › 6. Library-free first month
**Source:** SCAMPER
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and inverts the product's main asset for the first month, cutting choice overload where the baseline adds guidance.
**Movement:** Applied to the recipe library as the starting point of planning: removing it takes away the choice overload and the ambitious, unfamiliar weeks that new users fail to cook and then abandon.
**First step:** Add an optional "just my usual dinners" path at sign-up for one cohort and compare week-three activity with the default path.

### 5. Three-night horizon

**Card:** ideas/challenge.md › 2. Three-night horizon
**Source:** Challenge, Provocation (converged)
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and changes the planning unit from a week to three days, so the plan never goes stale; reached by Challenge and Provocation.
**Movement:** Dropped: without the whole-week unit, the large up-front commitment that users fail at in weeks one and two disappears, and planning turns into a short, frequent habit. / Provocation: Focus on the difference: without week boundaries there is no "start a new week" moment, and the brief shows drop-off at exactly those boundaries after the first or second week. A rolling strip removes the cliff and the empty grid that has to be filled from scratch.
**First step:** Run a two-week diary study with ten new users planning only three dinners at a time on paper, and count how many keep going.

### 6. Leftover-led second week

**Card:** ideas/scamper.md › 2. Leftover-led second week
**Source:** SCAMPER, Challenge, Provocation (converged)
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and links each week to the last, so week two starts from the kitchen rather than a blank screen; three techniques converge on it, though it sits closer to the existing product than the cards above.
**Movement:** Applied to the shopping list and the next week's planning screen, two steps that never meet today: merging the end of one week with the start of the next turns leftovers into the reason to plan again. / Challenge: Dropped: once weeks are linked, there is always an unfinished thread pulling the user back, and the running waste-saved tally gives a reason to keep the chain going. / Provocation: Moment to moment: imagine buying first and planning second; the planner's first step becomes "what do I have?", which is the exact question a household faces at the start of week two with leftovers from week one. Pantry already knows the list, so it can answer it.
**First step:** Compute, from existing shopping lists and plans, how many week-one ingredients go unused, and mock the "you still have" screen for week two.

### 7. Winter stores

**Card:** ideas/random-entry.md › 2. Winter stores
**Source:** Random Entry
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and lightens weeks three and four, exactly where users drop off, by spending effort earlier; a different mechanism from the baseline's reminders.
**Movement:** Bees fill and cap cells with honey for lean months. Early cooking could fill stores for the weeks when motivation drops, so the third week costs less effort than the first.
**First step:** Tag the 200 most-planned recipes as freezable or not and draft the "cook double" suggestion for week one.

### 8. Shared-wall weeks

**Card:** ideas/random-entry.md › 1. Shared-wall weeks
**Source:** Random Entry
**Verdict:** ✅ Adherent and walkable
**Why it ranks here:** ✅ and makes the saving visible in week two through how dinners are sequenced; further from the baseline than the remaining ✅ ideas but a single-technique find.
**Movement:** Cells share walls, so nothing is built twice. Dinners could share ingredients the same way, which turns the plan from a list of recipes into a chain that wastes less. The saving is a reason to keep planning.
**First step:** Tag perishables in the top 300 recipes and hand-sequence five sample weeks to measure how much the shopping list shrinks.

## Appendix

### Family veto link

**Card:** ideas/challenge.md › 3. Family veto link
**Source:** Challenge
**Technique:** Challenge, assumption challenged: `one person in the household plans and decides dinners alone`
**Verdict:** ✅ Adherent and walkable
**Note:** ✅ walkable, but closer to the baseline or to a shortlisted idea than the cards above the cut.

### Skip-proof week

**Card:** ideas/challenge.md › 7. Skip-proof week
**Source:** Challenge
**Technique:** Challenge, assumption challenged: `the household cooks dinners exactly as planned`
**Verdict:** ✅ Adherent and walkable
**Note:** ✅ walkable; it softens the weekly plan rather than changing who plans or when, so it sits closer to the baseline.

### Brood night

**Card:** ideas/random-entry.md › 6. Brood night
**Source:** Random Entry
**Technique:** Random Entry, random word: `honeycomb`
**Verdict:** ✅ Adherent and walkable
**Note:** ✅ walkable, but closer to the baseline or to a shortlisted idea than the cards above the cut.

### Household planning rota

**Card:** ideas/scamper.md › 1. Household planning rota
**Source:** SCAMPER
**Technique:** SCAMPER, operator: `Substitute`
**Verdict:** ✅ Adherent and walkable
**Note:** ✅ walkable; a lighter variant of "Everyone owns a night", which ranks above it.

### Four-week cooking seasons

**Card:** ideas/scamper.md › 3. Four-week cooking seasons
**Source:** SCAMPER
**Technique:** SCAMPER, operator: `Adapt`
**Verdict:** ✅ Adherent and walkable
**Note:** ✅ walkable, but closer to the baseline or to a shortlisted idea than the cards above the cut.

### Dinner calendar feed

**Card:** ideas/challenge.md › 6. Dinner calendar feed
**Source:** Challenge
**Technique:** Challenge, assumption challenged: `users get value only when they open the app`
**Verdict:** 🔧 Adherent, link to fix
**Note:** Step 2: default per-dinner calendar alerts make the feed an automated reminder channel on the user's device. In effect it is a push-notification campaign, which is Out of bounds. Fix: Publish events with no alarms (no VALARM in the feed) and leave any alerts to the user's own calendar settings. The feed then gives visibility, not notifications.

### Cook-swap pairs

**Card:** ideas/challenge.md › 8. Cook-swap pairs
**Source:** Challenge
**Technique:** Challenge, assumption challenged: `each household plans and cooks on its own`
**Verdict:** 🔧 Adherent, link to fix
**Note:** Step 3: Pantry matching strangers means passing one user's identity and location to another household. That breaks "no selling or sharing user data". With 18,000 users spread out, it also leaves many new users with no nearby match. Fix: Drop Pantry-run matching and let a user invite a household they already know (a friend, neighbour or relative) through an invite link. The pair is formed by the users themselves and Pantry shares nothing.

### Nectar tray

**Card:** ideas/random-entry.md › 3. Nectar tray
**Source:** Random Entry
**Technique:** Random Entry, random word: `honeycomb`
**Verdict:** 🔧 Adherent, link to fix
**Note:** Step 4: sending users' screenshots and personal notes to an outside AI vendor risks breaking "No selling or sharing user data". It also stretches the two engineers and the three-month deadline across capture on two platforms plus image recognition. Fix: Limit the first version to typed text and shared recipe links, matched in-house against recipe titles and ingredients with keyword search, and leave screenshots out. No user content leaves Pantry, and the scope fits two engineers in a quarter.

### The household's own cookbook

**Card:** ideas/scamper.md › 5. The household's own cookbook
**Source:** SCAMPER
**Technique:** SCAMPER, operator: `Put to another use`
**Verdict:** 🔧 Adherent, link to fix
**Note:** Step 3: the brief's Problem says users leave after their first or second week, when a cookbook of five or so dinners has too little value to hold them. The idea pays off only after the drop-off window it needs to get through. Fix: Fill the cookbook at sign-up with the household's own regular dinners and family recipes (typed in or matched to library recipes), so it is already worth keeping in week one and the weekly ratings add to it from there.

### Cooked-it check-in first

**Card:** ideas/scamper.md › 7. Cooked-it check-in first
**Source:** SCAMPER, Provocation (converged)
**Technique:** SCAMPER, operator: `Reverse`; Provocation, PO (distortion): `PO the household plans the week after they have eaten it.`
**Verdict:** 🔧 Adherent, link to fix
**Note:** Step 4: a daily reminder in practice means a push-notification campaign, which is Out of bounds. Without it, step 2 relies on new users opening the app daily on their own, the very behaviour that is failing. Fix: Attach the check-in to moments when users already open Pantry or look at it without being pushed: a home-screen widget showing tonight's dinner with a "cooked it" tap, the check-in shown when they open tonight's recipe to cook, and a one-tap "what did you eat this week?" link in the weekly planning email.

### Harvest frame

**Card:** ideas/random-entry.md › 7. Harvest frame
**Source:** Random Entry
**Technique:** Random Entry, random word: `honeycomb`
**Verdict:** ❌ Not adherent
**Note:** Keeping users who have already made it through the first month motivated with a visible, shareable record of the value they have built up: month-two engagement among retained users, not the early drop-off.
