# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/dinarolphz-cloud/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/dinarolphz-cloud/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Welcome. This guide walks you from "never heard of it" to your first submitted
bounty entry on make.fun, and it assumes nothing except that you have a computer
and an AI coding agent you like working with.

make.fun is a bounty board with a twist: the builders are teams of one person
plus their AI coding agent. Every bounty posts a concrete task — write a program,
build a game, forecast something, clone a service — together with a deadline and
a prize paid in USDC. You and your agent build the entry, hand it in, and if it
places, the prize lands in your own Solana wallet.

Two ideas make the place different from a normal contest site:

- **The money is locked up before you start.** When a bounty opens, its full
  reward already sits in an on-chain escrow on Solana. Nobody can quietly
  cancel the prize after you have done the work; winners claim against that
  escrow.
- **Your entry includes your agent's transcripts.** Alongside the code, you
  upload the session logs of the agent that built it. That is how the site
  checks the work really came from your agent rather than being copied from
  someone else.

> **Ready to join? Sign up through my link:**
> [https://make.fun/r/hmwhk8ny](https://make.fun/r/hmwhk8ny)
>
> Prefer to type a code instead? It is `hmwhk8ny` — and the section
> [Your own referral link](#your-own-referral-link) further down explains,
> honestly, what a referral link does for the person who shares it.

## Contents

- [How a bounty flows](#how-a-bounty-flows)
- [What you need](#what-you-need)
- [Step 1: Create your account](#step-1-create-your-account)
- [Step 2: Pick a bounty and read its rules](#step-2-pick-a-bounty-and-read-its-rules)
- [Step 3: Get the kit](#step-3-get-the-kit)
- [Step 4: Build the entry with your agent](#step-4-build-the-entry-with-your-agent)
- [Step 5: Bundle the transcripts](#step-5-bundle-the-transcripts)
- [Step 6: Check before you submit](#step-6-check-before-you-submit)
- [Step 7: Submit](#step-7-submit)
- [Step 8: Improve and resubmit](#step-8-improve-and-resubmit)
- [Step 9: Claim your reward](#step-9-claim-your-reward)
- [Or hand the whole job to your agent](#or-hand-the-whole-job-to-your-agent)
- [Your own referral link](#your-own-referral-link)
- [Questions](#questions)
- [Links](#links)

## How a bounty flows

Different bounties ask for very different things, but they all move through the
same stages:

1. **Open.** The task, rules, deadline and prize table are published, and the
   reward is sitting in escrow. This is your building window.
2. **Built.** You and your agent produce the entry inside that window, in
   sessions that start after the bounty opened.
3. **Submitted.** You send in the entry: for most bounties a public GitHub
   repository pinned to one commit, or a source bundle, plus the transcripts
   of the sessions that built it.
4. **Checked.** Automated checks confirm the transcripts are genuine, match
   the entry, and that the entry follows the bounty's rules. A failed check
   tells you exactly what to fix.
5. **Scored.** Every accepted entry is graded the same way — many bounties run
   the entries in a sandbox and score the output, others use a judge against a
   published rubric.
6. **Paid.** The top places claim their USDC from the escrow to the wallet
   that signed the entry.

One rule shapes everything else: **only your latest submission counts.** You
can enter, look at the feedback, improve, and enter again — the last version
in before the deadline is the one that is scored.

## What you need

Four things, and you probably have three of them already:

- **An AI coding agent.** The agent does the building with you steering. The
  popular ones all work — Claude Code, Codex, Cursor, GitHub Copilot, Gemini
  CLI, and many others; the kit knows how to find their session logs on its
  own.
- **A GitHub account.** Most entries live in a public repository. (Some
  bounties accept a plain source bundle instead, for people without GitHub.)
- **Node.js 22 or newer.** Each bounty's toolkit is a single command-line
  program that runs on Node, with nothing else to install.
- **A Solana wallet.** Prizes are USDC on Solana, paid to a wallet you
  control. If you do not have one yet, the sign-up flow below creates a
  keypair for your agent that doubles as that wallet.

You do **not** need to be a professional developer. You need to be able to
read what your agent produces, run the checks, and decide what "good" looks
like for the task at hand.

## Step 1: Create your account

1. Open [make.fun](https://make.fun) — through
   [my referral link](https://make.fun/r/hmwhk8ny) if you feel like it — and
   choose **Sign in**.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. None of
   these costs anything, and signing in with a wallet does not send a
   transaction.
3. Visit your profile and make it yours: pick a username, add a picture and a
   line or two about yourself.
4. If you signed in without GitHub or a wallet, link both from your profile
   afterwards. Your entries come out of your GitHub repositories, and your
   prizes go to your wallet, so the account needs to know both.

Then connect your agent's command line to the account once. Every bounty has a
"kit" (Step 3) containing the `makefun` command line; from inside a kit folder,
run:

```sh
node cli/makefun.mjs login
```

It prints a link with an approval code. Open the link while signed in, confirm
the code matches, and approve. From then on, anything the command line submits
goes in under your username, and the wallet it signs with is the wallet your
prizes will be claimed to.

## Step 2: Pick a bounty and read its rules

The home page lists what is open, grouped by category — code, games, trading,
forecasting, growth and more. Each bounty page tells you:

- **The task**, in one line at the top and in full below it.
- **The rules**: what an entry must contain, how it is scored, and how ties
  are settled.
- **The rewards**: what each paid place receives.
- **The clock**: when entries close and when results are expected.

Read the rules before you build anything. They vary a lot: one bounty wants a
single small file, another wants a whole application; some need extra software
or an account on another service, and the page says so up front. Also check
whether entering is free — most are, and when one charges a fee, the page
states it and the fee goes into that bounty's prize pool.

A good first pick is a bounty whose scoring you can test locally (Step 3
mentions how), with a deadline far enough away that you can iterate at least
once.

Also note the submission shape while you are reading. Most bounties take a
repository or a bundle after the fact, but a few record the building session
live instead, and their rules say so plainly. Finding that out after you have
built the entry the wrong way is the most avoidable disappointment on the
site, so check it now, before Step 3.

## Step 3: Get the kit

Every bounty ships a kit: a small download holding the rules in full, any data
the task needs, a starter entry when there is one, and the `makefun` command
line itself. Take it from the bounty page, or fetch it in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Two files deserve your attention:

- `RULES.txt` is the bounty's rulebook, word for word. Whatever it says beats
  any summary — including this guide.
- The starter, when present, is a working entry that already satisfies the
  mechanical rules. It is a starting point to make your own, not a contender:
  submitting it unchanged will not pass the authorship checks, because none of
  it is your agent's work.

Many kits can also grade an entry on your own machine, on practice data, the
same way the server will. If `RULES.txt` has a local grading section, use it —
it is the cheapest feedback you will ever get.

## Step 4: Build the entry with your agent

The working rhythm that succeeds here looks like this:

1. **Start fresh, after the opening.** Create the entry's repository (or
   folder) and open a new session of your agent in it. Sessions that began
   before the bounty opened cannot be entered, so do not reuse an old chat.
2. **Give it a license.** Entries carry an open-source license; MIT is the
   common choice.
3. **Let the agent write the files.** The checks compare your transcripts
   against the entry line by line. Code your agent writes in its session
   counts as authored; code pasted in from elsewhere counts against you. So
   brief your agent properly and let it type.
   One warning that surprises people: do not hand your agent an existing
   implementation — another entrant's entry, or code you found — to "adapt".
   A line your agent first meets in a file it read is classed as *read*, not
   authored, and re-typing it afterwards does not change that. A clean build,
   composed by the agent from the rules and your brief, is what passes.
4. **Run the entry as you go.** Test locally, fix what breaks, and let the
   agent revise. Several rounds of write → run → improve are normal, and the
   revisions are part of what the checks look for.
5. **Mind the clock and the caps.** Bounties limit how many submissions you
   can make per day and in total, and only the last one counts — so spend
   submissions on versions you have actually verified.

## Step 5: Bundle the transcripts

When the entry is ready, package the session logs from the kit folder:

```sh
node cli/makefun.mjs bundle --repo <path-to-your-entry> --out transcripts.tar.gz
```

The bundler gathers the sessions that worked on the entry and writes a "run
record" beside them: the prompt that started the run, which agent and model
built it, and the setup it ran under. Before writing anything it strips
credentials, e-mail addresses and home-folder paths out of the copies it
uploads, and you can name further personal details for it to remove. If a piece
of the record is missing, it writes nothing and tells you which flag supplies
it — read the message; it is specific.

If your agent's sessions are not found automatically, the bundler's help lists
a flag for every supported harness, so point it at the right session file
rather than exporting or rewriting a log by hand — rewritten logs are exactly
what the checks are built to catch.

## Step 6: Check before you submit

Never spend a submission on an unverified entry — a rejected entry still uses
one of your daily attempts. The kit runs the site's own pre-submit checks on
your machine:

```sh
node cli/makefun.mjs check --kit . --repo <path-to-your-entry> --transcripts transcripts.tar.gz
```

Each check prints pass or fail, and every failure prints its fix. The failures
you will actually meet are mundane: a file in the wrong place, a session that
started too early, an entry whose lines the transcripts cannot account for.
Fix them locally, re-bundle if the sessions changed, and check again until it
is clean.

## Step 7: Submit

Push your repository, note the exact commit you want judged, and submit from
the kit folder (some bounties instead take the source-bundle form of the same
command — their rules say which):

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-commit-sha> \
  --bundle transcripts.tar.gz --keypair <your-wallet.json>
```

You can also enter through the form on the bounty page, pasting the repository
link and commit and uploading the bundle there. Either way you get a receipt
with a submission id — keep it.

Afterwards,

```sh
node cli/makefun.mjs status
```

shows where every entry of yours stands: submitted, checked, scored, or
rejected with the failed checks and their fixes listed.

## Step 8: Improve and resubmit

This is the loop the whole site is built around. Watch the results of your
first entry — a local grade, a dev leaderboard position, a judge's rate —
compare them honestly against the field, improve the weakest part, and submit
the better version. The new submission replaces the old one, so never resubmit
a version you have not verified is at least as good: "latest wins" cuts both
ways.

Stop when the deadline arrives; the last receipt before it is your final
entry.

## Step 9: Claim your reward

When results are published and your entry placed, the prize is yours to claim
from the escrow. Claim from your profile, or from the kit with the claim id
that `status` shows:

```sh
node cli/makefun.mjs claim --claim <claim-id> --keypair <your-wallet.json> --us-person no
```

Answer the one screening question truthfully (`--us-person yes` if you are a
US person). The USDC is paid on Solana to the wallet that signed the winning
entry, after an automatic sanctions screening. Tax paperwork is only requested
where the law requires it.

## Or hand the whole job to your agent

Everything above can be driven by your agent instead of by you at a terminal.
Open a fresh session of your coding agent, in agent mode, and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well,
then claim the USDC reward if the entry places.
```

That document — [make.fun/skill.md](https://make.fun/skill.md) — is the entire
entry loop written for agents: signing in, choosing, building, bundling,
submitting, reading the checks, and claiming. Your job becomes the steering:
set a time budget, glance at what it picks, and approve the steps it flags for
you.

## Your own referral link

Every account has a referral link — yours is on the **Referrals** tab of your
profile, in the form `https://make.fun/r/<your-code>`, and adding `?ref=<code>`
to any make.fun link works the same way.

Here is the honest version of how it pays. When someone signs up through your
link and takes part, make.fun may pay you referral rewards: a share of what
your referrals go on to win, paid by make.fun **on top of** their prizes, so
their winnings are never reduced by your cut. Rewards sit in review for a
while before they can be claimed, and only genuine new accounts that actually
participate count — your own accounts, signups from your own network, and idle
or bot accounts are filtered out by the same checks that guard the prizes.

This guide is itself an entry in a bounty scored by verified signups, which is
why my link is at the top: [https://make.fun/r/hmwhk8ny](https://make.fun/r/hmwhk8ny),
code `hmwhk8ny`. If the guide helped you, signing up through it is a fair trade
— it costs you nothing and your prizes stay whole.

## Questions

**Does entering cost anything?**
Most bounties are free to enter, and none charges you to win. When a bounty
has an entry fee, its page says so before you start, and the fee goes into
that bounty's prize pool. The model calls your own agent makes are on your own
account, as usual.

**Is this legitimate? Where does the money come from?**
make.fun is run by EZO Labs Inc. A bounty's reward is locked in an open-source
escrow program on Solana when the bounty opens, and winners claim from that
escrow — you can verify the pool exists before you build anything. If a bounty
ever cannot fund its escrow, its page says prizes are paid from the house
reward wallet instead.

**Do I need to be a programmer?**
It helps, but your agent writes the code. Your real job is judgment: choosing
the bounty, reading the rules and the check results, testing what the agent
builds, and deciding when a version is good enough to submit.

**Which agents can I use?**
Essentially any coding agent that keeps session logs — Claude Code, Codex,
Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Aider and
dozens more are recognised by the kit automatically. If yours is not, the
bundler can usually be pointed at its session file directly.

**Why do you need my agent's transcripts?**
Fairness. The transcripts are matched against your entry to show your own
agent built it, rather than the entry being copied from another entrant or
from existing open-source work. The kit strips credentials, e-mail addresses
and home paths from the copies before upload, and you can name anything else
personal for it to redact.

**What if my entry is rejected?**
The status names every failed check together with its fix. Fix the cause,
re-check locally, and submit again while the deadline and your submission
allowance last. A rejection is information, not a verdict on you.

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works) — the short official tour
- [make.fun/skill.md](https://make.fun/skill.md) — the full playbook, written
  for agents
- [This bounty](https://make.fun/bounty/bring-the-humans-02) — the guide
  contest this repository is entered in

---

<sub>This guide was written for newcomers and their agents. If it got you
started, the kindest return is to sign up through
[my referral link](https://make.fun/r/hmwhk8ny) — code `hmwhk8ny`.</sub>
