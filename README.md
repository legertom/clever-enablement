# Build an enablement for the Clever AI Exchange

A guide you hand to Claude. Claude then sets up your Mac and walks you and your team through building an **enablement**: a short, interactive lesson a colleague can complete on their own in about 30 minutes. Finished enablements live on the Clever AI Exchange, behind Clever sign-in, and the Exchange records who started and finished them.

**Already built an enablement?** The same guide gets it onto the Exchange. See [Already have an enablement](#already-have-an-enablement).

You don't need any coding experience. The first-time setup takes about 45 minutes, and some of that is waiting while things install.

Owner and author: **Katie Clarkson**. Questions go to Katie or any AI Exchange admin.

## What you'll end up with

- Claude Code and VS Code on your Mac
- A secure connection between Claude and the AI Exchange
- Your own enablement project, which you change by asking Claude in plain English
- A packaged enablement, ready for an Exchange admin to publish

## Step 1: Download the guide

1. Click **[SKILL.md](SKILL.md)** to open it.
2. Near the top right of the file, click the **download** button (⬇). When you hover over it, it says "Download raw file".
3. The file lands in your **Downloads** folder.

## Step 2: Give it to Claude

**Already using Claude Code?** That means the **Code** tab in the Claude desktop app, or the Claude Code extension in VS Code.

1. Open Claude Code.
2. Copy this line, paste it into the message box and press **Return**:

   ```
   Read ~/Downloads/SKILL.md and let's get started.
   ```

**Never used Claude Code, or not sure?**

1. Open the Claude app, or go to [claude.ai](https://claude.ai), and start a new chat.
2. Drag the file from your Downloads folder into the message box, then press **Return**.
3. Claude will welcome you and help you open Claude Code. You'll finish there.

That's it. Claude takes it from here.

## Already have an enablement

If you built an enablement at Campfire, at a hackathon, or on your own, you don't start over. Claude adds two small things to it: a way to build it that the Exchange can host, and the signals that tell the Exchange who finished. Your enablement's own site keeps working exactly as it does now.

1. Download the guide (Step 1 above).
2. Open Claude Code **in your enablement's project folder**.
3. Paste this line and press **Return**:

   ```
   Read ~/Downloads/SKILL.md and get this enablement onto the AI Exchange.
   ```

Claude checks that the enablement fits, makes the changes on a separate branch, proves both versions still build, and writes the message for you to send to an Exchange admin.

Before you send it, have these ready: the full name of everyone on the team as it appears on the Exchange, who should own the catalog entry, and the team's OK for it to be listed and tracked. Anyone you want credited needs to have signed in to the Exchange at least once.

## Coming back later

Open Claude Code in your enablement's project folder and say what you want to do, for example "Add a section about ___", "Is tracking still correct?" or "Package this for the Exchange".

## Good to know

- **Publishing.** The AI Exchange hosts enablements, and publishing is done by hand for now: Claude packages your enablement, you send it to an Exchange admin, and they add it to the Exchange under your name. It isn't instant. There is no upload page yet; the top of the guide says what is live and will be updated when that changes.
- **What the Exchange records.** Which steps each learner finishes, their answers, how long each step takes, and when they complete it. Exchange admins can see it, and your enablement's page on the Exchange tells learners so before they start.
- **Updates.** The Exchange holds a copy of your enablement as it was when it was published. To update it, change your project, ask Claude to package it again, and send the new package.
- **What can't go in an enablement.** Real customer, district, school, student or staff data, and passwords or keys. Use realistic made-up examples.
- **This guide is also a Claude skill.** The folder can be installed as a skill named `clever-enablement`.
