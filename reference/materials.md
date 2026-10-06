# Materials: where the client puts things, and how we find them

The goal is that the person never has to ask "where do I put this", and that in
three months you know what you have without opening a folder.

The rule the whole file rests on:

> **The bytes live in storage, the knowledge about them lives in text.** A file
> that is not in the catalogue does not exist: nobody will find it or remember it.

## One folder, four boxes

Make **one** shared folder in whatever cloud the client already uses - Drive,
Dropbox, OneDrive, it does not matter, what matters is that they already go there.
Four subfolders inside, and no more:

| Folder | What goes in | How much we expect |
| --- | --- | --- |
| `Inbox` | anything at all, unsorted: dropped and forgotten | continuously |
| `Photos` | real photographs of the face of the brand and the team | 25-30 of them, 10-15 of each second speaker |
| `Product` | screenshots, interfaces, dashboards, drawings, photos of the work | as they appear |
| `Recordings` | calls, webinars, talks, voice notes | everything there is |

`Inbox` is the most important of the four. People will not sort. Requiring them to
is the reliable way to receive nothing.

## The message to the client, ready to send

> I have made a folder, link below. Anything that comes to hand and relates to the
> work - drop it into Inbox without sorting: photos, screenshots, recordings of
> calls, voice notes, other people's posts you liked. I will sort it.
>
> Two separate asks. First, 25-30 real photographs of you: at work, in a meeting,
> travelling, with the team. Phone is fine, studio is not needed, vertical is best.
> The less staged, the better it works.
>
> Second, a recording of one half-hour conversation where you explain your work - a
> client call, a consultation, anything. This is what makes the texts sound like
> you rather than like us writing about you. Without it I can write correctly, and
> correct is the same as forgettable.

## File names

The name is given by whoever puts the file there, and it is never corrected
afterwards: by then something already links to the old name.

```
YYYY-MM-DD-what-it-is.ext
2026-10-06-warehouse-line.jpg
2026-09-18-client-call.m4a
```

The date is when it was taken or recorded, not when it was uploaded. Latin
letters, hyphens, no spaces: spaces break links and commands.

## The catalogue

Every accepted file gets a line in `business/clients/<client>/materials.md`: name,
where it is, what is on it, when it was taken, where it has been used. The line is
written by whoever accepted the file, in the same session.

| File | Where | What it is | Taken | Used in |
| --- | --- | --- | --- | --- |
| `2026-10-06-warehouse-line.jpg` | Drive, `Photos` | him at the line, in a hard hat, profile | 06.10 | the post on lead times, 12.10 |

Why bother, when the folder can simply be opened: a second machine and a future
marketer cannot see the folder but can read the text - and the "used in" column is
how you notice that one photograph has appeared four times this month.

## What never goes into the repository

- **Raw recordings and transcripts with names.** Other people's personal data.
  They stay in storage and in a local folder outside git; the repository holds the
  mining and a catalogue line.
- **Photographs of people.** Only finished post images belong in a repository.
- **Other people's interfaces with real names and sums.** Replace names with
  invented ones and sums with figures of the right order but not the real ones. Ask
  permission for every screenshot that shows somebody's client.
- **Credentials.** Keys and passwords live in a secrets store, never in the
  materials folder and never in a chat thread. If a client pastes a password into
  chat, ask them to rotate it.

## What we never ask a client for

- **Their social network logins.** Publishing goes through a scheduler they connect
  themselves; you never need access to the account.
- **Retouched photographs.** They send what they have.
- **Draft posts.** They give facts and recordings; the text is your job. If a
  client has started writing drafts, you asked too few questions.
- **Sorting and labelling files.** Only dropping them into Inbox.

## When there are no materials at all

Normal for the first fortnight, and not a reason to wait.

1. Write text, and make images from diagrams and quotes on the brand background
   (`visuals` skill) - those need no photographs at all.
2. On every call, name **one** specific missing thing, not a list of ten. A list
   reliably brings nothing.
3. The easiest thing to get is what already exists: a recording of an old webinar,
   a screenshot of their working screen, photos from their phone from last month.
   Start there.
