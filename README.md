# Pawcast 🐾
Your dog's official weather advisory service. A weather app where your dog diagnoses your mood and tells you when to go for a walk. Real weather data, very unserious energy.

**Try it:** [pawcast.up.railway.app](https://web-production-95675.up.railway.app)

<img width="300" height="600" alt="pawcast" src="https://github.com/user-attachments/assets/fc945ade-42df-46ab-bb26-ad5bd827c63d" />

---

## Why this exists
I wanted to learn FastAPI and needed a project that wasn't another to-do app. A dog-powered weather advisory service felt like a reasonable alternative.

---

## Try it yourself
**You'll need:** Python 3.11+ and a free [OpenWeatherMap API key](https://openweathermap.org/api)

```bash
git clone https://github.com/your-username/pawcast.git
cd pawcast
pip install -r requirements.txt
cp .env.example .env
# then open .env and add your API key
python -m backend.main
```

Open `http://localhost:8000` — the backend serves the frontend directly, no separate step needed.

---

## Customize it

**Add a new mood** — add a scoring function in `mood_engine.py`, the copy in `mood_content.py`, and a matching card in `index.html`.

**Change the text** — everything visible (landing page, quiz labels, testimonials) lives in `index.html`.

**Deploy your own** — push to Railway or anything that runs Python. Set `OPENWEATHERMAP_API_KEY` and update `API_BASE` in `index.html` to your URL.

---

## How it's built

Vanilla JS/HTML frontend, no build step. FastAPI backend that scores hourly weather slots based on whatever mood you pick. City search uses Nominatim (OpenStreetMap) — no extra API key needed.

```
pawcast/
├── index.html               # entire frontend
├── backend/
│   ├── main.py              # FastAPI app
│   ├── models.py            # request/response models
│   ├── routers/             # /walks and /weather endpoints
│   └── services/            # weather fetching + mood scoring logic
├── Procfile                 # Railway config
└── requirements.txt
```

---

## Known quirks

OpenWeatherMap's One Call 3.0 isn't always available on free tier — it falls back to the 5-day forecast automatically, so results still work either way.
