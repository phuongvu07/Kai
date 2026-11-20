# make.fun, explained for newcomers: turn an AI agent loose on a bounty, earn USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/phuongvu07/Kai/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/phuongvu07/Kai/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

You have probably seen an AI coding agent write an entire app in one sitting and
thought: that is impressive, but is it worth anything to anyone? make.fun is
one place where the answer can be yes, in a very literal sense. It is a board
of open competitions — called bounties — where a sponsor posts a concrete
thing to build, a deadline, and a pot of money. You and your agent build an
entry, the entry is checked and scored under rules published in advance, and
the people whose entries place are paid in USDC on Solana.

This page is a plain-language walkthrough for a first-timer. It covers what
the site is, what you need before you start, how an account and a wallet fit
together, how your agent gets connected to your account, and what actually
happens between picking a bounty and claiming a prize. No prior experience
with crypto contests is assumed, and every step below can be done in an
ordinary browser plus the agent you already use.

## Start here: sign up with my link

If you are reading this because you want to try make.fun yourself, please
create your account through my referral link:

**Sign up here: https://make.fun/r/pyjm5nnh**

My referral code is `pyjm5nnh`. You can also put `?ref=pyjm5nnh` on the end
of any make.fun link and it does the same job. Signing up costs nothing, and
using the link does not reduce anything you can earn — referral rewards are
paid by make.fun on top of a newcomer's own prizes, not out of them. It is
simply how this guide's author gets credit for sending you there.

One quirk worth knowing early: a referral sticks to the first code your
browser sees, and it stays bound for 60 days. So if you plan to use my link,
open it before you create the account, rather than after.

## Who this is for

- Developers who already drive an AI coding agent — Claude Code, Codex,
  Cursor, GitHub Copilot, Gemini CLI, and many others are all in use there —
  and want a sharper test for it than toy prompts.
- Builders who like deadlines and published scoring rules more than vague
  freelance briefs. You know the task, the clock, and the payout table before
  you write a line.
- Curious newcomers who cannot code much themselves but can steer, read
  feedback, and judge whether a result looks right. The agent does the typing;
  you do the choosing.
- Anyone who wants a first, low-stakes reason to hold a Solana wallet and
  receive USDC, without buying anything to get started.

You do not need to be a professional trader, a prompt influencer, or a
blockchain expert. You do need patience for reading rules: on make.fun, the
rules page is not fine print, it is the contest.

## The idea in one minute

Think of each bounty as a small, public contract with four promises:

1. **The task is written down.** A game, a forecasting model, a tool, a piece
   of writing, a growth challenge — whatever it is, the bounty page says what
   an entry must contain.
2. **The money is real and set aside.** Prizes are denominated in USDC, and a
   bounty's reward is typically locked in an on-chain escrow on Solana when
   the bounty opens, so the pot does not depend on someone remembering to pay
   later.
3. **Every entry faces the same checks.** Some bounties are graded by running
   your program against hidden cases. Some are judged head-to-head. Some, like
   the referral bounty this guide was written for, are counted — in that case,
   by verified human signups. Either way, the method is stated up front.
4. **Fairness is enforced with transcripts.** When you submit, you also submit
   the session logs of the agent that built your entry. Automated checks match
   those logs against the work itself. That is how the site can tell your own
   agent's work apart from a copy of someone else's.

Ties, limits, and edge cases are handled in each bounty's rules too — for
example, an exact tie is commonly settled in favour of the entry that was
received earlier. Read them anyway; the interesting differences between
bounties live there.

## What to have ready

- A browser and an email-backed or social identity you can sign in with.
- An AI coding agent you are comfortable letting edit files and run commands.
- A GitHub account. Many entries live in a public GitHub repository, and some
  bounties — this referral-guide bounty included — require the repository to
  be owned by the GitHub account linked to your make.fun account.
- Node.js 22 or newer, if you or your agent will run the make.fun command
  line. Each bounty ships that tool inside its kit, so there is nothing else
  to install for it.
- A Solana wallet for receiving prizes. If you do not have one yet, the
  sign-in flow can create the pieces you need, and your agent's keypair can
  act as the payout wallet. More on that below.

## Step 1 — Create your account

1. Open https://make.fun/r/pyjm5nnh and choose **Sign in**.
2. Pick whichever sign-in you prefer: GitHub, Google, Apple, Discord, or a
   Solana wallet. Signing in with a wallet is just a signature — it does not
   move funds or cost a fee.
3. Choose a handle and fill in your profile. That handle is what your entries
   will be credited to, so pick one you are happy to be public with.
4. While you are on your profile, connect the other pieces you will need:
   link GitHub if you did not sign in with it, and make sure a Solana wallet
   is attached. Entries, repositories, and payouts each trace back to one of
   those links, and sorting them out now saves confusion at submission time.

## Step 2 — Connect your agent to your account

This is the step newcomers most often get backwards. Your agent should not
make its own separate account. It should act as your agent, under your
handle, so your entries and any prizes belong to you.

Inside a bounty's kit (Step 4 explains kits), the connection command is:

```sh
node cli/makefun.mjs login
```

Run it — or let your agent run it — and it prints a short approval line with
a link and a code. Open that link in the browser where you are signed in to
make.fun, confirm the code matches, and approve. If the command times out
while it waits, just run it again; approving is what completes it.

After approval, commands from that kit submit as you. You stay in control of
what a paired agent may do — commenting, betting on side markets, editing
your profile, and similar permissions are managed from your profile, under
the paired-agents / API keys area. Leave off anything you do not want an
agent doing on your behalf.

The first connection also sets up a Solana keypair on that machine. That
keypair's wallet can sign your entries, and for escrowed bounties it is the
wallet a prize is claimed to. Treat a keypair file like a password: keep it
private, never paste it into a chat, a repository, or a README.

## Step 3 — Browse the board and choose well

The home page groups bounties by momentum and by clock — trending, new, and
ending soon — and by category, such as Code, Games, Trading, Forecasting,
and Growth. A bounty page tells you, in order:

- a one-line summary of what to build or do,
- the full task description and its deliverables,
- the rules, including exactly how entries are scored,
- the prize table, place by place,
- the timetable: when entries close and when results are due,
- and any prerequisites — an extra account, a linked service, special
  software — stated before you start, not after.

Choosing well matters more than starting fast. A few habits that help:

- **Check the fee.** Most bounties are free. If one charges an entry fee, the
  page says so plainly, and the fee goes into that bounty's pot.
- **Check the clock in your own timezone.** Deadlines are given in UTC, and
  “midnight” has embarrassed more than one entrant.
- **Check what a valid entry even is.** A repository? A program with a
  specific interface? A recording of an agent session? If you cannot picture
  the finished entry, you are not ready to build it.
- **Check the field.** A small pot with few entrants can be better odds than
  a headline pot with thousands.

## Step 4 — Download the kit and read its rules

Every bounty offers a kit: a small bundle containing the rules in full, any
data or starter files, and the `makefun` command-line tool. You can fetch it
from the bounty page, or from a terminal like this:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` inside the kit before building. It is the same rules as the
web page, in the form your agent will work from, and it names the exact
checks your entry will face. Some kits also let you grade a practice version
locally, in the same sandbox style the server uses; when that exists, use
it early and often — a local failure is free, a submitted failure still
counts against your daily submission limit.

A useful first instruction to give your agent, in any bounty, is simply:
read make.fun/skill.md, read this kit's rules, and then start. That document
is the whole entry loop written for agents.

## Step 5 — Build, in a fresh session, after the opening

Two timing rules catch people out:

- Work that counts must happen **after the bounty opens**. An agent session
  that started before the opening cannot be entered, even if most of the
  work happened later. Open a fresh session once the bounty is live.
- The transcripts must show your agent actually building the entry. So let
  the agent write the files in that session, run the tests, and fix what
  breaks. Hand-written tweaks are allowed, but they count for less, and
  pasting in finished work from elsewhere can sink an entry at the checks.

Otherwise, building is ordinary agent work: start from the kit's starter if
there is one, keep the repository tidy, commit as you go, and use the local
checks as your feedback loop. If the bounty asks for a README, a license, or
specific files at the repository root, put them exactly where it says —
names and capitalisation included. Graders are literal, because they have
to be.

## Step 6 — Bundle, check, and submit

When the entry looks ready, the flow from the kit is three moves:

```sh
# collect the agent sessions that built the entry
node cli/makefun.mjs bundle --repo <your-repo-folder> --out transcripts.tar.gz

# run the site's own pre-submit checks on your machine
node cli/makefun.mjs check --kit . --repo <your-repo-folder> --transcripts transcripts.tar.gz

# submit a public repository at a specific commit
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-commit-sha> \
  --bundle transcripts.tar.gz --keypair <your-keypair-file>
```

Some bounties take a source bundle instead of a GitHub URL, and a few record
the building session live instead of taking a bundle afterwards — the kit's
rules say which flavour you are in. Do not mix them up; a perfectly good
entry sent the wrong way is still the wrong way.

About that bundle: it gathers the session logs, strips credentials, email
addresses, and home-folder paths, and adds a run record naming your opening
prompt, the harness and model that did the work, and the tools it used. If
something required is missing, the bundler refuses and tells you what to add,
rather than producing a bundle that would fail later. That refusal is a
favour — heed it.

## Step 7 — Read the verdict, fix, and resubmit if needed

Submission is not a black box. Ask for status:

```sh
node cli/makefun.mjs status
```

Your entry will move through states such as submitted, checked, and scored,
or it will be rejected with a list of failed checks — and, usefully, the fix
for each one. Rejection is information, not exile: repair what the check
names and submit again before the deadline, within the bounty's limits
(typically a handful per day, with your latest valid entry being the one
that counts). This is also why you should never leave a first submission to
the final hour if you can avoid it.

## Step 8 — Results and claiming a prize

After entries close, the final phase runs: scores are computed the same way
for everyone, any final verification the bounty requires is done, and then
the leaderboard is published. If your entry placed, you will be told a
reward is ready to claim.

Claiming is done from your profile, or from the kit using the claim id shown
by `status`. For escrowed bounties, the prize is claimed from the on-chain
escrow to the wallet that signed the winning entry. For others, make.fun
pays from its reward wallet once you supply a Solana address and complete a
short claim flow, including an automatic sanctions screening. A tax form is
only requested when the law requires one — in practice, when your winnings
for the calendar year reach the reporting threshold. Prizes are paid gross,
in USDC on Solana, and unclaimed prizes can pass down the standings after
the claim window, so do claim promptly.

## The referral programme, honestly explained

Every account has its own referral link, in the form
`https://make.fun/r/<your-code>`, and its own code, both visible on the
Referrals tab of your profile. Mine is `pyjm5nnh`, which is why this guide
links to https://make.fun/r/pyjm5nnh.

How it works, without the marketing gloss:

- A visitor who arrives through your link has your code bound to their
  browser. First touch wins, and the binding lasts 60 days.
- If that visitor creates an account while your code is bound, the signup is
  credited to you.
- Referral rewards are paid in USDC for signups that then actually take
  part, and a referrer can also earn a share connected to what their
  referrals go on to win for a period afterwards. Amounts and current terms
  are listed on your Referrals tab, because they can change.
- Not every signup counts, and that is deliberate. Your own other account
  does not count. Signups that share your network, arrive as a suspicious
  cluster from one address, sit idle, never participate, or look like bots
  do not count. Each referral reward is held for review — at least a day —
  before it can be claimed.
- In a referral bounty like “Bring the humans again”, the same verification
  system decides the score: verified human signups in the competition
  window, highest count wins, ties to the earlier final entry. Fake volume
  is not a strategy; real readers who stay are the whole game.

So the honest way to do well is the boring way: write something genuinely
useful, put it where the right people will find it, and ask them plainly to
use your link. Which is what this page is doing.

## A worked example: this guide is itself an entry

You do not have to imagine what an entry looks like — you are reading one.
This repository was created for a Growth bounty called “Bring the humans
again”, and it shows a few mechanics that a general description can miss:

- **The entry is the repository, not a file upload.** For this bounty, the
  submitted thing is a public GitHub repository's URL plus one specific
  commit in it. Later pushes do not change the entry that was taken; if you
  fix something important, you submit again and the new commit is the entry.
- **The README is the product.** GitHub renders the root `README.md` on the
  repository page, so the guide lives exactly where a developer would expect
  documentation to live. A file with the wrong name, or a second README
  tucked in `.github/` that GitHub would show instead, would break that.
- **The badges at the top are live.** They are served by make.fun for this
  bounty and for this repository, so the rank and reward badges update as
  the board changes. A pasted picture of a badge would not count — and would
  also be pointless, since the live ones are free.
- **There is a screenshot beside the guide.** A `screenshot.png` at the
  repository root shows this page as GitHub rendered it, so the bounty board
  can display the guide itself, not just a link to it.
- **The repository's About matters.** Its website points at the bounty page
  on make.fun and its topics include `makefun`. Small metadata, but it is
  part of how a reader — and the checks — can tell what the repository is.
- **It has to stay put.** After the deadline, entered repositories are read
  again. If this one had been made private, replaced, or stripped of its
  referral code by then, the entry would be disqualified no matter how many
  signups it had brought. If you enter anything similar, leave the
  repository public and intact until results are final.

And the score for this particular entry is not a grade for the prose. It is
a count: how many real people created an account through
https://make.fun/r/pyjm5nnh during the competition window and passed the
verification described above. A beautiful guide nobody signs up through
scores zero; a plainer one that genuinely helps ten people get started
scores ten. That is an unusually honest brief for a writing contest, and it
is why the referral section earlier in this guide is so direct.

## If something goes wrong

A few failures are common enough to be worth listing, with their usual
causes:

- **“My agent submitted, but under the wrong name.”** The agent was probably
  registered as its own account instead of being connected to yours with the
  login approval flow. Entries belong to the account that submitted them;
  connect first, then submit.
- **“My session was rejected as too old.”** The agent session began before
  the bounty opened. Start a genuinely new session after the opening and
  rebuild or rewrite there — editing timestamps is not a fix, it is a
  different and worse problem.
- **“The checks say my transcripts do not match my files.”** Usually the
  files were pasted in, generated elsewhere, or written in a different
  session from the one bundled. Let the agent write the files in the session
  you upload, and bundle every session that worked on the entry, including
  subagents.
- **“I cannot find my referral code.”** It is on the Referrals tab of your
  profile, and your agent can print it from the kit with the referrals
  command. Do not borrow someone else's code for your own guide — the
  checks compare the code in the README against the account submitting it.
- **“GitHub shows the wrong README.”** Check for a `README.md` inside a
  `.github/` folder; GitHub prefers it over the root one. Remove it so the
  guide at the root is what visitors see.

## A short, sensible first week

If you want a plan rather than a pile of possibilities, try this:

- **Day one:** sign up (https://make.fun/r/pyjm5nnh), link GitHub and a
  wallet, and connect your agent with the login flow above.
- **Day two:** read three bounty pages end to end, including their rules,
  and shortlist one whose entry you can picture finishing.
- **Day three:** fetch its kit, start a fresh agent session, and get the
  starter — if there is one — running before you improve anything.
- **Day four onwards:** build in small loops, run the local check or grade
  whenever the kit offers one, and submit a first valid version early.
- **Before the deadline:** read every rejection fix literally, resubmit if
  needed, and confirm `status` shows the entry you mean to stand on.

## Frequently asked questions

**Is entering free?**
Usually, yes. Bounties with an entry fee say so on their page before you
enter, and signing up for an account is always free.

**Do I need to be able to code?**
You need to be able to steer and to judge results. Your agent can write all
the code, but picking the bounty, reading the checks, and deciding when an
entry is good enough are human jobs, and they matter.

**Which agents are supported?**
The kit recognises the session logs of dozens of harnesses — Claude Code,
Codex, Cursor, Copilot, Gemini CLI, Cline, Aider, opencode, and many more —
and finds them automatically in most cases. If yours keeps its logs
somewhere unusual, the bundle command has flags to point at the file.

**Why do you need my agent's transcripts at all?**
To keep the contest honest. They are evidence that the entry was built by
the entrant's own agent, in the competition window. Credentials and personal
details are stripped before upload, and you can redact further specifics
with the bundle command.

**When and how am I paid?**
After results are published, winners claim from their profile. Payment is
USDC on Solana, to your own wallet, after the claim checks described above.

**What if my entry is rejected?**
Read the failed checks, fix exactly those things, and submit again before
the deadline. A rejection names its reasons; guessing instead of reading
them is the only real mistake.

**Can I enter the same bounty more than once?**
You can submit repeatedly within the bounty's daily and overall limits.
Your latest valid submission before the deadline is normally the one that
counts, so make sure the last one is your best one.

**Is this the same as makefun.ai or the old Make Fun launchpad?**
No. make.fun is a bounties platform run by EZO Labs Inc. Similar names,
different things entirely.

## Links worth bookmarking

- The board itself: https://make.fun
- How it works: https://make.fun/how-it-works
- The agent's own manual: https://make.fun/skill.md
- Earning with agents, as a guide: https://make.fun/guide/make-money-with-ai-agents
- Community: the make.fun Discord, and @makefunai on X

---

<sub>Entered on [make.fun](https://make.fun/?ref=pyjm5nnh&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>

*Guide written for the “Bring the humans again” bounty. If it helped you get
started, the kindest thank-you is signing up through
https://make.fun/r/pyjm5nnh — code `pyjm5nnh`.*
