---
name: my-skill
description: Shows the weather forecast for Sofia, Bulgaria for the coming week. Use when the user asks about the weather in Sofia, next week's forecast, or invokes /my-skill.
---

# Sofia weekly weather

Fetch the 7-day forecast for Sofia (lat 42.6977, lon 23.3219) from Open-Meteo, which is free and needs no API key:

```bash
curl -s "https://api.open-meteo.com/v1/forecast?latitude=42.6977&longitude=23.3219&daily=weather_code,temperature_2m_max,temperature_2m_min,precipitation_sum,wind_speed_10m_max&timezone=Europe%2FSofia&forecast_days=7"
```

## Output

Present a compact table with one row per day:

| Day | Conditions | High / Low (°C) | Rain (mm) | Wind (km/h) |

- Use weekday names with dates (e.g. "Mon 23 Nov").
- Translate `weather_code` (WMO) to words: 0 clear, 1-3 partly cloudy, 45/48 fog, 51-67 drizzle/rain, 71-77 snow, 80-82 showers, 95-99 thunderstorm.
- Finish with one sentence summarizing the week (warmest/coldest day, any rain or snow days).
- If the request fails, say so and do not guess at the forecast.
