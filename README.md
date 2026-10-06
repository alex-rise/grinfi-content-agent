# Content Agent for Claude Code

A content team in one folder. It meets your business, mines what you have
already said into material, writes posts in your own voice, makes the images,
schedules them through your own Buffer account and reads the numbers back.

It runs inside Claude Code. It keeps what it learns about you in plain text
files you can read, and it publishes nothing without your yes.

## Why this exists

Post generators write badly for four reasons, and all four are fixable:

1. **No facts.** They write what is true of every company in your industry,
   because that is all they were given. Your numbers, your thresholds and the
   thing you learned the hard way are what makes a post worth reading.
2. **No raw material.** You have already explained your work a hundred times -
   in calls, webinars, replies to clients. That is the content. A generator
   starts from a topic instead, so it produces topics.
3. **No voice.** Your hedges, your blunt word for bad work, your own names for
   things. Strip those and the text reads like a brochure about you.
4. **No measurement.** Nothing comes back, so nothing improves. Month three
   reads exactly like week one.

This kit is built around those four. Most of the work happens before a single
sentence is written.

## Install

You need [Claude Code](https://claude.com/claude-code). Then:

```bash
git clone https://github.com/alex-rise/grinfi-content-agent.git content-agent
cd content-agent
claude
```

Then say: **set me up**.

That is the whole installation. The agent reads this folder, asks you about
your business, creates the folders for your material and tells you what to
drop where.

## The first hour

1. **It asks about your business** - who buys, what they compare you to, what
   you prove it with. Fifteen to twenty minutes of talking, no forms.
2. **It reads what is public** - your site, your blog, your profile - before
   asking you anything it could find itself.
3. **It creates your folders** and tells you, in one message you can forward,
   what to put in each one.
4. **It writes two posts** from what it already has, and marks honestly where
   a fact is missing instead of inventing one.
5. **You read them out loud.** Where a word is not yours, you say so, and it
   goes into your voice file so the next text does not repeat it.

## What it needs from you

Three things, and only the first is urgent:

- **One recording of you explaining your work.** A client call, a consultation,
  a webinar - thirty minutes is plenty. This is where your voice comes from.
  Without it the texts are correct and neutral, which is the same as forgettable.
- **Twenty five to thirty photographs of you.** Phone is fine, studio is not
  needed, vertical is best. At work, in a meeting, with your team.
- **A yes on every text.** The agent prepares and queues. A human says go.

## What it will not do

- **Publish without your approval.** Ever, on any channel.
- **Invent a case, a number or a quote.** If a fact is missing it asks you or
  leaves the gap visible.
- **Video and dubbing.** Out of scope for now: text and images only.
- **Ask for your social network passwords.** You connect your own channels in
  Buffer yourself; the agent never needs your logins.

## Channels

Scheduled through your own Buffer account: LinkedIn (personal profile and
company page), Threads, X, Instagram, Bluesky, Mastodon, Facebook **Pages**,
Google Business Profile, Pinterest.

Two honest exceptions:

- **A personal Facebook profile cannot be scheduled by anything.** Meta does
  not allow third-party publishing to profiles, only to Pages. If a personal
  Facebook line matters to you, the agent writes it and you paste it.
- **Video channels** (TikTok, YouTube) are connectable, but this kit does not
  make video yet.

## Publishing: your own Buffer

You pay Buffer, not us, and you keep control of the accounts.

- **Free plan:** 3 channels, 10 scheduled posts per channel, refillable. Enough
  to start on one profile.
- **Essentials:** $5 per channel per month ($60 a year per channel).
- **The API is on every plan, including free.** The agent uses it to queue
  posts and to read results. The free quota is 3,000 requests a month, which is
  far more than publishing needs.

Setup is one page: the `publishing` skill walks you through connecting your
channels and creating the key, and tells you what to do if you would rather not
give the agent a key at all.

## What lives where

| Folder | What is in it |
| --- | --- |
| `.claude/skills/` | the work itself: onboarding, mining, planning, writing, visuals, publishing |
| `reference/` | per-platform forms, the materials rules, and two tested image templates: single images and carousels |
| `examples/` | finished posts with the image brief for each, to see the level |
| `business/` | **your** business: facts, voice, channels, material, results. Never leaves your machine - it is outside git |

## The order of work

```
meet the business → collect the raw material → mine it into cores
   → facts and voice → plan the week → write → image → your yes → queue → measure
```

Skipping the first three is what makes the rest read like everyone else.

## Licence and provenance

Built by the team behind [Grinfi](https://grinfi.io),
[Lead Finder](https://finder.grinfi.io) and [Telegrin](https://tg.grinfi.io),
out of our own publishing and our clients' - the same way our
[outbound kit](https://github.com/alex-rise/grinfi-outbound-agent) was built.
MIT: take it, change it, use it for your clients.
