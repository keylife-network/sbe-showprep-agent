# SBE Show Prep Agent

Generates weekly show prep documents for **Steve Brown, Etc.** on Key Life Network.

Given an author name and book title, it:
1. Searches the web for the guest's bio, social handles, website, and book details
2. Generates interview questions, studio banter, hashtags, and YouTube copy in Steve Brown's voice
3. Saves a formatted `.docx` file ready for production

---

## Setup (fresh computer)

**Requirements:** Python 3.10+, [Claude Code](https://claude.ai/code)

```bash
# 1. Clone the repo
git clone https://github.com/keylife-network/sbe-showprep-agent
cd sbe-showprep-agent

# 2. Install Python dependencies
pip3 install -r requirements.txt
```

That's it for Option 1 (Claude Code). For Option 2 (standalone script), one more step:

```bash
# 3. Add your Anthropic API key — get one at https://console.anthropic.com/
echo 'ANTHROPIC_API_KEY=sk-ant-...' > .env
```

---

## Two Ways to Use It

### Option 1: Claude Code agent (recommended — no API key needed)

Open Claude Code inside the cloned repo folder and say:

> **"Generate show prep for [Author Name] / [Book Title]"**

Claude searches the web, generates all content, and saves the `.docx` to `./2026/` (or whatever the current year is). No API key needed — Claude Code handles authentication.

You can include optional details:
> "Generate show prep for Hugh Ross / Noah's Flood Revisited, episode 28, airdate 7.11.26"

### Option 2: Run the script directly

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

Output is saved to `./2026/28 - Hugh Ross_Show Prep.docx` (episode number auto-detected if not specified).

---

## What Gets Generated

| Section | Content |
|---|---|
| Opening teaser | ALL CAPS hook in Steve Brown's voice |
| Studio banter | Lines for Matthew, Jeremy, John, George, Cathy |
| Guest intro | Bio paragraph with bold author name |
| Segments 1–4 | Interview questions drawn from book-specific research |
| Segment rejoins | Social handle mention in Seg 3, Key Life plugs in Seg 4–5 |
| Metadata | Show title, airdate, social handles, hashtags |
| YouTube copy | Title, description, guest bio, chapter markers, tags |

## What to Fill In After Recording

- **YT Shorts Target Clip** — timestamp
- **Etc. Insider** — timestamp
- **Amazon Book** — replace the placeholder link
- **Posted date** — verify the day after airdate
- **Social handles** — double-check what the agent found
