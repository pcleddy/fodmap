# FODMAP Recipes

A clean, minimal web app for browsing 45 FODMAP-friendly, spicy recipes from around the world.

**Live:** https://pcleddy.github.io/fodmap

## Features

- 45 recipes across Thai, Indian, Japanese, Chinese, Korean, Indonesian, Mediterranean, and Guam cuisines
- All recipes are low-FODMAP (no garlic/onion, ginger-forward)
- Vegan and non-vegan options
- Spice levels: mild → very hot
- Filter by ingredient and cuisine
- Expandable/collapsible ingredient and instruction sections

## Recipes Included

**Thai:** Pad Thai, Tom Yum, Panang Curry, Pad Krapow, Som Tam, Green Curry
**Indian:** Chickpea Curry, Tofu Vindaloo, Chana Masala, Tandoori Fish, Chicken Tikka Masala, Sambar, Instant Pot Masala
**Japanese:** Okonomiyaki, Yakitori, Miso Ramen, Gyudon
**Chinese:** Hot Pot, Mapo Tofu, Kung Pao Chicken, Dan Dan Noodles, Chongqing Chicken
**Korean:** Bibimbap, Tteokbokki, Bulgogi, Dakgangjeong, Kimchi Fried Rice
**Indonesian:** Rendang, Gado-Gado, Satay, Sambal Oelek Stir-Fry
**Mediterranean:** Salmon, Cod, Halibut, Roasted Chicken, Quinoa Salad
**Guam:** Red Rice, BBQ Chicken, Spicy Shrimp
**Asian:** Stir-fries, Fried Rice, Rice Bowls, Shrimp

## Setup

### Local Testing

The app loads recipes dynamically from `recipes.json`. Local `file://` URLs don't support `fetch()` due to CORS, so use a local server:

**Python 3:**
```bash
python3 -m http.server 8000
```

**Python 2:**
```bash
python -m SimpleHTTPServer 8000
```

**Node:**
```bash
npx http-server
```

Then visit `http://localhost:8000`

### GitHub Pages Deployment

1. Create a new repo: `gh repo create fodmap --public`
2. Clone it: `gh repo clone fodmap && cd fodmap`
3. Add both files:
   ```bash
   cp /path/to/index.html .
   cp /path/to/recipes.json .
   ```
4. Commit and push:
   ```bash
   git add index.html recipes.json README.md
   git commit -m "Add FODMAP recipe app"
   git push -u origin main
   ```
5. Enable Pages in repo settings → Pages → Deploy from main branch → Save

Your app will be live at: `https://yourusername.github.io/fodmap`

## File Structure

```
fodmap/
├── index.html       # UI + JavaScript (loads recipes dynamically)
├── recipes.json     # All 45 recipes with ingredients & steps
└── README.md        # This file
```

## How It Works

- `index.html` fetches `recipes.json` on page load
- Recipes render dynamically in JavaScript
- Click any recipe in the sidebar to view details
- Ingredients and instructions sections expand/collapse

## Customization

### Add a Recipe

Edit `recipes.json` and add an entry:

```json
{
  "id": 46,
  "title": "Your Recipe Name",
  "cuisine": "Cuisine",
  "servings": 2,
  "time": 30,
  "vegan": true,
  "spice": "medium",
  "ingredients": [
    { "name": "ingredient", "amount": "1 cup" }
  ],
  "steps": [
    "Step 1",
    "Step 2"
  ]
}
```

### Change Styling

Edit the `<style>` block in `index.html`. Colors, fonts, layout are all CSS variables.

## FODMAP Guidelines

These recipes avoid:
- Garlic and onions (use ginger as substitute)
- High-fructose fruits
- Wheat (uses tamari instead)
- Most legumes (chickpeas in moderation)

All recipes use **garlic-infused oil** or **ginger** for flavor instead of fresh garlic/onion.

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires ES6 JavaScript support.

## License

Public domain — use freely, modify as you like.
