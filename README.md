# SBE Show Prep Agent

Generates weekly show prep documents for **Steve Brown, Etc.** on Key Life Network.

Given an author name and book title, it:
1. Searches the web for the guest's bio, social handles, website, and book details
2. Generates interview questions, studio banter, hashtags, and YouTube copy in Steve Brown's voice
3. Saves a formatted `.docx` file ready for production

---

## Two Ways to Use It

### Option 1: Inside Claude Code (recommended — no API key needed)

Open Claude Code in your show prep folder and say:

> "Generate show prep for [Author Name] / [Book Title]"

Claude will search the web, generate all content, and save the `.docx` directly. No setup required.

### Option 2: Run the script directly

Requires an [Anthropic API key](https://console.anthropic.com/).

**Setup (one time):**
```bash
pip3 install anthropic duckduckgo-search python-docx

# Add your API key — create a .env file (never commit this):
echo 'ANTHROPIC_API_KEY=sk-ant-...' > .env
```

**Run:**
```bash
python3 generate_show_prep.py --author "Hugh Ross" --book "Noah's Flood Revisited"

# With optional args:
python3 generate_show_prep.py \
  --author "Hugh Ross" \
  --book "Noah's Flood Revisited" \
  --episode 28 \
  --airdate "7.11.26" \
  --year 2026
```

---

## What Gets Generated

| Section | Content |
|---|---|
| Opening teaser | ALL CAPS hook in Steve Brown style |
| Studio banter | Lines for Matthew, Jeremy, John, George, Cathy |
| Guest intro | Bio paragraph with bold author name |
| Segments 1–4 | Interview questions drawn from book content |
| Segment rejoins | With social handle mentions in Seg 3 |
| Key Life plugs | Segment 4 & 5 outros |
| Metadata | Show title, airdate, social handles, hashtags |
| YouTube copy | Title, description, guest bio, chapter markers, tags |

## What to Fill In After Recording

- **YT Shorts Target Clip** — timestamp
- **Etc. Insider** — timestamp
- **Amazon Book** — replace placeholder link
- **Posted date** — day after airdate
- **Social handles** — verify what was found is correct

---

## Dependencies

```
anthropic
duckduckgo-search
python-docx
```
