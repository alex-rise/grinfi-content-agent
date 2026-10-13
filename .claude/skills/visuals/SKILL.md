---
name: visuals
description: Use when a post needs an image, a carousel, a diagram, a number card or a checklist card - and when the user says make the picture, what image goes with this, make a carousel, or asks what to photograph.
---

# Images: what goes with the text

An image is needed every time: across every profile we read, posts without one
collected less. But an image is not decoration - each type has a job.

## Five types, and when each one

| Type | When | What is on it |
| --- | --- | --- |
| **A real photograph** | personal story, position, ordinary post | the person writing: at work, on stage, travelling. With or without a headline bar |
| **A number** | a measurement | one figure, large, and one line saying what it means |
| **A diagram** | a mechanism, a process, a timeline | three to five blocks with arrows, no more |
| **A checklist** | advice | four to six items, each one line |
| **A screenshot** | a tool, a case | a real screen, with names and sensitive data replaced |

**A carousel** is a separate format rather than an image for a post: a
step-by-step teardown, a listicle, "ten things that". It outperforms a single
image wherever there is an enumeration.

## Rules for all of them

- **Real photographs, not stock and not AI-generated.** A stock image on a
  personal profile reads as somebody else's, and it is noticed immediately.
- **One style across the whole stream:** one accent colour, one typeface, the logo
  in the same place every time. Different content, identical dress - that is how a
  feed becomes recognisable by the third post.
- **Little text on the image.** A headline of four to eight words, some words in
  the accent colour. Everything else belongs in the post.
- **Readable on a phone.** The test: shrink it to thumbnail size. If the headline
  is unreadable, it is too small.
- **Never cover the face.** The bar goes above or below the head.

## Carousel

- Five to eight slides. Beyond that people stop swiping.
- **The first two slides are the hook.** The platform shows a carousel a second
  time starting from slide two, so slide two has to work on its own.
- One slide, one thought: a simple image and one or two sentences.
- The last slide is an action: what to do, or what to write in the comments.

`reference/carousel-template.html` builds the whole thing. Edit the `SLIDES` array -
each slide is `cover`, `text`, `number` or `steps` - and render **both** outputs
from the same file:

```bash
# LinkedIn document post: one PDF, all slides, one command
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless \
  --disable-gpu --no-pdf-header-footer --print-to-pdf=carousel.pdf \
  "file://$PWD/reference/carousel-template.html"

# Instagram: one PNG per slide
for n in 1 2 3 4 5 6; do
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless \
    --disable-gpu --screenshot=slide-$n.png --window-size=1080,1350 \
    --force-device-scale-factor=2 --hide-scrollbars \
    "file://$PWD/reference/carousel-template.html?slide=$n"
done
```

LinkedIn takes the PDF as a document post. Instagram takes the PNGs as a gallery.
Same slides, two formats, no design tool and no manual assembly.

The footer carries "swipe →" on every slide but the last, which carries the handle:
that is deliberate, it measurably holds people through the middle slides.

## Sizes

| Where | Size |
| --- | --- |
| Professional feed, vertical post | 1200×1500 (4:5) |
| Square for short feeds | 1080×1080 |
| Carousel | 1080×1350, PDF |
| Chart or diagram in the feed | 1200×675 |

A vertical image takes more of a phone screen, so the feed gets 4:5 rather than a
square.

## How to actually make one, with no designer

`reference/image-template.html` is a template with four layouts: a number, a
checklist, a diagram and a headline over a photograph. Edit the text and the two
brand variables at the top of the file, then render:

```bash
# macOS
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --screenshot=out.png \
  --window-size=1200,1500 --force-device-scale-factor=2 \
  --hide-scrollbars --default-background-color=00000000 \
  "file://$PWD/reference/image-template.html?layout=number"

# Linux
google-chrome --headless --disable-gpu --screenshot=out.png \
  --window-size=1200,1500 --force-device-scale-factor=2 --hide-scrollbars \
  "file://$PWD/reference/image-template.html?layout=number"
```

```powershell
# Windows (PowerShell). Edge works with the same flags:
# "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe"
$page = "file:///" + ($PWD.Path -replace '\\','/') + "/reference/image-template.html?layout=number"
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --headless --disable-gpu `
  --screenshot="$PWD\out.png" --window-size=1200,1500 --force-device-scale-factor=2 `
  --hide-scrollbars $page
```

On Windows, Chrome may print a few `ERROR ... external_registry_loader` lines
before "bytes written to file". They are about installed extensions and do not
affect the image. The carousel commands above work the same way: swap the Chrome path and
build the `file:///C:/...` address as shown.

`--force-device-scale-factor=2` is what makes the text sharp; without it the
headline looks soft on a phone. Layouts are chosen by the `?layout=` parameter:
`number`, `checklist`, `diagram`, `photo`.

No Chrome, or it will not cooperate? Open the HTML file in any browser and take a
screenshot of the card. The result is the same; it just is not repeatable.

For the brand: set `--accent` and `--font` once in the template, keep them for
every post. Two colours and one typeface are a style; five colours are a mess.

## What to ask the client for

- **Twenty five to thirty real photographs** of whoever is the face: at work, at
  an event, travelling, and a plain portrait. Vertical, phone camera is fine.
- **Ten to fifteen of each additional speaker**, plus a few group shots.
- **Screenshots of the product or the work**, if there is anything to show.
- No watermarks, and no other people's faces in close-up.

They go into the agreed folder, not into a chat thread: in a thread they are lost
within a week.

## What we never do

- Stock photographs or AI-generated images.
- Collages of client logos without their permission.
- Screenshots with real names, addresses or sums.
- Different styles inside one stream. "Let's try something different this week"
  costs recognisability and buys nothing.
