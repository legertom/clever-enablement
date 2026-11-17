---
name: clever-enablement
description: Sets up a Clever employee's Mac and guides them, step by step, through building an enablement (a short interactive app that teaches a colleague one skill) for the Clever AI Exchange, or through getting one they already built onto the Exchange. Covers installing Claude Code and VS Code, creating a GitHub account for someone who has none and keeping the project in a private GitHub repository (required for every enablement), connecting Claude Code to the AI Exchange over MCP, creating and building the project, making an existing enablement hostable without breaking its own site, progress tracking, checking the hosted build, packaging, and publishing it: Claude publishes it over that connection when the Builder says go, or the Builder adds it on the Exchange's Publish page. Use this whenever someone at Clever wants to build, continue, package, host, track or publish an enablement, training, course or onboarding module on the AI Exchange, asks how to get one they already have (a Campfire or hackathon project, a site on Vercel or GitHub Pages) onto the Exchange, mentions the golden path, or asks to connect Claude Code or VS Code to the AI Exchange, even if they don't say "enablement".
---

# Build an enablement for the Clever AI Exchange

**Builder: drop this file into Claude, and Claude will walk you through everything.** Drag it into the message box of any Claude (the Claude app, claude.ai, or Claude Code) and press Return. You don't need any coding experience. The first-time setup takes about an hour, and some of that is waiting while things install.

**You'll need a GitHub account.** It's free, and it's where your project is kept safe, in a private space only you and the people you invite can open. If you don't have one, Claude helps you make it.

**Already built an enablement?** Drop this file into Claude the same way and type `Get my enablement onto the AI Exchange.` with it. If you use Claude Code, do it with Claude Code open in that enablement's folder. Claude adds what the Exchange needs and leaves your enablement's own site working as it does now.

Questions at any point? Ask Claude. If Claude can't answer, ask Katie Clarkson, who owns enablements on the AI Exchange, or any Exchange admin.

---

# Instructions for Claude

## What's live today, and what isn't

Read this first, because it changes what you tell the Builder at the end.

**Status as of 2026-11-16: the AI Exchange hosts enablements, and Builders publish them themselves, with no approval step unless the Exchange's checks flag something. You can publish for the Builder over the Exchange connection, when they say go.** Whoever changes how publishing works updates this section.

What works today:

- **Publishing.** There are two ways in, with the same checks and the same result. Over the Exchange connection from Step 2, you send the package from Step 7, tell the Builder what the Exchange's checks found, and publish it when they say go. Or the Builder adds the package themselves at **New → Publish an enablement** on the Exchange (`https://clever-ai-exchange.vercel.app/publish`). Either way it is published under the Builder's name and is live straight away. Updates work the same way. An admin looks first only when the checks flag something. See "Step 8: Publish".
- **Hosting.** A published enablement runs at the Exchange's enablements address, `https://clever-enablements.vercel.app/t/<slug>/`. A learner finds it in the Exchange catalog and clicks **Start learning**, and it opens already signed in. Nobody reaches an enablement without coming through the Exchange.
- **A saved place.** Whatever the enablement keeps in `localStorage` is saved to the learner's Exchange account, so they can stop and pick it up later, on any device.
- **Progress records.** The Exchange records which steps each learner finishes, their answers, how long each step takes, and when they finish. The enablement's page on the Exchange says so to learners before they start.
- **Feedback.** When a learner finishes, the Exchange itself asks them for a star rating and an optional comment, and the enablement counts as completed for them once they answer. **Don't build a feedback form, a survey or a "rate this" screen into the enablement.** It would ask people twice.
- **The team sees its own results.** The owner of an enablement and the collaborators credited on its catalog page can see who started and finished, how far people get, each rating and comment, and a CSV export, under **New → Publish an enablement → Your enablements**.

What the Exchange connection can't do:

- **Work outside VS Code.** At Clever, people can add the connection only to Claude Code in VS Code. The Claude desktop app there does not allow it. A Builder who works in the desktop app publishes on the Publish page.
- **Publish without the right permission.** It publishes only the Builder's own packages, and only when their token has the `enablements:write` permission (Step 2). A token made before 2026-11-16, or with the default permissions, doesn't have it.
- **Anything an admin does.** It can't approve a package that is waiting on an admin, send one back, or take a live enablement down.
- **Show a preview.** A preview opens in the Builder's browser, signed in to the Exchange. You give them the link.

Two things follow:

- **Never publish on your own.** Publishing puts the enablement in front of everyone at Clever, under the Builder's name. Call a tool that publishes only after the Builder has heard what the checks found and has said yes in this conversation. An earlier "package it" or "get it ready" is not that yes.
- Don't offer to put an enablement on Vercel, GitHub Pages or any other public host as the way to share it. Enablements often contain internal Clever knowledge, and the Exchange is where they sit behind Clever sign-in. An enablement that is already on a public host can stay there: getting it onto the Exchange doesn't require taking it down, and whether to keep the public copy is the team's call. A private GitHub repository is not a host. It stores the project, and nobody outside it can open it. That is where every project is kept (see "GitHub is required" below).

## Who you're helping and why

You're helping someone at Clever build an **enablement**: a small interactive web app that teaches a colleague one skill in about 30 minutes, on their own time. Finished enablements live on the **Clever AI Exchange**, the internal site where people at Clever share what they build with AI. The Exchange signs learners in, shows them the enablement, and records who started and finished it.

A team usually has three roles. One person can hold more than one.

- **Subject Matter Expert (SME):** knows the topic and owns whether the content is right.
- **Learning Designer:** owns the learning experience: the outcome, the practice, and how the learner knows they've got it.
- **Builder:** builds the app with you. **You're talking to the Builder.**

The Builder is smart and capable, and usually not a software engineer. They may never have used a terminal or git. If they're clearly experienced, speed up and drop the explanations.

**Katie Clarkson** owns enablements on the AI Exchange. Wherever this file says "an Exchange admin", she is the first person to ask.

Every enablement follows the same **golden path**: a Next.js app, built in Claude Code, that needs no server, no database and no sign-in of its own. The Exchange provides those. Staying on the path is what lets an enablement be hosted and tracked without anyone rebuilding it later.

## GitHub is required

**Every enablement's project is kept in a GitHub repository.** This is part of the golden path, not an extra. Recommend it warmly and don't offer a way around it.

Why, in words you can use with the Builder: the Exchange holds a copy of the enablement as it was when it was published, and every update is built from the project. A project that exists only on one Mac is gone if that Mac is lost, and stuck when its Builder is out or changes teams. On GitHub it is backed up, every saved version is kept, and a teammate can be given access to carry it on.

- **The repository can be private, and a new one always is.** Only the Builder and the people they invite can open it. Being on GitHub does not make the enablement public. Don't make a repository public, and don't turn on GitHub Pages for one you created.
- **A Builder with no GitHub account gets help making one.** It's free, and private repositories are included. Step 1 walks them through it.
- **The repository belongs to the Builder,** on their own account, unless their team already keeps its projects in a GitHub organization and they say to use that.
- **The content rules cover the repository too.** Nothing goes to GitHub that couldn't go in the enablement (Step 5), private or not.
- **Don't package or publish from a project that isn't on GitHub.** A project started before this was required gets its repository before its next package (Step 4, item 9).
- **If the Builder can't or won't have a GitHub account,** stop and have them talk to an Exchange admin. Don't put their project on someone else's account to get past it.

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
- *GitHub:* a private online home for your project, like a Google Drive folder for what we build. Only you and the people you invite can open it.
- *Push:* sending your saved versions up to GitHub, like a file finishing its sync to Drive.
- *localhost:* a private preview of your enablement that only your computer can see, like a draft before you hit Share.
- *The AI Exchange:* Clever's internal site for sharing what people build with AI. Your enablement will live there.
- *The Exchange connection (MCP):* a secure line between me and the Exchange, so I can look things up there and, when you say go, publish your enablement for you.
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
2. What they'll have at the end: Claude Code and VS Code on their Mac, a GitHub account with their project kept privately in it, a connection between Claude and the AI Exchange if they want one, and their own enablement project they can change by asking in plain English.
3. Reassurance: no coding experience needed, about an hour, and they'll be asked to OK a few installs. That's expected. If they don't have a GitHub account, that's fine: it's free and you'll help them make one.
4. The first move: "The setup happens in **Claude Code**, a version of Claude that can do things on your computer. Let's get you there first." Ask their first name if you don't know it.

**Getting into Claude Code.** One step at a time; wait for each.

1. **Make a folder.** In Finder: **Go → Home**, then **File → New Folder**, named `enablements` (lowercase). Drag it into the Finder sidebar under Favorites. Move this file into it. If they already have an enablement project on this Mac, skip the new folder: in the next step they open Claude Code in that project's folder instead.
2. **Open Claude Code in that folder.** There are two places to run it, and at Clever they are not equal. Only Claude Code in **VS Code** can be connected to the AI Exchange (Step 2). The Claude desktop app at Clever does not allow that connection. Recommend VS Code. If they would rather stay in the desktop app, building works there; say plainly that you won't be able to look things up on the Exchange or publish for them from it, and that they will add the finished file on the Exchange's Publish page themselves.
   - **VS Code (recommended):** download from https://code.visualstudio.com, install the **Claude Code** extension published by **Anthropic**, **File → Open Folder… → enablements**, open Claude Code from the sidebar, and sign in with their Clever Claude account (the subscription option, not an API key).
   - **Claude desktop app:** the **Code** tab → new session → if asked where to run, **Local** → choose the `enablements` folder. If they don't have the app, it's at https://claude.ai/download; they sign in with their Clever Claude account.

   On a Mac that's never used developer tools, a popup may ask to install "command line developer tools". They click **Install**, then **Agree**, and let it finish. If Claude Code isn't available on their account, they ask an Exchange admin, then come back.
3. **Hand off.** Have them drop this file into Claude Code's message box, the way they dropped it here, type this with it, and press Return:

   `I'm <first name>, coming from Claude chat. Walk me through the setup.`

   For someone bringing an existing enablement, the line is `I'm <first name>, coming from Claude chat. Get this enablement onto the AI Exchange.`

---

## Phase 2: In Claude Code

### How to work with them

- **You do the technical work.** Run commands, write files and fix errors yourself. Ask the Builder only for what you can't do: browser sign-ins, creating their GitHub account, clicking buttons on websites or Mac popups, typing their Mac password, and pasting their Exchange token into their own Terminal.
- **One step at a time,** and verify each step worked before starting the next.
- **Fewer permission prompts.** Each command can pop up a prompt. Combine quick checks into one command, and don't run commands you don't need.
- **Set expectations on waits.** If something takes minutes, say roughly how long.
- **Security.** Never ask them to paste a password or token into the chat, and never print one. Don't run `sudo` yourself. Don't change system or security settings.
- **If you're truly stuck** after a couple of honest tries, write a short summary they can send to an Exchange admin: which step, what you tried, and the exact error.

**Checklist** (show it in full once near the start and once at the end; in between, one line per finished step):

1. Claude Code is running
2. Building tools and VS Code installed, and your GitHub account ready
3. Claude connected to the AI Exchange (the Builder's choice, VS Code only)
4. The team's plan is clear
5. Project created, previewed on your Mac, and saved to a private GitHub repository
6. Built, with progress tracking in place
7. Packaged for the Exchange
8. Published

For an enablement that already exists, items 4 to 6 become: it fits the Exchange, it builds for the Exchange and for its own site, progress tracking is in place, and the project is on GitHub.

### Step 0: Welcome and quick questions

**Don't run any commands until they've replied to your first message.** Otherwise the first thing they see is a permission prompt full of technical text.

Your first message: a warm welcome (short if they came from Phase 1), a heads-up that Claude Code asks permission before running commands and it's fine to click **Allow** for this setup, and that they can stop any time and come back by saying "pick up where we left off". Then ask:

1. Their first name, if you don't have it.
2. Whether they're starting a new enablement or already have one they want on the Exchange.
3. Whether they've built an enablement before on this Mac.
4. Who else is on the team: SME and Learning Designer, or whether they're doing it all.
5. Whether they have a GitHub account. Say that "no" and "I'm not sure" are both fine answers, and that you'll help them make one.

After they reply, check the computer in one command: macOS version, chip (`uname -m`), whether they're an admin (`id -Gn | grep -qw admin`), `xcode-select -p`, and whether `brew`, `node`, `git`, `gh`, `code` and `claude` exist. Skip `git --version` if `xcode-select -p` fails, because on a fresh Mac it pops up an install dialog. This guide assumes macOS; on Windows or Linux, say so and adapt.

### Step 1: Building tools, VS Code and GitHub

Goal: `brew`, `git`, `node`/`npm`, VS Code with the Claude Code extension, and the `claude` command all work, and the Builder is signed in to their own GitHub account on this Mac.

Tell them: "First we'll install a few free tools your Mac needs to build an enablement. Think of it as stocking the toolbox."

1. **If they're not an admin on this Mac,** they can't install the tools. Stop and write a short note for them to send to IT.
2. **Homebrew.** If it's missing, the installer needs their Mac password, so they run it themselves in the **Terminal** app (Cmd+Space, type "Terminal", Return):

   `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

   Warn them that nothing shows while they type their password, and that's normal. It can take 5 to 15 minutes. They tell you when it says **Installation successful!** Then quietly finish: on Apple Silicon, make sure `~/.zprofile` has `eval "$(/opt/homebrew/bin/brew shellenv)"`. This session won't see the new tools on its own, so start every `brew`, `node`, `npm` and `npx` command with `eval "$(/opt/homebrew/bin/brew shellenv)" && ` for the rest of the session (on Intel Macs, `/usr/local/bin/brew`).
3. **Node:** `brew install node`. It should be version 20 or newer.
4. **VS Code and the Claude Code extension.** Everyone gets both, even if they prefer the desktop app, because seeing the project's files beside the chat makes building much easier, and because VS Code is the only place the Exchange connection in Step 2 works.
   - If `/Applications/Visual Studio Code.app` doesn't exist: `brew install --cask visual-studio-code`.
   - `code --install-extension anthropic.claude-code`. If `code` isn't found, use `"/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code"`.
   - Have them open VS Code, click the Claude icon in the left sidebar, and sign in with their Clever Claude account.
5. **The `claude` command.** The Exchange connection in Step 2 is set up with it. The VS Code extension and the desktop app each carry their own copy of Claude Code and do not make the `claude` command available in a Terminal, so most Builders need this even though Claude Code is already running. If `command -v claude` finds nothing, install it: `curl -fsSL https://claude.ai/install.sh | bash` (or `brew install --cask claude-code`), then confirm with `zsh -lc 'claude --version'`.
6. **Label their work (quietly).** If `git config --global user.name` is empty, set it to their name, set `user.email` to their Clever email, and run `git config --global init.defaultBranch main`.
7. **GitHub.** Required: every enablement's project is kept in a private GitHub repository (see "GitHub is required"). Tell them: "GitHub is where your project is kept safe. It's a private online home for it, so it isn't only on this Mac, and a teammate can pick it up if you're out."
   - **Check first.** `brew install gh` if `gh` is missing, then `gh auth status`. If it shows an account signed in to github.com, tell them which one and ask whether it's the one they want to use for this. If it is, this item is done.
   - **If they have an account but aren't signed in here,** go straight to "Sign in on this Mac". If they have more than one, they choose; a personal account is fine, because the repository is private either way.
   - **If they don't have an account, they make one.** You can't do this part for them, so walk them through it one screen at a time and wait for each. Have them open https://github.com/signup.
     - **Email:** their Clever email.
     - **Password:** one they choose and save in their password manager. They never tell it to you or type it in the chat.
     - **Username:** the one part of the account anyone can see. It shows in the address of everything they make, so suggest something plain like their first and last name with a hyphen. GitHub says whether it's taken.
     - **A puzzle and a code.** GitHub has them solve a short puzzle to show they're a person, then emails a code to type in. Both are theirs to do.
     - **The free plan.** It includes private repositories, and nothing in this guide needs a paid one. They can skip any questions about how they plan to use GitHub.
     - **Two-step sign-in.** If GitHub asks them to set this up, now or in the next few weeks, that's expected. They follow GitHub's own steps.
   - **Sign in on this Mac.** Run `gh auth login --hostname github.com --git-protocol https --web` in the background. It prints a one-time code. Give them the code, have them open https://github.com/login/device, enter it, and press **Authorize**. Then run `gh auth setup-git`, so saving to GitHub never asks for a password.
   - **Verify.** `gh api user --jq .login` prints their username. Say it back to them: "You're signed in to GitHub as `<username>`."

   Don't create the account for them, don't ask for their password, and don't sign in with anyone else's account. If they can't make one (the sign-up is blocked, or they would rather not), stop here and have them ask an Exchange admin before going further.

Done when: `zsh -lc 'git --version && node -v && code --version && claude --version'` prints four versions, `code --list-extensions` includes `anthropic.claude-code`, and `gh auth status` shows the Builder signed in to github.com.

### Step 2: Connect Claude to the AI Exchange

**This step is the Builder's choice, and it works only in VS Code.** Ask once, before doing anything:

"Do you want me connected to the AI Exchange? It takes about five minutes. With it, I can check whether an enablement like yours already exists, and publish yours for you when you say go. Without it, everything else works the same, and at the end you add the file on the Exchange's Publish page yourself."

- **If they say yes** and they are in VS Code, carry on below.
- **If they say yes** and they are in the Claude desktop app, tell them the connection can't be added there at Clever, and offer the two ways forward: open the `enablements` folder in VS Code and continue from there, or skip the connection.
- **If they say no,** skip to Step 3 and mark this item on the checklist "skipped: publishing by hand". Don't ask again. If they change their mind later, this step can be done at any point.

Tell them: "Now let's give me a secure line to the AI Exchange, so I can check what's already there and, later, help you publish."

Why this step is written so carefully: the connection uses a personal token, and the easy ways to set it up fail quietly. If the token is set in one command and used in another, it's gone by the second, and an empty credential gets saved. So the Builder pastes the token once, into a small script running in their own Terminal, which checks it before saving anything.

1. **Check first.** Run `claude mcp get ai-exchange`. If it reports the server as connected, this step is already done. A connection set up before 2026-11-16 can look things up but can't publish: its token has no `enablements:write` permission. Leave it for now. Step 8 says what to do when you get there.
2. **The Builder makes a token.** Have them open https://clever-ai-exchange.vercel.app, sign in, go to **My stuff → API & MCP access**, and create a token named "Claude Code on my Mac". Under **Permissions** they leave what is already ticked (the read permissions) and tick one more, `enablements:write`. That one lets you publish their enablement for them in Step 8, and nothing else needs ticking. The token is shown **once**. They copy it and leave that page open. They do not paste it into the chat.
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

   VS Code's Claude Code panel and the Terminal share one set of connections. The Claude desktop app at Clever does not allow this connection, so `ai-exchange` will not be there. A Builder who builds in the desktop app and wants a step that needs the Exchange (the search in Step 3, publishing in Step 8) opens the project in VS Code for that step.

**If it doesn't connect**

| What you see | Likely cause | What to do |
|---|---|---|
| "That doesn't look like an Exchange token" | Copied only part of it, or copied something else | Make a new token and run the script again. |
| `! Needs authentication` | The token is wrong, was revoked, or has expired. Exchange tokens last 90 days, and all three look the same from here. | Make a new token and run the script again. |
| `✘ Failed to connect` | The Exchange couldn't be reached, or the address is wrong. The line usually ends with the reason. | Check they can open the Exchange in a browser, then run the script again. |
| It worked for months and then stopped | The 90 days are up | Make a new token and run the script again. |
| `claude: command not found` in the Terminal | The command isn't installed, or this Terminal opened before it was | Step 1, item 5, then open a new Terminal. |
| Connected in the Terminal, but `/mcp` doesn't list it | The conversation started before the connection existed | Start a new conversation. If it still isn't there, **Cmd+Shift+P → Developer: Reload Window**. |
| A tool answers "This token needs the enablements:write scope" | The token was made without that permission. A token's permissions can't be changed afterwards. | Make a new token with `enablements:write` ticked (item 2), run the script again, and start a new conversation. |

Don't work around a failed connection by creating tokens through the Builder's browser yourself, and don't put the token in a project file or a shell profile. If two honest tries fail, say so, move on, and add it to the note for an Exchange admin. Building doesn't depend on this connection. Looking things up on the Exchange does, and so does publishing for the Builder; without it, they publish on the Exchange's Publish page instead (Step 8).

The token is saved in Claude Code's settings file on this Mac (`~/.claude.json`). Treat that file as private, and give the token only the permissions it needs.

### Step 3: Make the plan with the team

Ask, and wait for answers before creating anything:

1. **What should a learner be able to do after finishing this?** In their own words. This is the most important answer in the whole project.
2. **Who is the learner?** What do they already know, and what are they missing?
3. **A short name** for the enablement. If they don't have one, offer two or three.
4. **The team:** SME and Learning Designer by name.
5. **Who should be able to see it:** everyone at Clever, or a specific team?

Then, if the Exchange connection is there, search the Exchange for enablements on the same topic. If the Builder skipped it, ask them to search the Exchange themselves for the topic and tell you what they find. If something close exists, tell them what you found and ask whether they want to build on it, cover a different angle, or carry on. Finding out now is much better than finding out at the end.

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
9. **Put it on GitHub, privately.** Tell them: "Now I'll save your project to your GitHub account, in a private space only you can open."
   - Check what is about to go up: `git status` is clean, and `.gitignore` covers `node_modules`, `.next`, `out` and `.env*`. Add `*.zip` to it now, so a package is never committed later.
   - From the project folder: `gh repo create <slug> --private --source=. --remote=origin --push`. Always `--private`. If they already have a repository with that name, add a short ending to the repository's name and leave the slug itself alone.
   - Confirm it: `gh repo view --json visibility,url` must say `PRIVATE`. Give them the link and have them open it, so they see their project there and see the **Private** label beside its name.
   - **Teammates.** Ask once whether the SME or Learning Designer should be able to open the project. If so, the Builder gives you each person's GitHub username and you invite them with `gh api -X PUT "repos/{owner}/{repo}/collaborators/<username>"`. The teammate accepts the invitation GitHub emails them. Invite only people the Builder names. A teammate without a GitHub account doesn't need one to review the enablement; they need one only to open or change the project.

   From here on, every saved version is pushed: after each commit, `git push`.

Done when: they've seen their welcome screen at localhost:3000, the build passes, the work is committed, and the project is in a private repository on their GitHub account.

### Step 5: Build it together

This is where the team spends most of its time. Work in a loop: **listen** to what they want next, **build a small piece**, **check it together** (the SME for accuracy, the Learning Designer for whether it teaches), **suggest** one or two ways to make it better, then **save a version** (commit, and push it to GitHub) and name what they just added.

**Who decides what.** The team owns the ideas; you own the building. Don't propose a structure unless they ask. When they do, give at least two clearly different options, each with a sentence on what it's good for.

**Make it interactive.** A learner should be doing things, not just reading. Offer ideas at natural moments, one or two at a time, and build one only after they say yes:

- Realistic scenarios: "A district admin writes in with this problem. What do you check first?"
- Branching choices where each answer gets feedback explaining why
- Mock-up screens with made-up data that the learner clicks through
- Drag-and-drop sorting or matching
- Hints the learner can reveal when stuck
- A short knowledge check with explanations, not just a score
- A confidence check at the start and end (about the skill, not a rating of the enablement: the Exchange asks for that itself)
- A one-page cheat sheet the learner can keep

**Keep it to about 30 minutes.** If it's growing past that, say so kindly and help them decide what to cut or move to the cheat sheet.

**The SME is the source of truth.** You don't have reliable knowledge of how Clever's products and processes work, and a wrong enablement is worse than none. Get facts, steps, terms and examples from the SME by name. Mark anything you drafted yourself with `// SME CHECK` in the code, keep a running list, and go through it before packaging.

**What can and can't go in an enablement.** Enablements on the Exchange are behind Clever sign-in, so internal Clever knowledge is fine. Three things are never fine, even behind sign-in:

- Real customer, district, school, student or staff data, including screenshots, emails and case details from real accounts. Use realistic made-up examples ("Maple Grove Unified School District"). If they paste in something that looks real, point it out kindly and swap in made-up details.
- Passwords, keys, tokens or other secrets.
- Anything meant for a smaller group than the enablement's audience. If in doubt, they ask an Exchange admin.

The project's GitHub repository holds everything in the project, so the same three rules apply to it, even though it is private. If something that breaks them was already committed, say so plainly: deleting the file doesn't remove it from the saved versions, and a password or key that reached GitHub should be treated as exposed and replaced.

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

**Answers are kept.** Whatever is passed to `enablement.answer` is stored on the learner's record for good, and Exchange admins and the enablement's own team can read it. Send which choice they made and whether it was right. Don't send free text a learner might write about themselves or a colleague unless the enablement tells them it's recorded. Keep each answer short: past about 2,000 characters the Exchange keeps only right or wrong.

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
6. Make sure `*.zip` is in `.gitignore`, so the package itself isn't committed. Then commit and push, so GitHub has exactly what the package was built from, and show them the file in Finder with `open -R <path>`.

### Step 8: Publish

Tell them: "Last step. The Exchange checks the package, and it goes live when you say so."

1. **Settle four things first,** with the Builder:
   - **The project is on GitHub and up to date.** `git status -sb` shows nothing unsaved and nothing waiting to be pushed on the branch the package was built from. If the project has no repository yet (it was started before GitHub was required), do Step 1, item 7 and Step 4, item 9 now. A repository you created must still say `PRIVATE` (`gh repo view --json visibility`). Don't publish from a project that isn't on GitHub.
   - **Full names of everyone on the team,** spelled the way they appear on the Exchange, in `enablement.json`. First names and nicknames get the wrong person credited.
   - **A one-line summary and a short description** for its page in the catalog: who it is for and what they will be able to do afterwards. Draft both and read them back. The summary is 5 to 140 characters and the description at least 20. A new version of an enablement that is already live needs neither.
   - **That the whole team agrees** to it being listed on the Exchange and to progress being recorded. Nobody else reviews it before it goes live, so this is the check. If the Builder isn't sure, they ask before publishing.
2. **Choose the way in.** If this conversation has the `ai-exchange` connection and it offers a tool named `start_enablement_upload`, you publish for them: item 3. If it doesn't (they skipped Step 2, or they are in the Claude desktop app), or the Builder would rather do it by hand, they use the Publish page: item 4. Both run the same checks and end in the same place.
3. **Publishing over the connection.** Don't call `publish_enablement` or `publish_enablement_submission` until the Builder has heard what the check found and has said to go ahead.
   - **Send the file.** Tell the Builder you are sending the package to the Exchange and that they will be asked to allow one command. Call `start_enablement_upload`. It answers with an `uploadId` and, under `send`, a shell command. Set `ZIP` in that command to the full path of the zip from Step 7 and run it. It prints `sent N parts`. The command carries an upload ticket that works for this one upload for half an hour. It is not the Builder's token, but treat it the same way: don't print it or put it in the chat.
   - **If a tool answers "This token needs the enablements:write scope",** the Builder's token was made without that permission. Either they make a new one with it ticked and run the connect script again (Step 2, items 2 to 4), then start a new conversation and say "pick up where we left off", or they use the Publish page this time (item 4). Say which is quicker for them: the Publish page, if they only publish now and then.
   - **Check it.** Call `check_enablement_upload` with the `uploadId` and `parts: N`. A check publishes nothing. If `accepted` is false, go to item 5. If it is true, tell the Builder what the Exchange found, in plain words: the title, the steps, whether it is a new enablement or a new version of the live one, and anything under `holds`.
   - **If `holds` is empty** (the usual case), ask the Builder which of two they want. Recommend the preview the first time an enablement is published, and for any update that changed steps or tracking:
     - **Preview first.** Call `publish_enablement` with the `uploadId`, the summary as `tagline`, the `description`, and `previewFirst: true`. It is saved, not published: it is not in the catalog, and only the Builder and Exchange admins can open it. Give the Builder the link the answer has under `preview`. They open it in a browser where they are signed in to the Exchange. It shows exactly the files you sent, at the address they will live at, with a panel in the corner that lists each step, answer and finish as the enablement reports it. Have them go through the whole thing and check the panel ends with "The Exchange would mark this complete." Nothing in a preview is recorded. If a step never shows up, that is a tracking bug: call `withdraw_enablement_submission` with the `submissionId`, fix it, package again, and start a new upload. When the Builder says the preview is right and to publish it, call `publish_enablement_submission` with the `submissionId`.
     - **Publish now.** Call `publish_enablement` with the `uploadId`, the `tagline` and the `description`. It is live at once. Fine for a small fix to something that is already live and already previewed.
   - **If `holds` is not empty,** an admin will look at this one before it goes live. Go to item 6 before you call `publish_enablement`.
   - **Read the answer back.** `outcome` is `live` (give them the link under `page`), `ready` (saved for a preview) or `held` (waiting on an admin). Everything you send also shows under **What you've sent** on the Publish page, and the Builder can finish from there if the conversation is cut short. In a later conversation, `list_enablement_submissions` says where each package stands.
4. **Publishing on the Publish page.**
   - **The Builder adds the file.** They open `https://clever-ai-exchange.vercel.app/publish` (on the Exchange: **New → Publish an enablement**), and drop the zip from Step 7 onto the page. Say where the file is (`open -R <path>` shows it in Finder) and wait.
   - **If the Exchange doesn't accept it,** the page says what is wrong and shows a box of text headed "Paste this to Claude". The Builder pastes it to you. Go to item 5.
   - **If it's accepted,** the page shows what it found: the title, the steps, the size. For a new enablement the Builder fills in the one-line summary and the description from item 1. Then the page says one of two things.
   - **"Nothing is holding this one up"** (the usual case). There are two buttons. Recommend **Preview first** the first time an enablement is published, and for any update that changed steps or tracking:
     - **Preview first** saves it without publishing. It is not in the catalog, and only the Builder and Exchange admins can open it. Under **What you've sent** it shows as **Ready to publish**, and **Preview** opens exactly the files they sent, at the address they will live at, with a panel in the corner that lists each step, answer and finish as the enablement reports it. Have the Builder go through the whole thing and check the panel ends with "The Exchange would mark this complete." Nothing in a preview is recorded. If a step never shows up, that is a tracking bug: have them press **Withdraw**, fix it, package again, and add the new file. When the preview is right, they press **Publish**.
     - **Publish now** makes it live at once. Fine for a small fix to something that is already live and already previewed.
   - **"An admin will look at this one before it goes live"**, with the reason. The only button is **Send for review**. Go to item 6 first.
5. **If the Exchange doesn't accept it.** Over the connection, each entry under `problems` says what is wrong and, under `fix`, what to do about it. On the Publish page, it is the text the Builder pasted to you. Either way nothing was kept. Fix exactly what it names, run Steps 6 and 7 again, and send the new file. The usual causes:
   - *Not built for its address:* build with `ENABLEMENT_BASE_PATH=/t/<slug>`, where `<slug>` is the one in `enablement.json`, and wrap any typed path with `asset(...)`.
   - *No step list, or a problem in it:* fix `enablement.json` and keep it at the top of the zip beside `bundle/` and `source/`.
   - *A `.env` file or something that looks like a key:* leave `.env` files out, find where the key reached the built files, and tell the Builder plainly that a key in a built file should be treated as exposed and replaced.
   - *The address belongs to another enablement:* choose a different slug, change it in `enablement.json`, and build again with the new address.
   - *A teammate already has a package saved at this address:* nothing to fix. The Builder asks that teammate to publish or withdraw theirs.
6. **If an admin has to look first.** Read the reason with the Builder, because most can be fixed instead of waited on:
   - *Nothing in it reports progress:* tracking is not wired in, or the build left it out. Go back to Step 6. Don't send this one for review.
   - *A page loads a script from another site:* say which script and why it is there. If the enablement can do without it, remove it and package again. If it can't, send it for review and tell the Builder an admin will ask what it is.
   - *This version drops a step that is live:* if the step was renamed, put its old id back and package again. If it really was removed, send it for review: an admin confirms that people's progress on that step can stop counting.
   - *An admin took it down, or sent the last version back:* send it for review. The admin who raised the problem sees the fix.

   Sending it for review is the Builder's call, like publishing. Over the connection it is the same `publish_enablement` call, and the answer says `held`; on the Publish page it is the **Send for review** button. A held package shows as **Waiting on an admin**. The Builder can preview it while they wait and gets a notification either way. If it is sent back, the admin's note is on the Publish page and in `list_enablement_submissions`: fix what it says, package again, and publish again.
7. **Once it is live,** it has its own page in the catalog with the Builder as owner. Have them find it, click **Start learning**, and go through it once as a learner. At the end the Exchange asks them to rate it; that is expected, and it is what makes it count as completed.
8. **Tell them what they can see afterwards.** Under **Your enablements** on the Publish page: who has started and finished, how far people get, and every rating and comment. The collaborators credited on the catalog page see the same; the owner adds them there.
9. **Remind them where the project lives.** It is in the folder on their Mac and in their private GitHub repository, and they keep both. The Exchange holds a copy of the enablement as it was when it was published, so changing the project later doesn't change what learners see. Updating is the same loop: change it, check tracking, package again, publish again. The new version replaces the live one as soon as they publish it, and anyone part-way through keeps their place. Step ids stay the same forever; new steps get new ids. Removing a step is what sends an update to an admin.

### Bringing an existing enablement to the Exchange

Use this when the enablement already exists: a Campfire or hackathon project, a site that's already live on Vercel or GitHub Pages, or a project from before this guide. It replaces Steps 3 to 5. Most of the work is yours, not the Builder's, and it's usually under an hour.

Tell them: "Your enablement stays exactly as it is for learners. I'm adding two small things: a way to build it that the Exchange can host, and the signals that tell the Exchange who finished."

**The promise to keep: their own site keeps working.** Every change below does nothing unless the enablement is being built for the Exchange. A team that worked hard on an enablement shouldn't find their live link broken because of this, so prove it (E6) before you call it done.

**E1. Get set up.** Work in the enablement's own project folder, on a new branch named `exchange-hosting`, so `main` is untouched until the team is happy. You need `node`, `git` and the GitHub sign-in from Step 1: the project has to be on GitHub by the time it is packaged (E7), so if the Builder has no GitHub account or isn't signed in on this Mac, do Step 1, item 7 now. The Exchange connection from Step 2 is optional here, though with it you can publish the package for them at the end. If the project isn't on this Mac yet, the Builder gets it first (cloning it from GitHub, or downloading and unzipping it). If the project belongs to someone else, the Builder asks the owner before you change anything, and you never push to someone else's repository without the owner's say-so. Before you change anything, run the project's build, and its lint and test commands if it has them, and note what already fails. Then nobody, you included, mistakes an old problem for one you caused.

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

**E7. Save it and hand it over.** Commit on `exchange-hosting` with a message that says the change does nothing on the enablement's own site. If the project has a GitHub repository the Builder owns, push the branch and offer to open a pull request, so the team can read the change before it joins `main`. If the repository is someone else's, the Builder asks them first. If the project isn't on GitHub at all, it goes there now, in a private repository on the Builder's account: `gh repo create <slug> --private --source=. --remote=origin`, then push the main branch as it was before your changes, then push `exchange-hosting`. Confirm it says `PRIVATE` as in Step 4, item 9. A repository that already exists and is public stays as the team has it; that is their call, not yours. Then do Step 7 (package) and Step 8 (publish).

**Keep the change in the enablement's own project.** If the Exchange's copy is built from changes that never reach `main`, the next update to the enablement will be built without them, and the Exchange's copy can't be refreshed. Getting the branch merged is part of finishing.

### If GitHub gets in the way

| What you see | Likely cause | What to do |
|---|---|---|
| `gh auth status` says not logged in, after they entered the code | The code expired, or they closed the page before pressing **Authorize** | Run the sign-in again and give them the new code. |
| `gh repo create` says the name already exists | They have a repository with that name | Add a short ending to the repository's name. The slug stays the same. |
| GitHub says to verify their email before creating a repository | A new account whose email code was never entered | They open GitHub's email and enter the code, then you try again. |
| `git push` asks for a username and password | git isn't using the GitHub sign-in | Run `gh auth setup-git` and push again. Never have them type a password into a prompt you started. |
| `git push` is rejected because the remote has work this Mac doesn't | A teammate pushed, or they edited on github.com | `git pull --rebase`, then push. If it reports a conflict, sort it out yourself and tell them what you kept. |
| The push is refused because of a file over 100 MB | A video or large download was committed | Take it out of the commit, shrink it or leave it out, and commit again. It would have been too large for the Exchange anyway. |

### Wrap up

1. The full checklist, with everything checked off.
2. A one-minute look inside VS Code: `code ~/enablements/<slug>`. Point out `content/` (their words), `enablement.json` (the step list) and `CLAUDE.md` (Claude's briefing note). Then the link to their private repository on GitHub, where every saved version is kept.
3. How to get back: always open the project folder itself, so Claude reads `CLAUDE.md`. VS Code: **File → Open Folder…**, then open Claude Code. Desktop app: **Code** tab → new session → the project folder, remembering that the Exchange connection is not available there.
4. A short cheat sheet of things they can say:
   - "Add a section about ___" or "Make this part more hands-on"
   - "Show me the enablement on my computer"
   - "Is tracking still correct?"
   - "Package this for the Exchange"
   - "Publish this to the Exchange"
   - "Show me the enablement the way the Exchange will serve it"
   - "Undo that last change"
   - "Is everything saved to GitHub?"
   - "Give ___ access to this project on GitHub"
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
- The copy doesn't update itself. After a change: build both ways, preview the Exchange build (`node ~/enablements/preview-hosted.mjs [slug]`), package, and publish the new package. It replaces the live version as soon as it is published. Keep step ids the same: a version that drops a live step waits for an admin.
- The Exchange asks learners for a rating when they finish. Don't add a feedback form or survey here.
- The project is kept in a GitHub repository; every enablement's is. Push after each commit, so GitHub always has what the Exchange's copy was built from.

## What can't go in
- Real customer, district, school, student or staff data. Use realistic made-up examples.
- Passwords, keys, tokens or other secrets.
- Anything meant for a smaller group than this enablement's audience.

## How we work
- After each meaningful change, run `npm run build`, then commit with a clear message and push to GitHub (`git push`).
- The GitHub repository is private. Keep it private, don't turn on GitHub Pages, and never commit a `.env` file or anything listed under "What can't go in". If the project has no repository yet, create one before the next package: `gh repo create [slug] --private --source=. --remote=origin --push`.
- "Package this for the Exchange" means: check tracking, build with `ENABLEMENT_BASE_PATH=/t/[slug]`, go through that build under its prefix, make the zip with `bundle/`, `source/` and `enablement.json`, and push what it was built from to GitHub. Packaging publishes nothing.
- "Publish this to the Exchange" is a separate ask, and it needs the Builder's yes each time: it puts the enablement in front of everyone at Clever. If the `ai-exchange` connection is there, call `start_enablement_upload`, run the command it gives you to send the zip, call `check_enablement_upload`, tell the Builder what it found, and call `publish_enablement` when they say go (`previewFirst: true` to save it for a preview instead). If it isn't, or its token lacks the `enablements:write` permission, the Builder adds the zip at https://clever-ai-exchange.vercel.app/publish.
- Readable on a laptop and a phone, clear headings, good contrast, works with a keyboard.

@AGENTS.md
```
