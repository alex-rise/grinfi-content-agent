---
name: publishing
description: Use when connecting Buffer, queueing posts, setting a publishing schedule, or reading results back - and when the user says connect Buffer, schedule this, put it in the queue, when does it go out, or how did the last posts do.
---

# Publishing: their Buffer, their channels, their yes

The person you work for pays Buffer and owns the accounts. You never ask for a
social network password. They connect their channels inside Buffer themselves,
and you work through the API with a key they create.

## What it costs them

- **Free:** 3 channels, 10 scheduled posts per channel, refillable. Enough for one
  profile and the first month.
- **Essentials:** $5 per channel per month, $60 a year per channel.
- **The API is on every plan, free included.**

API quotas, which publishing never comes close to:

| | Free | Essentials | Team |
| --- | --- | --- | --- |
| API keys | 1 | 3 | 5 |
| Requests / 15 min | 100 | 100 | 100 |
| Requests / 24 h | 250 | 250 | 500 |
| Requests / 30 days | 3,000 | 7,500 | 15,000 |

## Connecting it, in the order that works

1. **They connect the channels** at buffer.com: LinkedIn profile and company page,
   Threads, X, Instagram, Bluesky, Mastodon, Facebook Pages, Google Business,
   Pinterest. Authorising is done in their own browser, with their own logins.
2. **They create an API key** at `https://publish.buffer.com/settings/api` and
   paste it to you once.
3. **You store it in `.env` in this folder**, as `BUFFER_TOKEN=...`, and `.env` is
   never committed and never repeated back in chat. If they paste it into a group
   chat, tell them to rotate it.
4. **You list their channels** and write the channel ids into their
   `channels.md`, so later sessions do not have to ask again.

**If they would rather not hand over a key at all, that is a legitimate choice.**
Then you write the finished texts and images into a file by date and time, and they
paste them. Everything else in the kit works the same. Do not argue about it.

## Two honest limits

- **A personal Facebook profile cannot be scheduled by any tool.** Meta does not
  allow third-party publishing to profiles, only to Pages and groups. If a personal
  Facebook line matters, you write it and they paste it.
- **Instagram and some others may publish by notification** rather than
  automatically. That means Buffer pushes a reminder to their phone at the
  scheduled minute and they tap publish. Say this out loud when you set the
  schedule, or they will think it failed.

## The API, concretely

It is GraphQL. One endpoint, `https://api.buffer.com`, POST, with
`Authorization: Bearer <token>`.

List the channels:

```bash
curl -s https://api.buffer.com \
  -H "Authorization: Bearer $BUFFER_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query":"{ account { organizations { id name channels { id service name } } } }"}'
```

Queue one post:

```bash
curl -s https://api.buffer.com \
  -H "Authorization: Bearer $BUFFER_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query":"mutation { createPost(input: { text: \"...\", channelId: \"CHANNEL_ID\", schedulingType: automatic, mode: customScheduled, dueAt: \"2026-10-13T09:00:00.000Z\" }) { ... on PostActionSuccess { post { id } } ... on MutationError { message } } }"}'
```

Fields that matter: `text`, `channelId`, `schedulingType` (`automatic` or
`notification`), `mode: customScheduled`, `dueAt` in ISO 8601 UTC. The response is
either a success with the post id or an error with a message - read the message and
say it in plain words, never "something went wrong".

Check the current shape at `https://developers.buffer.com/` before a first setup:
this is their API and it moves.

## The approval gate

**Nothing is queued before the human whose name is on it has said yes.** Not a
draft in their account, not "it is only scheduled, we can still cancel".

The order is always: text and image ready → they read it, ideally out loud → they
say go → you queue it → you tell them the date, the time and the channel in one
line. The queue is visible in their Buffer, so they can still change their mind,
and that is the point: you are not the only brake.

## Rhythm

- **Three posts a week per channel to start.** More than that and the approval
  queue backs up, which is what actually kills content programmes.
- **One fixed hour**, matched to where the audience is, not where the author is.
- **Do not publish to every channel in the same hour.** The same person following
  two of them sees a broadcast.
- **The first hour after publishing is work, not waiting.** Comments get answered
  then: platforms count comments above likes, and replies pull the post back into
  circulation.
- A post that is late is not published at the wrong hour - it moves to the next
  slot. There are no urgent posts.

## Reading the numbers back

A week after publication, pull what the platform gives - impressions, reactions,
comments, profile visits, follows - and write them into `what-works.md` for that
client, one line per post with its type and its first line.

Once a month, read their own best ten percent of the last ninety days and find the
one or two traits all of the best ones share. Carry those into the next month.
Do not analyse the bottom eighty percent.

What to tell the client monthly, in three lines: what got the most response and
why you think so, what got the least, and what you are changing next month. Not a
dashboard. Three lines.
