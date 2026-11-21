---
name: plan-train-journey
description: Plan an Indian Railways train journey between two places on a date with RailCore. Use when someone asks which train to take, how to get from one Indian city or station to another by train, or wants trains with seats and fares for a date.
---

# Plan a train journey with RailCore

RailCore answers with live Indian Railways data. It cannot book, cancel or pay: tickets are booked on IRCTC (irctc.co.in or the IRCTC Rail Connect app).

1. If the person says "from home", "my usual class", "my usual quota" or "my usual route", call `get_my_preferences` first and use what it returns; if nothing is saved, ask. Only where RailCore's trip tools are available (the person allowed "See your saved trips"); otherwise ask. Never assume a saved preference the person did not refer to, and save one with `set_my_preferences` only when they ask.
2. Get the origin, the destination and the date. Names work ("Pune", "Mumbai", "Rajdhani"); words like "tomorrow", "Friday" or "kal" work too. If the class matters to the person and they have not said one, ask (SL, 3E, 3A, 2A, 1A, CC, EC, 2S).
3. Call `find_trains_between` with from, to and date. If it lists choices for a place name, ask the person which one.
4. Pick up to 3 trains that suit the person: departure time first, then duration, then trains that have their class. Say why each one fits in a few words.
5. For those trains, call `check_seat_availability` with one class each (the class the person wants). A seat check per class counts as one RailCore lookup.
6. Call `get_fare` for the train you recommend, in that class.
7. Recommend one train in two sentences: departure and arrival, availability with its `as_of` time, and the fare. Then list the others in one line each.
8. If every option is waitlisted, say so plainly and give the waitlist positions and confirmation chances the answers carry. Then call `find_confirmed_seats` for the train the person prefers, in their class: it tries a ticket from an earlier or to a later station on the same train, the day before and after, other classes and other trains (up to 12 seat checks, each one lookup), and says why each option works. Give its top options in one line each.
9. If the person asks whether trains will be crowded around a date or a festival, call `rush_signal`, and say it is an estimate.
10. End with where to book: IRCTC. Never say that RailCore booked, held or reserved anything.

Keep the answer short. Dates are in India time (IST); say which date each answer used. When the RailCore card or carousel appears, don't repeat everything it shows.
