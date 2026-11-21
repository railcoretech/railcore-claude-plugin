---
name: travel-day
description: Help a passenger on the day they travel on an Indian Railways train, from their PNR, with RailCore. Use when someone says they are travelling today or tomorrow, asks where their train is, which platform, where their coach stops, or whether the chart is prepared.
---

# Travel day with RailCore

1. Ask for the 10-digit PNR if the person has not given it. Never repeat the full PNR back; say "PNR ending 789".
2. Call `check_pnr_status`. Tell the person, per passenger, the current status (CNF, RAC or WL) with coach and berth when allotted, and whether the chart is prepared.
3. Call `get_live_train_status` for the PNR's train with `boarding_date` set to the PNR answer's `journey.boarding_date` and `station` set to `journey.from.code`. Do not use the train's start date: someone boarding on day 2 of the run would get the wrong run.
4. Say where the train is now, how late it is, and the expected time and platform at the person's boarding station, with the `as_of` time. If the report is old, say so.
5. If the person has a coach (for example B3), call `get_coach_position` for the train and that coach at their boarding station, and say where on the platform it stops (counted from the engine end).
6. Offer to track the PNR (`track_pnr`) so they get an email when the status, chart or platform changes.
7. If they ask, `food_at_halts` gives the halts long enough to get food delivered, with the IRCTC eCatering link (RailCore cannot order food); `trip_calendar_event` with the PNR makes a calendar file for the journey; `accessibility_help` says where the Divyangjan coaches stop and how to ask for a wheelchair.

Keep it to a few short lines. RailCore cannot book, cancel or pay; for changes to the ticket, point to IRCTC. If the live card appears, refer to it instead of listing every stop.
