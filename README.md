# learn_daily-data

This repo holds **only runtime data** for the [learn_daily](../learn_daily)
app: `topics.json`, `deck.json`, `feedback_log.jsonl`, and generation state
under `state/`. No application code lives here — for the app itself (frontend,
Netlify Functions, generation pipeline), see the `learn_daily` repo.

This repo must remain **private**. It contains the user's personal learning
data (topics, flashcards, feedback history). The GitHub token used by
Netlify Functions to read/write this data is scoped to this repo only, so
keep that scope narrow if it's ever rotated or reissued.
