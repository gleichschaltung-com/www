# gleichschaltung.com

The source of [www.gleichschaltung.com](https://www.gleichschaltung.com): a short definition of *Gleichschaltung* followed by a scrolling timeline of how the Nazi regime took power in 1933–1934.

The site is a single static page with no build step:

| File | What it is |
| --- | --- |
| `index.html` | The page itself: the definition, the styles and the script that draws the timeline. |
| `timeline.md` | The timeline events. **This is the only file you need to touch to change the timeline.** |
| `favicon.svg`, `favicon.ico`, `apple-touch-icon.png` | The site icon: two switches set the same way, for *gleich* + *schalten*. The `.ico` and `.png` are renders of the SVG. |
| `CNAME` | The custom domain the site is served from. |

## Changing the timeline

All events live in [`timeline.md`](timeline.md). The page reads that file when it loads and builds the timeline from it, so there's nothing to regenerate or copy anywhere else.

### The easy way: edit on GitHub

1. Open [`timeline.md`](timeline.md) on GitHub and click the pencil icon (**Edit this file**).
2. Make your change (see the format below).
3. Click **Commit changes…** and choose **Create a new branch and start a pull request**. Say briefly what you changed and, for new facts, where they come from.

Once the pull request is merged into `main`, the change goes live on the site.

### The event format

Each event starts with a `## ` heading holding its title. The next line holds the date, then comes a blank line, then the description:

```markdown
## Title of the event
**Date:** 30 January 1933

One or more paragraphs describing what happened.
Use *asterisks* for italics and **double asterisks** for bold.
Links look like [this](https://example.org).
```

The rules:

- **Dates** are written in English as *day month year*, e.g. `5 March 1933`. Write the month name out in full (`March`, not `Mar`).
- **Spans of days** are written as `27 June – 5 July 1933` or `30 June – 2 July 1934`. The event sits on the timeline at its first day, and the date text is shown exactly as written.
- **Order doesn't matter.** Events are sorted by date automatically. Events on the same day keep the order they have in the file.
- **Paragraphs** are separated by a blank line. Line breaks inside a paragraph are joined up.
- **Formatting** is limited to `*italics*`, `**bold**` and `[links](https://…)`. Other Markdown (lists, images, headings inside an event) isn't supported.
- **Anything above the first `## ` heading** (the title and the instructions at the top of the file) isn't shown on the page.

The timeline's range follows the events: its month and year marks run from the month of the earliest event to the month after the latest one. You can add events outside 1933–1934 without changing any code.

### Adding, changing and removing events

- **To add** an event, copy an existing one (from its `## ` line down to the line before the next `## `), paste it anywhere in the file and change the text.
- **To change** an event, edit its title, date or description in place.
- **To remove** an event, delete everything from its `## ` line down to the line before the next `## `.

### If something goes wrong

If an event's date can't be read, that event is left out, and the page shows a notice at the bottom of the timeline naming the event that was skipped. The usual cause is a date in the wrong format or a missing `**Date:**` line directly under the title. The browser console (`timeline.md: …`) shows the same message.

## Previewing locally

The page loads `timeline.md` with `fetch`, which browsers block for pages opened straight from disk (`file://`). Serve the folder with any static web server instead, for example:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

Without JavaScript, the page shows a link to `timeline.md` so the events can still be read as text.

## Contributing

Corrections, sources and new events are welcome. Please open a pull request, or open an issue if you're unsure about something. For changes to the facts, include a source in the pull request description.
