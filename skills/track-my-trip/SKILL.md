---
name: track-my-trip
description: Track an Indian Railways PNR with RailCore so the person gets alerts when its status, chart or platform changes, list the trips they track, or stop tracking one. Use when someone asks to watch, follow, track or get alerts for a PNR or a booked train trip.
---

# Track a trip with RailCore

RailCore's trip tools need the person's permission to see and change their saved trips. If a trip tool answers that permission is missing, tell the person their AI app will ask them to allow "See your saved trips" and "Save and remove trips"; then try again.

- **From a pasted ticket:** if the person pastes the IRCTC booking SMS or e-ticket text, call `read_ticket_text` to read the trip from it, then track or check the PNR from their message.
- **Track:** ask for the 10-digit PNR, then call `track_pnr` (optionally with a short label such as "Diwali trip"). Say where alerts go, using the answer's `alerts` (their email, and linked devices when there are any). If it was already tracked, say so. Someone can track up to 20 trips at once.
- **List:** call `list_my_trips` (add `include_past: true` when they ask about past trips). Give each trip in one line: label or train, date, from and to, latest status, and when it was last checked.
- **Watch a train without a PNR:** for someone picking a passenger up ("tell me when 12951 is 30 minutes from Borivali"), call `watch_train` with the train, the station, `when` (approaching with `minutes`, arrived or departed) and the day the train is at that station. Say where the alert goes; if the answer says it will not reach them, say how to turn alerts on. `list_my_watches` and `stop_watching_train` show and remove watches.
- **Stop:** call `stop_tracking_pnr` with the PNR or the `trip_id` from the list. If the answer says it wasn't tracked, say that rather than "stopped".

Never repeat a full PNR; say "PNR ending 789". RailCore only reads booking status: it cannot book, cancel or pay. Trips saved here also appear on railcore.tech under My trips, marked with the app they were saved from.
