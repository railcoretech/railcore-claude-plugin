# RailCore for Claude

RailCore answers Indian Railways questions with live and timetable data, in the conversation. Ask where a train is right now, which trains leave a station in the next few hours, or which trains run between two places on a date. Check seats and fares for a class, and when a class is waitlisted, see confirmed options from a nearby halt, another day, another class or another train. Find where your coach stops on the platform, check a PNR, track it for alerts, or watch a train to know when it reaches a station.

## What this plugin adds

- **The RailCore connector** at `https://mcp.railcore.tech/mcp`: the tools and cards (live train, station board, trains between stations, seat calendar, coach position, your trip).
- **Three skills** that teach Claude how to use them well:
  - `plan-train-journey`: trains between two places on a date, with seats and fares, and one recommendation;
  - `travel-day`: help on the day of travel from a PNR, including live status, platform and coach position;
  - `track-my-trip`: track a PNR for alerts, list tracked trips, or stop tracking one.

## Install

In Claude Code, this repository is also a plugin marketplace:

```
/plugin install railcore --marketplace railcoretech/railcore-claude-plugin
```

In the Claude apps, add `https://mcp.railcore.tech/mcp` as a custom connector (Settings, Connectors).

## Sign-in

The first time Claude uses RailCore it asks you to sign in with a RailCore account, which you can create during sign-in. You can disconnect Claude at any time on railcore.tech under Account, Sign-in and security, Connected apps.

## Good to know

- RailCore is independent and is not affiliated with IRCTC or Indian Railways. It cannot book, cancel or pay for tickets; tickets are booked on IRCTC.
- Live positions can lag a few minutes; every answer says when it was last updated (India time).
- Seat checks pause during IRCTC's nightly maintenance, about 11:45 PM to 12:20 AM IST.
- PNR checks are limited to 50 a day per account.

## Links

- How it works: https://railcore.tech/ai
- Privacy policy: https://railcore.tech/privacy
- Terms: https://railcore.tech/terms
- Support: https://railcore.tech/contact or hi@railcore.tech
