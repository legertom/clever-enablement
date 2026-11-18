# The Clever enablement skill

A Claude skill for the Clever AI Exchange. Hand it to Claude, and Claude builds an **enablement** with you (a short, interactive lesson a colleague completes on their own), puts one you already built onto the Exchange, or updates one that is already live.

You don't need any coding experience. Claude does the technical work and explains each step in plain words.

Owner: **Katie Clarkson**. Questions go to Katie or any AI Exchange admin.

## 1. Get the skill

On the AI Exchange, open **New → Publish an enablement** and click **Download the Claude skill**. Or get it here:

1. Click **[SKILL.md](SKILL.md)**.
2. Near the top right of the file, click the **download** button (⬇).
3. The file lands in your **Downloads** folder.

## 2. Give it to Claude

1. Open **Claude Code** in your enablement's folder. The Code tab of the Claude desktop app works, and so does Claude Code in VS Code. No Claude Code or no enablement yet? Open any Claude instead, and it gets you set up.
2. Drag **SKILL.md** into the message box.
3. Type what you want and press **Return**:

| You want to | Type this |
| --- | --- |
| Change one that is already live | `Update my enablement on the AI Exchange.` |
| Put one you already built on the Exchange | `Get my enablement onto the AI Exchange.` |
| Build a new one | `Help me build an enablement.` |

Claude saves the skill on your Mac the first time. After that, open Claude Code in your enablement's folder and just ask.

## 3. Send it to the Exchange

Claude packages your enablement into one file. There are two ways to send it. Both run the same checks and end in the same place.

| | The Publish page | Ask Claude |
| --- | --- | --- |
| Where it works | Any Claude Code, the desktop app included | Claude Code in VS Code only |
| Setting up | Nothing | About five minutes, once |
| What you do | Drag one file onto the Exchange's Publish page and press **Publish now** | Say "go" |

**Not sure which? Use the Publish page.** It needs no setting up and no VS Code.

It is live as soon as you publish it. Nobody has to approve it. An admin looks first only when the Exchange's checks flag something, and you are told why.

## Good to know

- **You can update what you own.** The Exchange takes a new version from an enablement's owner and from the collaborators credited on its catalog page. Yours are listed under **Your enablements** on the Publish page.
- **An update replaces the live version at once.** Anyone part-way through keeps their place.
- **GitHub is required.** Every enablement's project is kept in a private GitHub repository, so it isn't only on one Mac and a teammate can pick it up. No account yet? Claude helps you make one. It's free.
- **Letting Claude publish** needs a token with the `enablements:write` permission, and works only in VS Code: the Claude desktop app at Clever does not allow the connection. Claude walks you through it if you want it.
- **Feedback is built in.** When someone finishes, the Exchange asks them for a star rating and a comment. Don't build your own.
- **What can't go in an enablement.** Real customer, district, school, student or staff data, and passwords or keys. Use realistic made-up examples.
- **This folder is a Claude skill** named `clever-enablement`. Claude Code keeps its copy at `~/.claude/skills/clever-enablement`.
