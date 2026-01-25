# Refactor Reader

Since I zone out after the abstract while reading in PDFs, I want to read the papers more actively.
I built this because I wanted to refactor papers like legacy code: rewrite the confusing parts, delete the bloat (math I don't get), and save the gist of it so I can pretend I read it later.
It's a single HTML file. No build step. No npm install. No servers.

## What is it?

It's a wrapper around ArXiv's HTML view that lets you:

1. **Rewrite paragraphs:** Click text, write what you *think* it means in plain English, hit enter. It replaces the academic jargon with your notes.
2. **Delete bloat:** Turn on Delete Mode and click elements to remove them from existence. Therapeutic.
3. **Synthesize:** A side panel to track the "So What?" of the paper (Goal, Method, Impact).
4. **Export:** It generates a Markdown file of your notes and opens a URL to save it directly to your GitHub repo. Be an academic weapon. Ah guess I should've named it academic weaponizer.

## How to run it

It's one file

1. Clone the repo
2. Set up GitHub Page and Workflow permissions (hate ellaborating it, do what seems appropriate) in the settings
4. Paste an ArXiv URL

## How it works

* **Fetching:** It hits `arxiv.org/html/ID`. Since ArXiv has CORS headers, I route it through `corsproxy.io`. If that goes down, the app breaks. Ik it's messy.
* **Styling:** Tailwind via CDN. Idc, I have 1 Gbps internet.
* **Saving:** There is no database. Your notes live in the DOM. If you refresh the page, your work is gone. Use the "Export to GitHub" button before you close the tab.

## Exporting to GitHub

* If you host this on GitHub Pages (e.g., `username.github.io/reader`), it assumes you want to save notes to that same repo.
* If you run it locally, it defaults to `YOUR_USERNAME/YOUR_REPO_NAME`.

To fix the local default, open the html file, scroll to line 350-ish, and change the `repoSlug` variable.

No license, ppl won't even notice this exists.
