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
