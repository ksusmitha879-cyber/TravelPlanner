# TravelPlanner
# ✈️ Smart Travel Itinerary Planner

A comprehensive AI travel companion that drafts logical, day-by-day itineraries based on destination, budget, trip duration, and personal travel style — rendered as interactive collapsible day cards.

![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude%20AI-7F77DD?style=flat-square) ![Netlify](https://img.shields.io/badge/Deployed%20on-Netlify-00C7B7?style=flat-square)

---

## Demo

> **Input:** Destination: Kyoto. Days: 3. Budget: Low. Vibe: Historical & Quiet.
>
> **Output:**
> Day 1: Morning walk through Arashiyama Bamboo Grove (Free) → Lunch at a local udon shop ($) → Afternoon at Otagi Nenbutsu-ji Temple (quiet, less crowded) → Evening stroll along Philosopher's Path.

---

## Deployed Link - https://trav-plan.netlify.app

## Features

- Destination, duration (1–14 days), and budget selection
- 6 travel vibes — Historical, Nature, Foodie, Art & Nightlife, Relaxation, Family
- Structured JSON output rendered as interactive collapsible day cards
- Activities grouped by geographical proximity to minimize travel
- Estimated costs included per activity
- Local food recommendation every day
- Travel tips section
- Copy full itinerary to clipboard
- Dark mode support + mobile responsive

---

## Project Structure

```
06-travel-planner/
├── index.html
├── .gitignore
└── netlify/
    └── functions/
        └── generate.js
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [Netlify CLI](https://docs.netlify.com/cli/get-started/) — `npm install -g netlify-cli`
- An [Anthropic API key](https://console.anthropic.com/)

### Local Development

```bash
git clone https://github.com/yourusername/travel-planner.git
cd travel-planner
netlify login
netlify dev
```

Open [http://localhost:8888](http://localhost:8888)

### Environment Variables

```
ANTHROPIC_API_KEY=sk-ant-your-key-here
```

---

## Deployment

```bash
netlify deploy --prod
```

Add `ANTHROPIC_API_KEY` in **Netlify Dashboard → Site configuration → Environment variables**, then redeploy.

---

## How It Works

```
User enters destination, days, budget, and travel vibe
        ↓
index.html sends prompt requesting structured JSON response
        ↓
generate.js adds API key → forwards to Anthropic
        ↓
Claude returns a JSON object with title, days array, and tips
        ↓
JavaScript parses JSON and renders interactive collapsible day cards
```

---

## JSON Output Structure

Claude is prompted to return this exact structure:

```json
{
  "title": "3 Days in Kyoto",
  "destination": "Kyoto",
  "days": 3,
  "budget": "Low",
  "vibe": "Historical",
  "days_data": [
    {
      "day": 1,
      "title": "Ancient Temples & Bamboo",
      "schedule": "Morning: Arashiyama Bamboo Grove (Free)..."
    }
  ],
  "tips": "Buy an IC card for transport..."
}
```

---

## Prompt Template

```
Create a [Days]-day travel itinerary for [Destination].
Budget: [Budget]. Vibe: [Vibe].
Group activities by geographical proximity to avoid unnecessary commuting.
Return only valid JSON matching the specified structure.
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript |
| Icons | Tabler Icons |
| AI Model | Claude Sonnet (claude-sonnet-4-6) |
| Backend | Netlify Serverless Functions |
| Hosting | Netlify |

---

## License

MIT
