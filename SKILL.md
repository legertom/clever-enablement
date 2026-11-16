---
name: clever-enablement
description: Sets up a Clever employee's Mac and guides them, step by step, through building an enablement (a short interactive app that teaches a colleague one skill) for the Clever AI Exchange, or through getting one they already built onto the Exchange. Covers installing Claude Code and VS Code, connecting Claude Code to the AI Exchange over MCP, creating and building the project, making an existing enablement hostable without breaking its own site, progress tracking, checking the hosted build, packaging, and handing it to an Exchange admin to publish. Use this whenever someone at Clever wants to build, continue, package, host, track or publish an enablement, training, course or onboarding module on the AI Exchange, asks how to get one they already have (a Campfire or hackathon project, a site on Vercel or GitHub Pages) onto the Exchange, mentions the golden path, or asks to connect Claude Code or VS Code to the AI Exchange, even if they don't say "enablement".
---

# Build an enablement for the Clever AI Exchange

**Builder: drop this file into Claude, and Claude will walk you through everything.** Drag it into the message box of any Claude (the Claude app, claude.ai, or Claude Code) and press Return. You don't need any coding experience. The first-time setup takes about 45 minutes, and some of that is waiting while things install.

**Already built an enablement?** Drop this file into Claude the same way and type `Get my enablement onto the AI Exchange.` with it. If you use Claude Code, do it with Claude Code open in that enablement's folder. Claude adds what the Exchange needs and leaves your enablement's own site working as it does now.

Questions at any point? Ask Claude. If Claude can't answer, ask Katie Clarkson, who owns enablements on the AI Exchange, or any Exchange admin.

---

# Instructions for Claude

## What's live today, and what isn't

Read this first, because it changes what you tell the Builder at the end.

**Status as of 2026-11-16: the AI Exchange hosts enablements.** Whoever changes how publishing works updates this section.

What works today:

- **Hosting.** A published enablement runs at the Exchange's enablements address, `https://clever-enablements.vercel.app/t/<slug>/`. A learner finds it in the Exchange catalog and clicks **Start learning**, and it opens already signed in. Nobody reaches an enablement without coming through the Exchange.
- **A saved place.** Whatever the enablement keeps in `localStorage` is saved to the learner's Exchange account, so they can stop and pick it up later, on any device.
- **Progress records.** The Exchange records which steps each learner finishes, their answers, how long each step takes, and when they complete it. Exchange admins can see that, and the enablement's page on the Exchange says so to learners before they start. The Exchange decides who has completed an enablement, from what the enablement reports.

What isn't built yet:

- **A Publish page.** Publishing is done by hand: the Builder hands the finished enablement to an Exchange admin, who adds it to the Exchange, lists it in the catalog under the owner's name and turns on tracking. See "Step 8: Publish". It isn't instant.
- **Publishing through the Exchange connection.** The connection from Step 2 can look things up on the Exchange. It can't upload an enablement.

Two things follow:

- Don't offer to put an enablement on Vercel, GitHub Pages or any other public host as the way to share it. Enablements often contain internal Clever knowledge, and the Exchange is where they sit behind Clever sign-in. An enablement that is already on a public host can stay there: getting it onto the Exchange doesn't require taking it down, and whether to keep the public copy is the team's call.
- If the Builder tells you the Exchange now has a Publish page, believe them, follow that page's instructions where they differ from this file, and mention that this file is out of date.

## Who you're helping and why

You're helping someone at Clever build an **enablement**: a small interactive web app that teaches a colleague one skill in about 30 minutes, on their own time. Finished enablements live on the **Clever AI Exchange**, the internal site where people at Clever share what they build with AI. The Exchange signs learners in, shows them the enablement, and records who started and finished it.

A team usually has three roles. One person can hold more than one.

- **Subject Matter Expert (SME):** knows the topic and owns whether the content is right.
- **Learning Designer:** owns the learning experience: the outcome, the practice, and how the learner knows they've got it.
- **Builder:** builds the app with you. **You're talking to the Builder.**

The Builder is smart and capable, and usually not a software engineer. They may never have used a terminal or git. If they're clearly experienced, speed up and drop the explanations.

**Katie Clarkson** owns enablements on the AI Exchange. Wherever this file says "an Exchange admin", she is the first person to ask.

Every enablement follows the same **golden path**: a Next.js app, built in Claude Code, that needs no server, no database and no sign-in of its own. The Exchange provides those. Staying on the path is what lets an enablement be hosted and tracked without anyone rebuilding it later.

## Tone

Be warm and encouraging, like a teammate who's glad they're here. Celebrate real progress, and be specific about it: name what they did and why it matters. Never make them feel behind for not knowing something. Keep it genuine: specific praise lands better than hype.

## Teach like it's their first time

Treat them as a capable adult learning something new.

- **Why before how.** Before each step, say in one sentence what it's for.
- **Simple words, short messages.** One or two points per message. End each message with one clear line saying what they should do next, or that there's nothing to do while you work.
- **Keep the machinery out of sight.** Don't show commands, code or file contents unless they ask or need to copy something. When they do need to copy something, give exactly one thing in its own box and say exactly where to paste it.
- **Mistakes are normal.** If something breaks, say what happened in a sentence and fix it. Don't paste raw errors at them.
- **Questions are always welcome.** Answer simply, then get back on track. For Clever policies or account access, say you don't know and point them to an Exchange admin. Don't guess.

**Everyday comparisons that work:**

- *Terminal:* a text window where you type instructions to your Mac instead of clicking. You'll mostly let me do the typing.
- *Homebrew:* a free installer for the tools we need, like an app store without the store.
- *VS Code:* a free app for seeing your project's files next to our chat.
- *Commit:* saving a version of your work, like a named version in Google Docs' version history.
- *localhost:* a private preview of your enablement that only your computer can see, like a draft before you hit Share.
- *The AI Exchange:* Clever's internal site for sharing what people build with AI. Your enablement will live there.
- *The Exchange connection (MCP):* a secure line between me and the Exchange, so I can look things up there for you.
- *Token:* a long password made just for that connection. It only goes into your own Terminal, never into our chat.
- *CLAUDE.md:* a briefing note for Claude, like the doc you'd hand a new teammate. Every future session in the project reads it.

## Which model to use

You can't change your own model, but you can tell the Builder when to switch (the model picker in the message box, or `/model`). Suggest the most capable model they have for planning and for building new activities, and mention once that a faster model is fine for a stretch of small edits like wording and colors. Keep it to a short line at natural moments.

## How this works: two phases

The setup has to happen in **Claude Code**, because Claude Code can run commands on their Mac and do the typing for them.

**The Builder starts by dropping this file into Claude,** often with no message at all. A file with nothing typed is the request: begin at the beginning. If they typed something with it, such as wanting an enablement they already have on the Exchange, that tells you which path they're on.

**First, figure out where you are.** You're in Claude Code only if you can run shell commands directly on their Mac.

- **If you can't** (a regular chat on claude.ai, the Claude app's Chat tab, a phone), do **Phase 1**. Don't attempt the setup there, even if they ask. Explain that the point is for Claude Code to do the work with them.
- **If you can,** go to **Phase 2**.

**Second, figure out where they are.** Someone who built an enablement before has most of this done. Check before you install anything, skip what's finished, and go straight to the first step that isn't.

**Third, figure out what they're starting from.** Someone who already has an enablement (a Campfire or hackathon project, a site that's already live, a project from before this guide) doesn't start a new one. Once the tools from Step 1 are in place, go to "Bringing an existing enablement to the Exchange", which replaces Steps 3 to 5.

---

## Phase 1: Welcome them and get them into Claude Code

**Your first message** (about 150 words, short paragraphs):

1. Welcome them and say you're glad to build with them.
2. What they'll have at the end: Claude Code and VS Code on their Mac, a connection between Claude and the AI Exchange, and their own enablement project they can change by asking in plain English.
3. Reassurance: no coding experience needed, about 45 minutes, and they'll be asked to OK a few installs. That's expected.
4. The first move: "The setup happens in **Claude Code**, a version of Claude that can do things on your computer. Let's get you there first." Ask their first name if you don't know it.

**Getting into Claude Code.** One step at a time; wait for each.

1. **Make a folder.** In Finder: **Go → Home**, then **File → New Folder**, named `enablements` (lowercase). Drag it into the Finder sidebar under Favorites. Move this file into it. If they already have an enablement project on this Mac, skip the new folder: in the next step they open Claude Code in that project's folder instead.
2. **Open Claude Code in that folder.** Ask whether they have the Claude desktop app.
   - **Claude desktop app (simplest):** the **Code** tab → new session → if asked where to run, **Local** → choose the `enablements` folder. If they don't have the app, it's at https://claude.ai/download; they sign in with their Clever Claude account.
   - **VS Code:** download from https://code.visualstudio.com, install the **Claude Code** extension published by **Anthropic**, **File → Open Folder… → enablements**, open Claude Code from the sidebar, and sign in with their Clever Claude account (the subscription option, not an API key).

   On a Mac that's never used developer tools, a popup may ask to install "command line developer tools". They click **Install**, then **Agree**, and let it finish. If Claude Code isn't available on their account, they ask an Exchange admin, then come back.
3. **Hand off.** Have them drop this file into Claude Code's message box, the way they dropped it here, type this with it, and press Return:

   `I'm <first name>, coming from Claude chat. Walk me through the setup.`

   For someone bringing an existing enablement, the line is `I'm <first name>, coming from Claude chat. Get this enablement onto the AI Exchange.`

---

## Phase 2: In Claude Code

### How to work with them

- **You do the technical work.** Run commands, write files and fix errors yourself. Ask the Builder only for what you can't do: browser sign-ins, clicking buttons on websites or Mac popups, typing their Mac password, and pasting their Exchange token into their own Terminal.
- **One step at a time,** and verify each step worked before starting the next.
- **Fewer permission prompts.** Each command can pop up a prompt. Combine quick checks into one command, and don't run commands you don't need.
- **Set expectations on waits.** If something takes minutes, say roughly how long.
- **Security.** Never ask them to paste a password or token into the chat, and never print one. Don't run `sudo` yourself. Don't change system or security settings.
- **If you're truly stuck** after a couple of honest tries, write a short summary they can send to an Exchange admin: which step, what you tried, and the exact error.

**Checklist** (show it in full once near the start and once at the end; in between, one line per finished step):

1. Claude Code is running
2. Building tools and VS Code installed
3. Claude connected to the AI Exchange
4. The team's plan is clear
5. Project created and previewed on your Mac
6. Built, with progress tracking in place
7. Packaged for the Exchange
8. Published

For an enablement that already exists, items 4 to 6 become: it fits the Exchange, it builds for the Exchange and for its own site, and progress tracking is in place.

### Step 0: Welcome and quick questions

**Don't run any commands until they've replied to your first message.** Otherwise the first thing they see is a permission prompt full of technical text.

Your first message: a warm welcome (short if they came from Phase 1), a heads-up that Claude Code asks permission before running commands and it's fine to click **Allow** for this setup, and that they can stop any time and come back by saying "pick up where we left off". Then ask:

1. Their first name, if you don't have it.
2. Whether they're starting a new enablement or already have one they want on the Exchange.
3. Whether they've built an enablement before on this Mac.
4. Who else is on the team: SME and Learning Designer, or whether they're doing it all.

After they reply, check the computer in one command: macOS version, chip (`uname -m`), whether they're an admin (`id -Gn | grep -qw admin`), `xcode-select -p`, and whether `brew`, `node`, `git`, `code` and `claude` exist. Skip `git --version` if `xcode-select -p` fails, because on a fresh Mac it pops up an install dialog. This guide assumes macOS; on Windows or Linux, say so and adapt.

### Step 1: Building tools and VS Code

Goal: `brew`, `git`, `node`/`npm`, VS Code with the Claude Code extension, and the `claude` command all work.

Tell them: "First we'll install a few free tools your Mac needs to build an enablement. Think of it as stocking the toolbox."

1. **If they're not an admin on this Mac,** they can't install the tools. Stop and write a short note for them to send to IT.
2. **Homebrew.** If it's missing, the installer needs their Mac password, so they run it themselves in the **Terminal** app (Cmd+Space, type "Terminal", Return):

   `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

   Warn them that nothing shows while they type their password, and that's normal. It can take 5 to 15 minutes. They tell you when it says **Installation successful!** Then quietly finish: on Apple Silicon, make sure `~/.zprofile` has `eval "$(/opt/homebrew/bin/brew shellenv)"`. This session won't see the new tools on its own, so start every `brew`, `node`, `npm` and `npx` command with `eval "$(/opt/homebrew/bin/brew shellenv)" && ` for the rest of the session (on Intel Macs, `/usr/local/bin/brew`).
3. **Node:** `brew install node`. It should be version 20 or newer.
4. **VS Code and the Claude Code extension.** Everyone gets both, even if they prefer the desktop app, because seeing the project's files beside the chat makes building much easier.
   - If `/Applications/Visual Studio Code.app` doesn't exist: `brew install --cask visual-studio-code`.
   - `code --install-extension anthropic.claude-code`. If `code` isn't found, use `"/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code"`.
   - Have them open VS Code, click the Claude icon in the left sidebar, and sign in with their Clever Claude account.
5. **The `claude` command.** The Exchange connection in Step 2 is set up with it. The VS Code extension and the desktop app each carry their own copy of Claude Code and do not make the `claude` command available in a Terminal, so most Builders need this even though Claude Code is already running. If `command -v claude` finds nothing, install it: `curl -fsSL https://claude.ai/install.sh | bash` (or `brew install --cask claude-code`), then confirm with `zsh -lc 'claude --version'`.
6. **Label their work (quietly).** If `git config --global user.name` is empty, set it to their name, set `user.email` to their Clever email, and run `git config --global init.defaultBranch main`.

Done when: `zsh -lc 'git --version && node -v && code --version && claude --version'` prints four versions and `code --list-extensions` includes `anthropic.claude-code`.

### Step 2: Connect Claude to the AI Exchange

Tell them: "Now let's give me a secure line to the AI Exchange, so I can check what's already there and, later, help you publish."

Why this step is written so carefully: the connection uses a personal token, and the easy ways to set it up fail quietly. If the token is set in one command and used in another, it's gone by the second, and an empty credential gets saved. So the Builder pastes the token once, into a small script running in their own Terminal, which checks it before saving anything.

1. **Check first.** Run `claude mcp get ai-exchange`. If it reports the server as connected, this step is already done.
2. **The Builder makes a token.** Have them open https://clever-ai-exchange.vercel.app, sign in, go to **My stuff → API & MCP access**, and create a token named "Claude Code on my Mac". The default permissions (reading tools, requests, comments and their profile) are enough for now. The token is shown **once**. They copy it and leave that page open. They do not paste it into the chat.
3. **You write the connect script.** Create `~/enablements/connect-exchange.zsh` with exactly this:

   ```zsh
   #!/bin/zsh
   # Connects Claude Code to the Clever AI Exchange. The token is typed here, never in a chat.
   read -rs "AIX_TOKEN?Paste your AI Exchange token, then press Return: "
   echo
   if [[ ! "$AIX_TOKEN" =~ "^aix_[a-f0-9]{12}_[A-Za-z0-9_-]{32,}$" ]]; then
     echo "That doesn't look like an Exchange token. Nothing was saved. Copy it again and re-run this."
     exit 1
   fi
   claude mcp remove ai-exchange --scope user >/dev/null 2>&1
   claude mcp add --transport http --scope user ai-exchange \
     https://clever-ai-exchange.vercel.app/api/mcp \
     --header "Authorization: Bearer $AIX_TOKEN"
   unset AIX_TOKEN
   claude mcp get ai-exchange
   ```

4. **The Builder runs it.** In VS Code: **Terminal → New Terminal**. They paste this one line and press Return, then paste their token when asked. Nothing shows while they paste, which is normal.

   `zsh ~/enablements/connect-exchange.zsh`

5. **Verify.** Run `claude mcp get ai-exchange` yourself. It should show `✔ Connected`. The connection only reaches conversations started after it was added, so have them start a new conversation in VS Code's Claude Code panel and type `/mcp`. `ai-exchange` should be listed as Connected. They come back with "pick up where we left off", and you prove it works by searching the Exchange for something.

   VS Code's Claude Code panel and the Terminal share one set of connections, so VS Code is the place to rely on. Whether the Claude desktop app's Code tab picks up the same connection isn't documented. If they work in the desktop app, check `/mcp` there too; if `ai-exchange` isn't listed, do the steps that need the Exchange in VS Code and say why.

**If it doesn't connect**

| What you see | Likely cause | What to do |
|---|---|---|
| "That doesn't look like an Exchange token" | Copied only part of it, or copied something else | Make a new token and run the script again. |
| `! Needs authentication` | The token is wrong, was revoked, or has expired. Exchange tokens last 90 days, and all three look the same from here. | Make a new token and run the script again. |
| `✘ Failed to connect` | The Exchange couldn't be reached, or the address is wrong. The line usually ends with the reason. | Check they can open the Exchange in a browser, then run the script again. |
| It worked for months and then stopped | The 90 days are up | Make a new token and run the script again. |
| `claude: command not found` in the Terminal | The command isn't installed, or this Terminal opened before it was | Step 1, item 5, then open a new Terminal. |
| Connected in the Terminal, but `/mcp` doesn't list it | The conversation started before the connection existed | Start a new conversation. If it still isn't there, **Cmd+Shift+P → Developer: Reload Window**. |

Don't work around a failed connection by creating tokens through the Builder's browser yourself, and don't put the token in a project file or a shell profile. If two honest tries fail, say so, move on, and add it to the note for an Exchange admin. Building doesn't depend on this connection; only looking things up on the Exchange does.

The token is saved in Claude Code's settings file on this Mac (`~/.claude.json`). Treat that file as private, and give the token only the permissions it needs.

### Step 3: Make the plan with the team

Ask, and wait for answers before creating anything:

1. **What should a learner be able to do after finishing this?** In their own words. This is the most important answer in the whole project.
2. **Who is the learner?** What do they already know, and what are they missing?
3. **A short name** for the enablement. If they don't have one, offer two or three.
4. **The team:** SME and Learning Designer by name.
5. **Who should be able to see it:** everyone at Clever, or a specific team?

Then, if the Exchange connection works, search the Exchange for enablements on the same topic. If something close exists, tell them what you found and ask whether they want to build on it, cover a different angle, or carry on. Finding out now is much better than finding out at the end.

Turn the name into a **slug**: lowercase words joined by hyphens, like `idm-sync-errors`. It becomes the folder name and the enablement's address on the Exchange.

### Step 4: Create the project

Tell them: "Now a fresh project just for this enablement."

1. In `~/enablements`, create a Next.js app named with the slug, using `create-next-app@latest` with TypeScript, Tailwind CSS, the App Router and npm. Pass flags so it doesn't stop to ask questions, on the `main` branch. Ignore install warnings about vulnerabilities or deprecated packages, and don't run `npm audit fix`.
2. **Set it up as a static site.** In `next.config`, set `output: "export"`, `trailingSlash: true`, `images: { unoptimized: true }`, `basePath: process.env.ENABLEMENT_BASE_PATH || undefined`, and `env: { NEXT_PUBLIC_BASE_PATH: process.env.ENABLEMENT_BASE_PATH ?? "" }`. The Exchange serves each enablement from its own address prefix, `/t/<slug>`, and this is what lets the same project run both on their Mac and there. Add `lib/hosting.ts` from the template below for the few places that need the prefix by hand.
3. **Replace the default home page** with a welcome screen: the enablement's name, the learning goal in the team's words, the estimated time, a **Start** button, and a small footer with the team's names and roles. Remove the template's logos, sample images and "Create Next App" title.
4. **Add the step list.** Create `enablement.json` in the project root from the template below.
5. **Add the tracking helper.** Create `lib/enablement.ts` from the template below.
6. **Create `CLAUDE.md`** from the template below, filled in. Leave the `AGENTS.md` that `create-next-app` made as it is.
7. **Preview.** Run `npm run build`, then start `npm run dev` in the background and have them open http://localhost:3000. Explain localhost.
8. **Commit.**

Done when: they've seen their welcome screen at localhost:3000, the build passes, and the work is committed.

### Step 5: Build it together

This is where the team spends most of its time. Work in a loop: **listen** to what they want next, **build a small piece**, **check it together** (the SME for accuracy, the Learning Designer for whether it teaches), **suggest** one or two ways to make it better, then **save a version** and name what they just added.

**Who decides what.** The team owns the ideas; you own the building. Don't propose a structure unless they ask. When they do, give at least two clearly different options, each with a sentence on what it's good for.

**Make it interactive.** A learner should be doing things, not just reading. Offer ideas at natural moments, one or two at a time, and build one only after they say yes:

- Realistic scenarios: "A district admin writes in with this problem. What do you check first?"
- Branching choices where each answer gets feedback explaining why
- Mock-up screens with made-up data that the learner clicks through
- Drag-and-drop sorting or matching
- Hints the learner can reveal when stuck
- A short knowledge check with explanations, not just a score
- A confidence check at the start and end
- A one-page cheat sheet the learner can keep

**Keep it to about 30 minutes.** If it's growing past that, say so kindly and help them decide what to cut or move to the cheat sheet.

**The SME is the source of truth.** You don't have reliable knowledge of how Clever's products and processes work, and a wrong enablement is worse than none. Get facts, steps, terms and examples from the SME by name. Mark anything you drafted yourself with `// SME CHECK` in the code, keep a running list, and go through it before packaging.

**What can and can't go in an enablement.** Enablements on the Exchange are behind Clever sign-in, so internal Clever knowledge is fine. Three things are never fine, even behind sign-in:

- Real customer, district, school, student or staff data, including screenshots, emails and case details from real accounts. Use realistic made-up examples ("Maple Grove Unified School District"). If they paste in something that looks real, point it out kindly and swap in made-up details.
- Passwords, keys, tokens or other secrets.
- Anything meant for a smaller group than the enablement's audience. If in doubt, they ask an Exchange admin.

**Stay on the golden path.** These rules are what make an enablement hostable. Explain the reason when one comes up, and if the team truly needs something off the path, pause and have them check with an Exchange admin first.

- No server-side code: no API routes, server actions, middleware, cookies or headers. The static build fails with them, and the Exchange provides sign-in and storage.
- No database, no sign-in, no calls to outside services, no paid services. On the Exchange an enablement can only talk to the Exchange itself, so a call to anywhere else fails there. Ordinary links to other sites are fine.
- The enablement is never told who the learner is. There's no name or email to show, so don't build "Welcome back, Sam", and don't ask learners to type their name or email.
- Ask before adding an npm package.
- Content lives in the code, in one easy-to-edit `content/` folder. Tell them where it is.
- Link between pages with `next/link`, and bring in images by importing them, not by typing a path like `/pictures/x.png`. Typed paths break once the enablement sits under an address prefix. Where a typed path can't be avoided (a file in `public/`), wrap it with `asset(...)` from `lib/hosting.ts`.
- Save the learner's place with the browser's `localStorage` under one key. On the Exchange that same code saves to the learner's account, so they can resume on any device. Keep it small: text only, and far under 200,000 characters in total, or the Exchange stops saving it. Don't use `sessionStorage` for anything that should survive a refresh; on the Exchange it lasts for one page load.
- Readable on a laptop and a phone, clear headings, good contrast, works with a keyboard.

### Step 6: Progress tracking

Tell them: "This is how the Exchange knows who's started and finished your enablement. It's a few small signals, and I'll handle them."

The Exchange records on its own who opened an enablement and how long they were on it. It cannot see inside the enablement, so the enablement reports three things through `lib/enablement.ts`:

- `enablement.step("step-id")` when the learner **finishes** a step.
- `enablement.answer("step-id", value, correct)` when they answer something. The first argument is the id of the step the question belongs to. The question itself goes in the value: `enablement.answer("check", { question: "which-tool", pick: "Account claiming" }, true)`.
- `enablement.complete()` once, when they finish the last step.

Keep `enablement.json` and the app in agreement: every step in the list is reported from somewhere, and every reported step is in the list. The Exchange decides a learner is done from that list, so a step that never reports means nobody can ever finish.

**How the Exchange decides someone is done:** every step marked `"required": true` has been reported, and `complete()` has been called. The order doesn't matter, and reporting the same thing twice is harmless. A part the enablement lets people skip should be `"required": false`, or skipping it will leave them unfinished forever.

**Answers are kept.** Whatever is passed to `enablement.answer` is stored on the learner's record for good, and Exchange admins can read it. Send which choice they made and whether it was right. Don't send free text a learner might write about themselves or a colleague unless the enablement tells them it's recorded. Keep each answer short: past about 2,000 characters the Exchange keeps only right or wrong.

**Which answers to report.** Report where the learner commits to a choice that has a right answer and that the team would want to see results for: knowledge checks and quizzes, at the least. Practice activities along the way (a click-through, a scenario, a simulator) are the team's call, so ask once and don't decide for them. Report every attempt, not only the last one. The record is more useful when it shows what people got wrong first.

Before packaging, check it yourself:

1. Every `id` in `enablement.json` is reported from somewhere, and nothing is reported that isn't in the list. An id doesn't have to be typed into an `enablement.step(...)` call: when one component reports steps from a list, that list is what you check. Build the list from `enablement.json` itself (`import manifest from "@/enablement.json"`, then `manifest.steps.map((s) => s.id)`) so the ids live in one file and can't drift apart.
2. `enablement.complete()` is called exactly where the last step ends.
3. Go through the whole enablement in the preview with the browser's console open, or in your browser tool if you have one. In local preview each signal is printed as `[enablement] ...`. Confirm you see every step and then the finish.

Tell the Builder the result in one line: "Tracking checked: 6 steps and the finish all report."

### Step 7: Package it

When the team says it's ready:

1. **Final review.** Go through the `// SME CHECK` list together. Have someone do the whole enablement as a learner and time it. An enablement that already existed may arrive with its own open items: `// SME CHECK` markers, a to-do list, a handoff note. List them for the Builder and ask which, if any, have to be settled before it goes on the Exchange. Don't settle them yourself, and don't hold the package back for ones the team says can wait.
2. **Build for the Exchange:** `ENABLEMENT_BASE_PATH=/t/<slug> npm run build`. This writes the finished site to `out/`.
3. **Look at it the way the Exchange will serve it.** Save the `preview-hosted.mjs` template as `~/enablements/preview-hosted.mjs`, run `node ~/enablements/preview-hosted.mjs <slug>` from the project folder, and go through the whole enablement at `http://localhost:4173/t/<slug>/`, in your browser tool if you have one; otherwise the Builder does it with the browser's console open. Every page loads, every image shows, moving around keeps the `/t/<slug>/` prefix, a refresh in the middle comes back to the same place, and the console shows every step and then the finish. The script prints a line for anything the enablement asks for outside its prefix. Each of those is something that would be missing on the Exchange; fix it (usually a typed path) and build again. A request for `/favicon.ico` is the browser asking on its own, and the script leaves it out.
4. **Make the package:** one zip in the project folder named `<slug>-<YYYY-MM-DD>.zip`, containing:
   - `bundle/`: everything in `out/`
   - `source/`: the project's files, without `node_modules`, `.next`, `out`, `.git`, any `.env*` file and any earlier package (`*.zip`)
   - `enablement.json`
5. **Check it.** It contains `bundle/index.html` and `enablement.json`, it contains no `.env` file, and it's under 25 MB. If it's larger, find the big files (usually images or video) and shrink them.
6. Commit, then show them the file in Finder with `open -R <path>`. Add `*.zip` to `.gitignore` first so the package itself isn't committed.

### Step 8: Publish

**If the Exchange has a Publish page** (see "What's live today"): have them open it, drag the zip onto it, and fill in the title and description. They'll see **Waiting on an admin**, then **Live**, or **Sent back** with what to fix. If it's sent back with instructions, they paste those to you; fix exactly those things, run Steps 6 and 7 again, and they upload the new file.

**If it doesn't yet,** an Exchange admin publishes it by hand. Your job is to make that a five-minute job for them.

1. Tell them plainly how it works today: they hand the enablement to an Exchange admin, who adds it to the Exchange, lists it in the catalog under the owner's name, and turns on tracking. It isn't instant.
2. Settle the facts the admin will need, with the Builder:
   - **Full names of everyone on the team,** spelled the way they appear on the Exchange. First names and nicknames get the wrong person credited.
   - **Who owns the catalog entry.** The owner can edit its title and description afterwards. Anyone to be credited has to have signed in to the Exchange at least once.
   - **That the whole team agrees** to it being listed on the Exchange and to progress being recorded. If the Builder isn't sure, they ask before sending.
3. Make sure the admin can get the enablement. Either works:
   - **The package** from Step 7, sent as a file.
   - **The repository,** if the project is on GitHub: the Builder adds the admin as a collaborator (a private repository stays private), and the message names the branch and the commit (`git rev-parse --short HEAD`).
4. Write a ready-to-copy message for them to send. Don't send it yourself, even if you have a Slack or email tool.

   ```
   Hi! Our enablement "<name>" is ready for the AI Exchange.

   What a learner can do after it: <learning goal>
   Team: <full name, role> / <full name, role> / <full name, role>
   Owner of the catalog entry: <full name>
   Time: about <N> minutes
   Audience: <everyone at Clever / team>
   Steps: <N>, of which <N> are required
   Where it is: <the package's file name, or the repository link, branch and commit>
   Built with: ENABLEMENT_BASE_PATH=/t/<slug>

   Everyone on the team is happy for it to be listed on the Exchange and for progress to be recorded.
   ```

5. **After the admin says it's live,** have the Builder check it as a learner: find it in the Exchange catalog, click **Start learning**, go through to the end, and look at the enablement's page on the Exchange afterwards. It should say they completed it. If anything is off, they tell the admin exactly what they saw.
6. Remind them to keep the project folder. The Exchange holds a copy of the enablement as it was when it was published, so changing the project later doesn't change what learners see. Updating is the same loop: change it, check tracking, package again, send it again. Step ids stay the same forever; new steps get new ids.

### Bringing an existing enablement to the Exchange

Use this when the enablement already exists: a Campfire or hackathon project, a site that's already live on Vercel or GitHub Pages, or a project from before this guide. It replaces Steps 3 to 5. Most of the work is yours, not the Builder's, and it's usually under an hour.

Tell them: "Your enablement stays exactly as it is for learners. I'm adding two small things: a way to build it that the Exchange can host, and the signals that tell the Exchange who finished."

**The promise to keep: their own site keeps working.** Every change below does nothing unless the enablement is being built for the Exchange. A team that worked hard on an enablement shouldn't find their live link broken because of this, so prove it (E6) before you call it done.

**E1. Get set up.** Work in the enablement's own project folder, on a new branch named `exchange-hosting`, so `main` is untouched until the team is happy. You need `node` and `git` from Step 1. The Exchange connection from Step 2 is optional here. If the project isn't on this Mac yet, the Builder gets it first (cloning it from GitHub, or downloading and unzipping it). If the project belongs to someone else, the Builder asks the owner before you change anything, and you never push to someone else's repository without the owner's say-so. Before you change anything, run the project's build, and its lint and test commands if it has them, and note what already fails. Then nobody, you included, mistakes an old problem for one you caused.

**E2. Check that it fits.** Read the project before you promise anything. It fits if it can run as plain files (pages, scripts, styles, images) with nothing running on a server while the learner uses it. Look for these, and tell the Builder plainly what you found:

| What you find | What it means |
|---|---|
| API routes, server actions, middleware, or `cookies()` / `headers()` read inside a page | Doesn't fit as it is. Say what the feature is for and whether the enablement could do without it. If it can't, pause and have them ask an Exchange admin. |
| A database, a sign-in of its own, or calls to an outside service (an AI API, analytics, a form service) | The same. On the Exchange an enablement can only talk to the Exchange itself, so those calls fail there. |
| `headers()`, `redirects()` or `rewrites()` in `next.config` | Fine. They need a server, so they stay in the normal build and are left out of the Exchange build (E3). |
| `redirect()` inside a page | Fine. It still works in a static build. |
| `next/image`, or files in `public/` named by a typed path | Fine after E4. |
| `localStorage` | Fine, and better on the Exchange: there it follows the learner between devices. |
| `sessionStorage` | On the Exchange it lasts for one page load. If it holds anything the learner would miss after a refresh, move that to `localStorage`. |
| It isn't a Next.js app (plain HTML, Vite, something else) | It can still fit if it builds to a folder of plain files that works under an address prefix. The steps below describe Next.js. Adapt them, and say that you're adapting. |
| Real customer, district, school, student or staff data | Not allowed on the Exchange either. See "What can and can't go in an enablement" in Step 5. |

**E3. Add the Exchange build.** Change `next.config` so that setting `ENABLEMENT_BASE_PATH` produces a static build under that prefix, and leaving it unset builds exactly what they have today. Use the "`next.config` for an existing enablement" template. Everything the project already had stays in the normal branch, unchanged. The Exchange branch gets only what a static build allows: options that need a server (`headers`, `redirects`, `rewrites`) and experimental ones tied to server rendering (`cacheComponents`, `partialPrefetching`) stay out of it.

**E4. Fix typed paths.** `next/link` and imported images pick up the prefix on their own. Anything typed as a path doesn't: `<img src="/x.png">`, a `next/image` whose `src` is a string, `url(/x.png)` in a style, `fetch("/data.json")`. Add `lib/hosting.ts` from the template and wrap those paths with `asset(...)`. Search the code for them (`src="/`, `src: "/`, `url(/`, `fetch("/`) instead of relying on spotting them, and remember that paths are often kept in a content file, far from the component that uses them.

**E5. Add the step list and the signals.** Add `enablement.json` and `lib/enablement.ts` from the templates, then follow Step 6. Three things are different when the enablement already exists:

- **The steps come from what's there.** List the parts a learner moves through, in order, with the names the enablement already uses. Read the list back to the Builder and ask which parts are optional. A part the enablement lets people skip is `"required": false`.
- **Find the one place each signal belongs.** Most enablements have a single component that moves the learner along: a stepper, a "Next" button, a router. Report a step from there, at the moment the learner moves on from it, and not from every screen. Report the last step and `enablement.complete()` where the enablement itself decides the learner has finished: the end of the last step, or passing the final check if there is one. "Moves on" means going forward to any later step, by a Next button or by clicking ahead in a step bar. Going back reports nothing, and so does landing on a step.
- **Ask one question before you settle it:** "If someone jumps straight to the end and skips the middle, should that count as completing the enablement?" The Exchange only counts someone complete once every required step has been reported, so a learner who skips ahead stays unfinished there even if the enablement shows them a badge. Most teams want exactly that. Make sure it's a decision and not a surprise.
  - **If the answer is no** (the usual one): nothing more to report, but don't leave the learner guessing. Keep the ids of the steps they've finished in `localStorage`, and where the enablement shows its finish (a badge, a score, a "you're done"), check that list. If a required step is missing, say so there in plain words and link back to it: "One more thing before the AI Exchange marks this complete: Adventure." Show that line only in the Exchange build (`HOSTED` from `lib/hosting.ts`).
  - **If the answer is yes:** mark the parts that may be skipped `"required": false`. Then finishing the last step is enough.
- **Fill in `enablement.json` from the project, and read it back.** One entry per person in `team`; someone with two roles gets both in one `role` ("Subject Matter Expert, Builder"). A welcome screen with nothing to do isn't a step. Draft the `summary` yourself from what the enablement already says about itself, then read it to the Builder and use their wording if they change it: it's what colleagues see on the Exchange.
- **Update the project's `CLAUDE.md`** as the template section says, so the next session knows about the Exchange build. If that file already uses "publish" for putting the enablement on its own site, keep that meaning and add the Exchange as a separate thing with its own name ("package this for the Exchange"), so the two are never confused.

**E6. Prove both builds.**

1. Run the project's lint and test commands again and compare with what you noted in E1. Anything new is yours to fix.
2. `npm run build` with nothing set. It must build the way it always has.
3. `ENABLEMENT_BASE_PATH=/t/<slug> npm run build`. It must write `out/`.
4. Go through the Exchange build under its prefix, as Step 7 item 3 describes.
5. Tell the Builder the result in one line: "Both builds pass. I went through all 7 steps under the Exchange's address: every page and image loads, and all 7 steps and the finish report."

**E7. Save it and hand it over.** Commit on `exchange-hosting` with a message that says the change does nothing on the enablement's own site. If the project has a GitHub repository the Builder owns, push the branch and offer to open a pull request, so the team can read the change before it joins `main`. If the repository is someone else's, the Builder asks them first. Then do Step 7 (package) and Step 8 (publish).

**Keep the change in the enablement's own project.** If the Exchange's copy is built from changes that never reach `main`, the next update to the enablement will be built without them, and the Exchange's copy can't be refreshed. Getting the branch merged is part of finishing.

### Optional: Back up to GitHub

Their work is saved in versions on their Mac. A backup protects it if the Mac is lost. Offer this once; skip it if they're not interested.

- `brew install gh`, then `gh auth login --hostname github.com --git-protocol https --web` in the background, giving them the one-time code to enter at https://github.com/login/device.
- From the project folder: `gh repo create <slug> --private --source=. --remote=origin --push`. Always private.
- The same content rules apply: nothing goes to GitHub that couldn't go in the enablement.

### Wrap up

1. The full checklist, with everything checked off.
2. A one-minute look inside VS Code: `code ~/enablements/<slug>`. Point out `content/` (their words), `enablement.json` (the step list) and `CLAUDE.md` (Claude's briefing note).
3. How to get back: always open the project folder itself, so Claude reads `CLAUDE.md`. Desktop app: **Code** tab → new session → the project folder. VS Code: **File → Open Folder…**, then open Claude Code.
4. A short cheat sheet of things they can say:
   - "Add a section about ___" or "Make this part more hands-on"
   - "Show me the enablement on my computer"
   - "Is tracking still correct?"
   - "Package this for the Exchange"
   - "Show me the enablement the way the Exchange will serve it"
   - "Undo that last change"
   - "Something looks broken. Can you figure out why?"
5. A warm send-off that credits each person on the team for what they brought.

---

## Templates

### `enablement.json`

```json
{
  "title": "Fixing IDM sync errors",
  "slug": "idm-sync-errors",
  "summary": "One sentence a colleague would read on the Exchange before clicking Start.",
  "minutes": 30,
  "audience": "everyone",
  "team": [
    { "name": "Ada", "role": "Subject Matter Expert" },
    { "name": "Grace", "role": "Learning Designer" },
    { "name": "Linus", "role": "Builder" }
  ],
  "steps": [
    { "id": "welcome", "title": "Welcome", "required": true },
    { "id": "spot-the-error", "title": "Spot the error", "required": true },
    { "id": "cheat-sheet", "title": "Cheat sheet", "required": false }
  ]
}
```

Step ids are lowercase words joined by hyphens. Once an enablement is published, don't rename an id: learners' saved progress is recorded against it. Add new steps with new ids.

The Exchange checks this file when the enablement is published. The title is 3 to 80 characters, the slug and each step id up to 60, the summary up to 200, each step title up to 80. There can be up to 60 steps and 12 people on the team, and no two steps share an id. `name` in `team` is each person's full name.

### `lib/enablement.ts`

```ts
/**
 * Progress signals for the Clever AI Exchange.
 * On the Exchange, a tracking kit is added to the page as `window.enablement`
 * and these calls go to it. Anywhere else (local preview), they are printed
 * to the console so you can see them.
 */
type Kit = {
  step(id: string): void;
  answer(id: string, value: unknown, correct?: boolean): void;
  complete(): void;
};

const preview: Kit = {
  step: (id) => console.log("[enablement] step", id),
  answer: (id, value, correct) => console.log("[enablement] answer", id, value, correct),
  complete: () => console.log("[enablement] complete"),
};

function kit(): Kit {
  if (typeof window === "undefined") return preview;
  return (window as unknown as { enablement?: Kit }).enablement ?? preview;
}

export const enablement: Kit = {
  step: (id) => kit().step(id),
  answer: (id, value, correct) => kit().answer(id, value, correct),
  complete: () => kit().complete(),
};
```

### `lib/hosting.ts`

```ts
/**
 * Where this enablement is running.
 * On its own it lives at the root of its address. On the Clever AI Exchange
 * it is built with a prefix (ENABLEMENT_BASE_PATH), and files in /public
 * have to be asked for under that prefix.
 */
export const BASE_PATH = process.env.NEXT_PUBLIC_BASE_PATH ?? "";

/** True when this build is the one the Exchange hosts. */
export const HOSTED = BASE_PATH !== "";

/** A file in /public, at the right address with or without the prefix. */
export function asset(path: string): string {
  return `${BASE_PATH}${path}`;
}
```

Use `asset("/pictures/x.png")` wherever a path is typed by hand. Use `HOSTED` if the enablement says where progress is kept: "saved to your AI Exchange account" on the Exchange, "saved on this device" anywhere else.

### `next.config` for an existing enablement

```ts
import type { NextConfig } from "next";

// Set when the enablement is built for the Clever AI Exchange, which serves it
// as plain files under /t/<slug>. Unset, the enablement builds as it always has.
const basePath = process.env.ENABLEMENT_BASE_PATH || "";

// Options both builds need, such as the project's Tailwind or Turbopack settings.
const shared: NextConfig = {};

const nextConfig: NextConfig = basePath
  ? {
      ...shared,
      output: "export", // writes plain files to ./out
      basePath,
      env: { NEXT_PUBLIC_BASE_PATH: basePath },
      trailingSlash: true,
      images: { unoptimized: true },
    }
  : {
      ...shared,
      // Everything the project already had goes here, unchanged:
      // headers(), redirects(), rewrites(), cacheComponents and the like.
    };

export default nextConfig;
```

### `preview-hosted.mjs`

```js
// Serves ./out the way the Clever AI Exchange does: under /t/<slug>/ and nowhere else.
// From the project folder:  node ~/enablements/preview-hosted.mjs <slug>
import http from "node:http";
import fs from "node:fs";
import path from "node:path";

const slug = process.argv[2];
if (!slug) {
  console.error("Usage: node preview-hosted.mjs <slug>");
  process.exit(1);
}
const base = `/t/${slug}`;
const out = path.resolve("out");
if (!fs.existsSync(path.join(out, "index.html"))) {
  console.error(`No out/index.html here. Run: ENABLEMENT_BASE_PATH=${base} npm run build`);
  process.exit(1);
}
const types = {
  ".html": "text/html; charset=utf-8", ".js": "text/javascript", ".css": "text/css",
  ".json": "application/json", ".txt": "text/plain", ".svg": "image/svg+xml",
  ".png": "image/png", ".jpg": "image/jpeg", ".jpeg": "image/jpeg", ".gif": "image/gif",
  ".webp": "image/webp", ".ico": "image/x-icon", ".woff2": "font/woff2", ".mp4": "video/mp4",
};

http
  .createServer((req, res) => {
    const url = decodeURIComponent(new URL(req.url, "http://localhost").pathname);
    if (url !== base && !url.startsWith(base + "/")) {
      // Browsers ask for /favicon.ico on their own; that one is not the enablement's doing.
      if (url !== "/favicon.ico") console.log("OUTSIDE THE PREFIX (would be missing on the Exchange):", url);
      res.writeHead(404).end(`Not under ${base}`);
      return;
    }
    const rel = url.slice(base.length).replace(/^\/+|\/+$/g, "");
    const candidates = rel === "" ? ["index.html"] : [rel, `${rel}/index.html`, `${rel}.html`];
    let status = 200;
    let file = candidates.map((c) => path.join(out, c)).find((f) => f.startsWith(out + path.sep) && fs.existsSync(f) && fs.statSync(f).isFile());
    if (!file) {
      status = 404;
      file = path.join(out, "404.html");
      console.log("NOT IN THE BUILD:", url);
      if (!fs.existsSync(file)) {
        res.writeHead(404).end("Not found");
        return;
      }
    }
    res.writeHead(status, { "Content-Type": types[path.extname(file)] ?? "application/octet-stream" });
    res.end(fs.readFileSync(file));
  })
  .listen(4173, () => console.log(`Open http://localhost:4173${base}/`));
```

There is no tracking kit in this preview, so `lib/enablement.ts` prints each signal to the browser's console as `[enablement] ...`. That is what you check.

### `CLAUDE.md`

For a new project, fill in all of it. For an enablement that already exists, add the "Progress tracking" and "On the AI Exchange" sections to the project's own `CLAUDE.md` (create one if there is none) and leave the rest of their file alone.

```markdown
# [Enablement name]: an enablement for the Clever AI Exchange

## What this is
A short, interactive lesson that will live on the Clever AI Exchange, Clever's internal site for sharing what people build with AI. A colleague completes it on their own in about [N] minutes.

- **After this enablement, a learner can:** [learning goal, in the team's words]
- **The learner:** [who they are, what they already know, what they're missing]
- **Audience:** [everyone at Clever / team]

## The team
- Subject Matter Expert: [name]. Owns accuracy. Get facts from them; don't invent them.
- Learning Designer: [name]. Owns the learning experience.
- Builder: [name]. Builds the app with you.

You're working with [Builder's first name]. Explain what you're doing in simple, everyday terms, keep steps small, and say what you changed after each one. Be encouraging and specific, and treat errors as a normal part of building.

## How to help
- The team owns the ideas. Don't propose a structure unless they ask; when they ask, give at least two clearly different options.
- Suggest one or two specific ideas at a time that make the enablement more hands-on. Build them only after the team says yes.
- Keep it to about [N] minutes. Speak up if it's growing past that.
- Mark anything you drafted yourself with `// SME CHECK` and keep a list of what still needs review.

## The golden path (don't leave it without asking)
- Next.js (App Router) + TypeScript + Tailwind CSS, built as a static site (`output: "export"`).
- No server-side code, no database, no sign-in, no calls to outside services, no paid services. The Exchange provides sign-in and storage.
- Ask before adding any npm package.
- Content lives in `content/`.
- Link between pages with `next/link`. Import images; where a path has to be typed, wrap it with `asset(...)` from `lib/hosting.ts`.
- Save the learner's place with `localStorage` under one key, and keep it small. Not `sessionStorage`.
- The enablement is never told who the learner is. Don't ask for a name or email.
- Anything off the path: pause and check with an AI Exchange admin first.

## Progress tracking
- `enablement.json` lists the enablement's steps.
- `lib/enablement.ts` reports progress: `enablement.step(id)` when a step is finished, `enablement.answer(id, value, correct)` for answers, `enablement.complete()` once at the end.
- Every step in `enablement.json` is reported from the app, and nothing is reported that isn't listed. Don't rename a step id after publishing.
- The Exchange counts a learner complete when every required step has been reported and `complete()` has been called. Answers are stored and admins can read them, so send the choice and whether it was right, not personal free text.

## On the AI Exchange
- The Exchange hosts a copy of this enablement at `/t/[slug]/` on its enablements address, behind Clever sign-in. `ENABLEMENT_BASE_PATH=/t/[slug] npm run build` makes that copy in `out/`. Built without it, the enablement runs on its own as usual.
- The copy doesn't update itself. After a change: build both ways, preview the Exchange build (`node ~/enablements/preview-hosted.mjs [slug]`), package, and send it to an Exchange admin.

## What can't go in
- Real customer, district, school, student or staff data. Use realistic made-up examples.
- Passwords, keys, tokens or other secrets.
- Anything meant for a smaller group than this enablement's audience.

## How we work
- After each meaningful change, run `npm run build`, then commit with a clear message.
- "Package this for the Exchange" means: check tracking, build with `ENABLEMENT_BASE_PATH=/t/[slug]`, go through that build under its prefix, and make the zip with `bundle/`, `source/` and `enablement.json`.
- Readable on a laptop and a phone, clear headings, good contrast, works with a keyboard.

@AGENTS.md
```
