# Pluto

[![Chiroptical](https://img.shields.io/badge/twitch.tv-chiroptical-purple?logo=twitch&style=for-the-badge)](https://twitch.tv/chiroptical)

Pluto is a recursive acronym for "PLUto Twitch Overlay". The goal is to create
an open-source overlay with features similar to Streamlabs or Player.me.  The
overlay should be responsive via an API and handle new follows, subscriptions,
and bit donations.

I believe we shouldn't have to focus on the various Twitch APIs and their
authentication and instead work on interesting custom components with our
communities. Ideally, getting viewers involved when possible.

The backend of this application is coded using Haskell, Servant, and
Persistent. The frontend with Purescript and Halogen. The project is early work
in progress.

Next steps
---

- Finish pulling out `liftIO`s from `src/Api.hs` and other locations
- Store goals in metrics table on startup
- Provide endpoints to get goals
- Frontend should display subscribers, followers, and goals for each
- Figure out websockets to update frontend based on backend requests, e.g.
  first feature request

Feature Requests
---

- `curl -X POST /overlay?brb={true,false,toggle}&time=5` which will set, unset, or
  toggle some "Be Right Back" text.
  - Optionally, `brb=true&time=N` will show brb screen for `N` minutes
- Display snail emojis when chat enters snail emojis, i.e. get chat involved
- Respond to subscription, follow, and bit Twitch requests
  - Twitch sends `GET /...`, websocket communication to update Purescript

Questions
---

- Should we switch back to Beam using in `stack.yaml` in `extra-deps`?
  - An upsert command is now better supported

```
- git: https://github.com/haskell-beam/beam
  commit: <commit>
  subdirs:
  - beam-core
```
