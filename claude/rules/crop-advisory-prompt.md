# Prompt Template: Crop Advisory Generation

```
Generate a crop advisory for <crop> in <region/season context>.

- Base guidance on established agronomic practice for the stated region
  and season; note when regional data is uncertain.
- Cover: irrigation timing, common risks this season, and any
  time-sensitive actions.
- Keep it actionable and concise — a farmer should be able to act on
  this without further research.
- Respond in the farmer's selected language (Hindi/English).
```

Use with weather/field context injected from `weather_logs` and `fields` where available.
