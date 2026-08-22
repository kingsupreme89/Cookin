# Cookin’ with B — App Concept Spec

## Overview
An app personalized by the user’s kitchen ingredients that turns what they already have into real meals, snacks, and desserts. Built to make meal prep feel less like a chore and more like discovery — while quietly educating users on nutrition along the way.

**Target users:**
- College students
- Busy moms
- Picky eaters / people with dietary restrictions
- Low-income families working with limited ingredients
- Chefs looking to expand their recipe repertoire

**Core value prop:** Reduce food waste, reduce decision fatigue, and make healthier choices easier — using only (or mostly) what’s already in the kitchen.

---

## Features & Navigation

### Tab 1: The Stash (Pantry)
Personalized digital pantry — the data source that powers the rest of the app.
- **Add items via:**
  - Manual entry (primary method)
  - Barcode scan (pulls item name + nutrition data via UPC lookup API)
  - Receipt photo scan — bulk-adds items, but requires a manual confirm/edit step afterward since OCR won’t always read item names correctly (especially on stores with abbreviated receipt printouts)
- **Nutrition info cards:** Tapping/selecting an ingredient shows a quick snippet of its nutritional benefits (e.g., “cilantro: high in vitamin K”). Pulled live from a nutrition API (e.g., Edamam or USDA FoodData Central), not hand-written.
- **Expiration tracking:** Users can log expiration dates. Items nearing expiration automatically flow into the Grocery List tab as a reminder/replacement prompt.

### Tab 2: Make a Plate
Uses Stash ingredients to generate meal, snack, or dessert ideas.
- **Two entry modes:**
  - Auto-generate — app builds a suggested meal from the full pantry, weighted to prioritize ingredients closest to expiring first, then fills in with the rest of the stash.
  - Select ingredients — user manually picks which stash items to build a dish around.
- **Filters:**
  - Sweet or savory
  - Snack, meal, or dessert
  - Prep time
- **Match mode toggle:** 
  - “Use what I have” (strict — only shows recipes fully covered by the stash)
  - “Willing to buy more” (partial match — shows recipes missing a few items, with those items able to be added to the grocery list)

### Tab 3: The Cook Out (Social Feed)
A feed where users share dishes they’ve made.
- Rate, review, and save dishes to favorites.
- Report/flag feature for moderation (inappropriate content, bad language, etc.)
- **Tapping a dish shows:**
  - Ingredients used
  - Prep time
  - Flavor profile (savory / spicy / sweet)
  - Ingredient match count against the user’s own Stash (e.g., “6/10 ingredients you have”)
- **Two action buttons:**
  - Save to Favorites (for later)
  - Cook Now — triggers an alert if ingredients are missing, with the option to add missing items directly to the Grocery List

### Tab 4: Grocery List
- Users manually add items they need.
- **Auto-populated with:**
  - Ingredients nearing expiration (as replacements).
  - Missing ingredients from a “Cook Now” or partial-match recipe selection.

### Tab 5: My Favorites (Personal Cookbook)
- Saves dishes the user wants to make next, or wants to keep as part of their own personal recipe collection.
- Pulls from both Make a Plate suggestions and Cook Out feed saves.

### Tab 6: Settings
- Add up to 5 people/profiles, each with:
  - Custom name
  - Allergy settings
  - Diet plan preferences
  - Language preference
  - Nutritional display information toggle (on/off)
- Push notifications for expiration date reminders.
- Share feature.

---

## Open Questions / Not Yet Decided
- Should allergy filtering be a hard block (recipe hidden entirely) or a warning (recipe shown with an alert)?
- Should Cook Out submissions require a photo, or is text-only allowed?
- What does onboarding look like for a brand-new user with an empty pantry? (e.g., starter templates, guided first-add flow)
- Recipe database sourcing: fully user-generated via Cook Out, a licensed third-party recipe API, or a hybrid of both?
- Monetization model (freemium, ads, premium tier) — not yet discussed.

---

## Technical Notes
- **Nutrition data:** Recommend Edamam or USDA FoodData Central API (both have free tiers).
- **Barcode lookup:** Standard UPC database APIs can handle item identification.
- **Receipt OCR:** Should be treated as “pre-fill and confirm,” not fully automatic, due to inconsistent item naming across store receipts.
