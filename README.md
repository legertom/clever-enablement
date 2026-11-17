# Build an enablement for the Clever AI Exchange

A guide you hand to Claude. Claude then sets up your Mac and walks you and your team through building an **enablement**: a short, interactive lesson a colleague can complete on their own in about 30 minutes. Finished enablements live on the Clever AI Exchange, behind Clever sign-in, and the Exchange records who started and finished them.

**Already built an enablement?** The same guide gets it onto the Exchange. See [Already have an enablement](#already-have-an-enablement).

You don't need any coding experience. The first-time setup takes about an hour, and some of that is waiting while things install.

You do need a **GitHub account**. It's free, and if you don't have one, Claude helps you make it. See [Why GitHub](#why-github).

Owner and author: **Katie Clarkson**. Questions go to Katie or any AI Exchange admin.

## What you'll end up with

- Claude Code and VS Code on your Mac
- A GitHub account, with your project kept in a private repository only you and the people you invite can open
- A secure connection between Claude and the AI Exchange, if you want one
- Your own enablement project, which you change by asking Claude in plain English
- A packaged enablement, which Claude publishes on the Exchange when you say go

## Step 1: Download the guide

1. Click **[SKILL.md](SKILL.md)** to open it.
2. Near the top right of the file, click the **download** button (⬇). When you hover over it, it says "Download raw file".
3. The file lands in your **Downloads** folder.

## Step 2: Drop it into Claude

1. Open Claude: the Claude app, [claude.ai](https://claude.ai), or Claude Code if you already use it.
2. Drag **SKILL.md** from your Downloads folder and drop it into the message box.
3. Press **Return**.

That's it. Claude reads the guide and takes it from here. If you started in a regular chat, Claude helps you open Claude Code, which is where the building happens.

## Why GitHub

Every enablement's project is kept on GitHub. It is required, and here is why it's worth it:

- **Your work is safe.** The project isn't only on your Mac. If the Mac is lost or replaced, nothing is.
- **Every version is kept.** You can always go back to how it was last week.
- **A teammate can pick it up.** You invite the people who should have access, and the enablement can still be updated when you're out or on another team.

**It can be private, and Claude always makes it private.** A private repository can be opened only by you and the people you invite. Putting your project on GitHub does not make your enablement public. Colleagues still reach it only through the Exchange, behind Clever sign-in.

**No account yet?** Claude walks you through making one, a screen at a time. It's free, and the free plan includes private repositories. You choose your own password and Claude never sees it. If you already have a GitHub account, personal or work, you can use it.

## Already have an enablement

If you built an enablement at Campfire, at a hackathon, or on your own, you don't start over. Claude adds two small things to it: a way to build it that the Exchange can host, and the signals that tell the Exchange who finished. Your enablement's own site keeps working exactly as it does now.

1. Download the guide (Step 1 above).
2. Drop **SKILL.md** into Claude, the same way.
3. Type this with it and press **Return**:

   ```
   Get my enablement onto the AI Exchange.
   ```

If you already use Claude Code, do this with Claude Code open in your enablement's project folder. If you don't, Claude gets you there.

Claude checks that the enablement fits, makes the changes on a separate branch, proves both versions still build, and packages it. If the project isn't on GitHub yet, Claude puts it there in a private repository. If it already is, it stays where it is. Then Claude publishes it on the Exchange when you say go, or you add the package on the Exchange's Publish page yourself.

Before you publish, have these ready: the full name of everyone on the team as it appears on the Exchange, and the team's OK for it to be listed and tracked. You will be its owner; add your collaborators on its catalog page afterwards, and they can see its results too.

## Coming back later

Open Claude Code in your enablement's project folder and say what you want to do, for example "Add a section about ___", "Is tracking still correct?", "Package this for the Exchange" or "Publish this to the Exchange". On a new Mac, ask Claude to get your project from GitHub first.

## Good to know

- **Publishing.** It is yours to publish, and there are two ways. Ask Claude to "publish this to the Exchange": it sends the package, tells you what the Exchange's checks found, and publishes it when you say go. Or do it by hand: on the Exchange, open **New → Publish an enablement** and add the file Claude packaged. Either way the Exchange checks it on the spot, and it is live in the catalog under your name straight away, or you can preview it at its real address first. Nobody has to approve it. An admin looks first only when the checks flag something, and you are told why.
- **Letting Claude publish.** Claude can publish only if the token you made for it has the `enablements:write` permission. A token from before 16 November 2026 does not. Claude will tell you if yours needs replacing. It also works only in VS Code: the Claude desktop app at Clever does not allow the connection. You can skip the connection altogether and add the file on the Publish page yourself.
- **Feedback is built in.** When someone finishes, the Exchange asks them for a star rating and a comment. You don't build that yourself. You see every rating and comment under **Your enablements** on the Publish page.
- **What the Exchange records.** Which steps each learner finishes, their answers, how long each step takes, and when they complete it. Exchange admins can see it, and so can you and the collaborators credited on your enablement. Its page on the Exchange tells learners so before they start.
- **Updates.** The Exchange holds a copy of your enablement as it was when you published it. To update it, change your project, ask Claude to package it again, and publish the new package. The new version replaces the live one as soon as you publish it.
- **What can't go in an enablement.** Real customer, district, school, student or staff data, and passwords or keys. Use realistic made-up examples. The same goes for its GitHub repository, even though it is private.
- **This guide is also a Claude skill.** The folder can be installed as a skill named `clever-enablement`.
