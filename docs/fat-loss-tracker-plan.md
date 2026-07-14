# Fat-Loss Nutrition Tracker — Product Plan

A plan for building a personal app that helps you lose fat effectively by (1) understanding you through an onboarding questionnaire, (2) tracking your food intake against personalized targets, and (3) telling you what to eat based on what's actually available to you.

---

## 1. The problem we're solving

Most tracking apps fail people trying to lose fat for three reasons:

1. **They track, but don't guide.** Logging 1,850 calories tells you nothing about what to eat *next*.
2. **They ignore your real food environment.** Recommendations assume you'll cook salmon and quinoa; real life is "what's in my fridge / near my office / on this menu."
3. **They ignore habits.** Fat loss fails at 9pm snacking, skipped breakfasts, and weekend blowouts — not for lack of a calorie number.

**This app's thesis:** personalize targets from a questionnaire, make logging nearly effortless, and answer the daily question *"given what I have available and what I've eaten today, what should I eat right now?"*

---

## 2. Product pillars

| Pillar | What it does |
|---|---|
| **Know me** | Onboarding questionnaire → personal calorie/protein targets, habit profile, food environment map |
| **Track me** | Fast intake logging (meals, weight, optional photos) with a running daily budget |
| **Guide me** | "What should I eat?" suggestions from *your* available foods, fitted to your remaining budget |
| **Coach me** | Weekly check-ins that adjust targets based on actual weight trend, and habit nudges tied to your stated weak spots |

---

## 3. The onboarding questionnaire

This is the heart of the app. It has five sections. Answers feed directly into the personalization engine (Section 4).

### Section A — Goals
1. What is your primary goal? *(Lose fat / Lose fat + keep muscle / General health)*
2. Current weight and height; age; sex (used only for energy-needs math).
3. Goal weight, or goal look/feel if you don't want a scale number.
4. How fast do you want to go? *(Gentle: ~0.25% bodyweight/week / Moderate: ~0.5% / Aggressive: ~0.75–1%)* — with a note that moderate is the sweet spot for keeping muscle and sanity.
5. Have you lost weight before? What worked, and what caused the regain?

### Section B — Body & activity
6. Typical daily movement: *(Desk-bound / On feet some of the day / On feet most of the day)*
7. Structured exercise: type, days per week, session length.
8. Do you lift weights or do resistance training? *(Strongly affects protein target and muscle retention.)*
9. Any injuries or medical conditions? (Flag: app gives general guidance, not medical advice — conditions like diabetes/thyroid/ED history should route to "talk to a professional" messaging.)

### Section C — Eating habits (the diagnostic core)
10. How many meals/snacks do you eat on a typical day, and roughly when?
11. When are you most likely to overeat? *(Late night / Weekends / Social events / When stressed / When bored / While cooking / Screen-time grazing)* — multi-select.
12. Liquid calories: sodas, juices, alcohol, sugary coffee drinks — how many per week?
13. Do you eat quickly? Do you finish others' plates? Do you eat until stuffed?
14. Which do you struggle with more: hunger between meals, or cravings for specific foods?
15. How often do you eat out or order in per week?
16. Who does the cooking and grocery shopping in your household?

### Section D — Food environment & preferences ("what's available to me")
17. Dietary pattern/restrictions: *(None / Vegetarian / Vegan / Halal / Kosher / Gluten-free / Allergies: ___)*
18. Foods you genuinely like that are protein-rich (checklist: eggs, chicken, fish, Greek yogurt, cottage cheese, tofu, beans, lean beef, protein powder, …).
19. Vegetables and fruits you'll actually eat (checklist).
20. What's typically in your kitchen right now? (This seeds your "pantry" in the app.)
21. What food sources are near your home/work? *(Supermarket / Corner store / Food court / Specific restaurant chains — free text.)*
22. Budget sensitivity: *(Eat cheap / Moderate / Not a constraint)*
23. Cooking skill and willingness: *(Won't cook / 10-minute meals max / Happy to cook)*

### Section E — Tracking style & support
24. How much logging effort will you realistically sustain? *(Full macros / Calories only / Simple "hand portions" & photo logging / Just meal check-ins ✓✗)*
25. How do you want to be nudged? *(Daily reminder / Only at my weak-spot times / Weekly summary only / No notifications)*
26. When will you weigh in? *(Daily morning — recommended, trend-smoothed / Weekly / Prefer measurements & photos instead)*
27. What does success look like in 12 weeks, in your own words?

### Re-assessment
A short 5-question version of this runs every 4 weeks: weight trend satisfaction, adherence self-rating, current struggle points, changes to schedule/food environment, energy/hunger levels. Answers re-tune targets and nudges.

---

## 4. How answers become a plan (the personalization engine)

1. **Energy target:** Estimate maintenance calories with Mifflin-St Jeor × activity factor (from B6–B7). Apply the deficit from A4 (e.g., moderate = maintenance − ~20%). Floor at safe minimums (~1,200 kcal women / ~1,500 kcal men) with a "slow down" warning if the goal pace demands less.
2. **Protein target:** ~1.6–2.2 g per kg of goal bodyweight, higher end if resistance training (B8). Protein is the #1 lever for satiety and muscle retention — the app treats it as the only macro that *must* be hit; carbs/fat are flexible.
3. **Meal skeleton:** From C10, build the day around when they already eat (don't force breakfast on a non-breakfast person). Allocate the calorie budget across those slots, weighting protein early in the day if late-night snacking was flagged (C11).
4. **Habit playbook:** Each C11 selection maps to one concrete tactic (e.g., late-night → "protein-forward evening snack pre-planned into your budget"; liquid calories → swap ladder: soda → zero soda → sparkling water). The app introduces **one habit change at a time**, every 1–2 weeks — never a list of ten rules.
5. **Food graph:** D17–D23 build a personal food database: pantry items, liked proteins/vegetables, nearby purchase options, budget and cooking constraints. Every suggestion the app ever makes is drawn from this set — never generic "eat more kale."
6. **Weekly auto-adjustment:** Compare 7-day average weight vs. expected pace. If loss stalls 2+ weeks with good adherence, trim ~100–150 kcal or add a step goal. If losing too fast or reporting low energy, add calories back. This closes the loop most apps leave open.

---

## 5. Core user flows

### Daily
- **Morning:** log weight (10 sec) → see trend line, not the noisy daily number.
- **Meal time:** open app → **"What should I eat?"** → app shows 3 options built from your pantry/nearby options that fit your *remaining* calories and protein gap → tap one to log it, or log something else.
- **Logging tiers** (from E24): full macro entry, calorie-only quick add, "hand portions" (palm of protein, fist of veg, cupped-hand carb, thumb of fat), or photo + ✓/✗ honesty check-in. Lower friction beats higher precision that gets abandoned.
- **Evening (if flagged as weak spot):** a single nudge at your stated risk time with your pre-planned snack.

### Weekly
- Weekly report card: weight trend, average intake vs. target, protein hit-rate, adherence streak, the one habit in focus.
- Grocery list generator: builds a shop from your liked foods + upcoming meal skeleton, sized to your budget setting.

### Monthly
- Re-assessment mini-questionnaire → targets and habit focus updated.

---

## 6. Feature list by priority

**MVP (must have)**
- Onboarding questionnaire (Sections A–E) with computed calorie/protein targets
- Daily food logging (calorie + protein minimum; hand-portion mode)
- Remaining-budget view ("you have 620 kcal and 40 g protein left today")
- Pantry list + "What should I eat?" suggestions filtered by remaining budget
- Daily weight log with 7-day trend line
- Weekly summary + automatic target adjustment

**V1.1**
- Habit nudges at user-declared weak-spot times
- Grocery list generator
- Restaurant mode: pick from saved nearby places, get the best-fit menu strategy ("grilled option + swap fries for salad ≈ 650 kcal")
- Barcode/label quick entry

**V2 (nice to have)**
- Photo-based meal estimation
- Food database API integration (Open Food Facts / USDA FoodData Central) for accurate macros
- Social/accountability sharing
- Wearable import for activity (HealthKit)

---

## 7. Data model (first pass)

```
UserProfile      — demographics, goal, pace, activity, dietary flags, tracking style
Targets          — calories, protein, meal skeleton; versioned (each weekly adjustment = new row)
HabitProfile     — weak spots (from C11), current focus habit, nudge schedule
PantryItem       — name, category, protein-rich?, est. macros, source (home/near work/restaurant)
FoodLog          — timestamp, items or portion-units or photo ref, kcal, protein, meal slot
WeightLog        — date, weight; derived: 7-day rolling average
CheckIn          — weekly/monthly re-assessment answers
Suggestion       — generated option, accepted?, timestamp (to learn what you actually pick)
```

---

## 8. Build path (iPad-friendly, phased)

You're on an iPad, so the plan avoids anything that requires a heavy local dev setup, and gets you *using the system* before any code exists.

### Phase 0 — Paper prototype, this week (no code)
Run the system manually to validate it before building anything:
1. Put the Section A–E questionnaire into **Google Forms** (works great on iPad); answer it yourself.
2. Compute your targets once using the rules in Section 4 (this can be done in the form's linked Google Sheet).
3. Track for 2 weeks in a **Google Sheet or Apple Notes**: weight each morning, meals with rough calories/protein, and a ✓/✗ for your one focus habit.
4. Keep a running "pantry" note and, at each meal, consciously pick from it against your remaining budget.

*Why:* two weeks of manual use will reveal which logging tier you'll actually sustain (E24) and which features matter — before a line of code.

### Phase 1 — Web app MVP (PWA)
- **Stack:** single-page web app — React (or plain HTML/JS to start) + local storage or Supabase for sync; installable as a PWA so it sits on your iPad/iPhone home screen like a native app. No app store needed.
- **Where it's built:** in this repo, developed via Claude Code on the web / GitHub Codespaces — all workable from the iPad. Deploy free on GitHub Pages (static) or Vercel (if a backend is added).
- **Scope:** the MVP list from Section 6. Suggestions engine starts as simple filtering: `pantry items → fits remaining kcal → maximizes protein gap → rank by your past picks`.

### Phase 2 — Smarter guidance
- Hook in Open Food Facts / USDA FoodData Central for real macro data.
- Restaurant mode with saved nearby spots.
- Automatic weekly target adjustment from weight-trend math.
- Optional: an LLM-powered "coach" endpoint that turns the week's data into a short natural-language review and next-week focus.

### Phase 3 — Native polish (only if PWA limits hurt)
- HealthKit weight/activity sync, better notifications → wrap as an iOS app (Capacitor) or rebuild in Swift.

---

## 9. Success metrics

- **Adherence:** ≥80% of days with at least a check-in logged (the #1 predictor of outcome).
- **Outcome:** weight trend within ±25% of chosen pace over any 4-week window.
- **Protein:** hit protein target ≥5 days/week.
- **Friction:** logging a meal takes <30 seconds.
- **Guidance uptake:** ≥30% of meals come from an accepted "What should I eat?" suggestion.

---

## 10. Guardrails

- The app gives general nutrition guidance, **not medical advice**; onboarding flags medical conditions and any history of disordered eating and softens/redirects accordingly (no aggressive deficits, no red "over budget" shaming states — the day is scored on adherence, not perfection).
- Hard calorie floors; pace capped at ~1% bodyweight/week.
- Missed days are treated as neutral, never punished — streaks count check-ins, not perfect eating.

---

## Next steps

1. Review/edit the questionnaire wording above.
2. Stand up the Phase 0 Google Form + tracking sheet.
3. After ~2 weeks of manual use, start Phase 1: scaffold the PWA in this repo (questionnaire screen → targets calculator → daily log → pantry + suggestions).
