---
name: mining
description: Use when there is a recording, transcript, webinar, podcast, client call, article or support thread to turn into material, or when the user says here is a recording, mine this, make cores, or asks for posts and the client folder has no sources yet.
---

# Mining recordings into cores

Input: anything where the person has already spoken in their own words. Output:
one file of cores per recording, plus the list of what must never be published.

This is the most underrated step in the whole kit. A generator starts from a
topic, so it writes the general case. You start from what the person has already
said, so the text contains things nobody outside the company knows.

## What counts as raw material

In descending order of value:

1. **A recording where they explain something to a colleague or a client.** A
   call, a consultation, a demo, a post-mortem. Here they talk the way they
   think, not the way they write.
2. **Webinars, podcasts, conference talks.** The same, with the audience in mind,
   so a little smoother.
3. **Their own articles and posts.** Facts and positions yes; voice only their
   written voice.
4. **The edits they made to your drafts.** Written voice again, but the most
   precise kind: every word they replaced goes into `voice.md` as before → after,
   and every pattern they struck out twice goes into their own stop list.
5. **Client threads and support.** This is where objections and the exact wording
   of the pain live.
6. **An automatic meeting recap** (a notetaker, meeting notes). Useful as an
   index. **Not a source of facts** - see the rule below.

Nothing from the first two categories? Ask for one thirty-minute recording where
they answer the onboarding questions. It is cheaper than six months of neutral
text.

## A meeting recap is not a transcript

Measured on a real client. The first drafts were built on a notetaker's summary
of a call. Then the full verbatim transcript of the same call arrived, and:

- **the recap had invented a case that was never said** - with an industry, a
  city and a timeframe. It read like a fact. It would have been published;
- **the recap had flattened the person's rule into a scare.** In the recording he
  had two different thresholds and his own caveat, "not everyone needs this". The
  caveat was the most convincing thing he said, and the recap had dropped it;
- **there is no voice in a recap at all.** It writes in flat machine prose. From
  it you cannot tell one founder from another.

So, two rules that are not up for discussion:

> **Any fact that will be published is checked against the verbatim transcript.**
> A recap is good for finding the timecode and knowing what was discussed.

> **Voice is only ever taken from verbatim speech.** No transcript, no voice
> file: write neutrally and say out loud what is missing.

Transcripts are free: `yt-dlp --write-auto-subs --sub-langs "en-orig,en"
--sub-format json3` for public video, the meeting service's own export for calls.
One minute of work, and it is the line between this kit and a generator.

## Two passes over one recording

One pass does not work: hunting facts and hunting speech notice different things.

**Pass one, facts.** What do they assert, with which numbers, what do they
describe as a mechanism rather than an opinion. Output: cores.

**Pass two, speech.** How they say it: the turns of phrase that repeat, the
hedges, the blunt words, their own names for things, what is absent from their
speech entirely. Output: `voice.md`.

## The shape of a core

One file per recording: `business/clients/<client>/sources/YYYY-MM-DD-what.md`.
A header (what the recording is, how long, who spoke, where the file itself
lives) and then the cores. A thirty to forty minute recording yields eight to
twelve cores, which make four to six posts.

```
## C7. Onboarding went from two weeks to three days
- Timecode: [29:17]
- Type: case · Verdict: take it, do not name the company

Verbatim: "..."

One or two lines: why this is a strong core and what is missing from it.
```

**Type** - case, measurement, position, mechanism, advice, tool. The week is
assembled by type later: three positions in a row and no case is a bad week.

**Every core carries a verdict**, one of four:

- **take it** - the fact is theirs, permission exists or is not needed;
- **check** - strong, but needs their yes or a number confirmed;
- **hold** - true, but the occasion has not arrived;
- **never** - not publishable, and repeated in a list at the end of the file, so
  that the next session does not find it mid-file and mistake it for material.

A core without a verdict is rubbish: in a month nobody remembers whether it may
be printed.

## Three checks before "take it"

**1. Anonymised is not the same as unrecognisable.** Stack the identifying
details: industry plus size plus one unusual fact, and the client's own partners
know exactly who it is. The shape of the mistake: "a logistics company" is safe,
while "a logistics company running a four-person night shift out of a single
regional depot" is a name with the name removed. Drop the most characteristic
detail even when it is the one that makes the text sing - and when you cannot
tell whether the stack identifies them, that is what asking them is for.

**2. Whose case is it.** Their client, their acquaintance, or something they read
somewhere - three different sets of rights. They can give permission about their
own client, not about a friend. If the recording does not make it clear, the
verdict is "check", not "take it".

**3. Did they promise this publicly or to you.** A free service offered inside a
sales call and the same offer in a post read by three thousand people are
different sizes of commitment. Those are always "check".

## What to preserve in a quote

- **Hedges are content, not noise.** "Most likely", "I think", "usually", "give
  or take" mark where knowledge ends and guessing starts. Straighten them out and
  the text reads like somebody else's marketing.
- **An admitted "I do not know" is worth more than another argument.** If they
  said "honestly, I do not know why they agreed", that goes in verbatim.
- **A number as a threshold, not an adjective.** "From fifty thousand installs",
  "a month or two without a release", "twenty or thirty gyms" - that is how they
  think. They do not say "significantly", so neither do you.
- **One blunt word per topic.** Every practitioner has a word for bad work. It is
  what separates them from any other vendor, and it must not be tidied.
- **Their own vocabulary.** Keep their names for working things as they are; in
  translation, match the register, not the dictionary.

## What mining never does

- **No paraphrase in place of the quote.** Verbatim first, your summary on a
  separate line beneath it.
- **No completing their logic.** A gap in the reasoning is a question for them,
  not a place for your guess.
- **No discarding contradictions.** If they say three months in one place and six
  in another, they have two thresholds for two situations - and that is the
  knowledge worth money.
- **No cleaning up the swearing or the hedges in the source.** You clean the post,
  never the core.

## Where the recording itself lives

Raw recordings and transcripts with names stay **out of the repository**: they are
other people's personal data. The repository holds the mining and a line in the
materials catalogue saying where the file is. The rule is in
`reference/materials.md`.

## End with the holes

Every mining file ends with a list of what is missing: which number, which case
is unconfirmed, whose voice has not been captured. That list is the agenda for
the next call with the client, and it is also the honest explanation of why the
first texts are more careful than the later ones.
