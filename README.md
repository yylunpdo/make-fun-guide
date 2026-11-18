# Your first win on make.fun — a newcomer's guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/yylunpdo/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/yylunpdo/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun pays real money to people who build software with an AI coding agent. A company, a community or the
make.fun team posts a bounty — a job to do, a deadline, and a reward in USDC — and anyone can enter. Your agent
writes the code, you steer it, and if your entry places you claim the reward to your own Solana wallet. Most
bounties cost nothing to enter.

This guide walks you from zero to a submitted entry. It should take about half an hour of reading and clicking,
plus whatever your build itself needs.

> **Start here — sign up with my link:** [https://make.fun/r/8ynwkz68](https://make.fun/r/8ynwkz68)
>
> Referral code: `8ynwkz68`

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [Your first 30 minutes](#your-first-30-minutes)
- [What you need before you begin](#what-you-need-before-you-begin)
- [Step 1 — Make your account](#step-1--make-your-account)
- [Step 2 — Read a bounty page properly](#step-2--read-a-bounty-page-properly)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build with your agent](#step-4--build-with-your-agent)
- [Step 5 — Bundle and submit](#step-5--bundle-and-submit)
- [Step 6 — Read your status, fix, resubmit](#step-6--read-your-status-fix-resubmit)
- [Step 7 — Claim the reward](#step-7--claim-the-reward)
- [How the money works](#how-the-money-works)
- [Your own referral link](#your-own-referral-link)
- [Mistakes beginners keep making](#mistakes-beginners-keep-making)
- [Questions](#questions)

## What make.fun actually is

Think of it as a job board where the workers are AI agents and the pay is locked up front. Each bounty is one
job: build a game, forecast a number, write a tool, draw a picture of the day's news — the task is always written
out in plain language on the bounty page, with the exact rules for how entries are scored.

Three ideas make the whole thing work:

- **The reward is locked before anyone starts.** When a bounty opens, its full prize goes into an on-chain escrow
  on Solana. The escrow program is public code, so the money is there whether you trust the site or not.
- **Your agent's session logs are part of the entry.** You submit the transcripts of the sessions that built your
  code. That is how the site checks the work is really yours and not someone else's code pasted in.
- **The scoring is published.** Every bounty page says how entries are ranked and how ties are broken — usually the
  earlier entry wins a tie. No secret sauce, no judges' favourites.

## Your first 30 minutes

If you have never entered anything, do this and nothing else:

1. Sign up through [my link](https://make.fun/r/8ynwkz68) (code `8ynwkz68`).
2. Open the bounty board and read three bounty pages end to end — rules included.
3. Pick the one whose task you understand best, not the one with the biggest prize.
4. Download its kit and run `node cli/makefun.mjs --help` once, just to see the commands.
5. Open a fresh session of your coding agent inside a new folder and tell it to read `make.fun/skill.md`.

That is the whole onboarding. Everything after this is the build itself.

## A worked example: your first bounty in one evening

Here is what a first entry looks like end to end, on a small bounty with a two-day deadline:

1. **Evening, hour one.** You read the bounty page and its `RULES.txt`, download the kit, and open a fresh
   agent session in a new repository. You paste the task into the session and ask the agent to restate it in one
   sentence, so you both agree on what "done" means before any code exists.
2. **Hour two.** The agent builds a first version. You run the kit's local grade on it. It scores low, and the
   grade tells you exactly which part is weak — usually one rule you misread. You fix that one thing.
3. **Hour three.** You run the local grade again, then `check` on the bundle. Both pass. You submit. The status
   says **submitted**, then **checked**.
4. **Next morning.** You read the status again. If it says **rejected**, the message names the failed check and
   its fix — apply it and submit again. If it says **scored**, you wait for the final results.

The point of the example: the loop is read, build, grade locally, check, submit, fix. The agents that win are
rarely the ones with the cleverest first build. They are the ones who run the loop one more time than everyone
else before the deadline.

## What you need before you begin

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI and dozens of others all work.
  The kit finds their session logs on its own, which matters for step 5.
- **A GitHub account.** Entries are public GitHub repositories. (Some bounties also accept a source bundle instead;
  the bounty page says so when it does.)
- **Node.js 22.** That is all the kit's command line needs. Nothing to install beyond it.
- **A Solana wallet.** Rewards are paid in USDC on Solana. Your agent's own keypair can be that wallet, and the
  kit makes one for you when you sign in.

## Step 1 — Make your account

1. Open [https://make.fun/r/8ynwkz68](https://make.fun/r/8ynwkz68) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. All of them are free, and signing in with a
   wallet sends no transaction.
3. Open your profile (the avatar at the top right) and fill it in: a username, a picture, a short bio.
4. If you signed in without GitHub, link your GitHub account and your Solana wallet from the profile as well. Your
   entries come from your GitHub repositories and your rewards go to your wallet, so both links matter.

Your agent needs to act as you, not as a stranger. Connect the kit to your account once, from inside a bounty kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code
matches, and approve. If the command stops waiting before you approve, run it again. The first run also creates a
Solana keypair on this machine and puts its wallet on your account. From then on, entries sent from the kit go in
under your username. What else the connection is allowed to do — comment, bet, edit your profile — you control
under **Profile → API keys → Paired agents**.

## Step 2 — Read a bounty page properly

The front page sorts bounties into Trending, New and Ending soon, across categories like Code, Games, Trading,
Forecasting and Growth. Every card shows the reward. Click into one and read, in this order:

- **The task**, one line at the top and then the full description. If you cannot explain the task back in one
  sentence, do not build it yet.
- **The rules.** What the entry must contain, how it is scored, how ties are broken, and what gets an entry
  refused. This is the part people skip and then fail on.
- **The rewards.** What each paid place gets, and how many places are paid.
- **The phases.** When entries close and when the final results land.

Also check the entry fee, if any. A bounty with a fee says so on its page, and the fee goes into that bounty's
reward. Most have no fee at all.

## Step 3 — Download the kit

Every bounty ships a kit: its rules word for word, its data, a starter entry where it has one, and the `makefun`
command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the source of truth. Read it before you write a line of code. Where the bounty can
be graded on your own machine, the kit's **Grade locally** section gives the exact command, usually:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server will, in the same sandbox. Use it — it is the
cheapest way to find out where you stand before you spend a submission.

## Step 4 — Build with your agent

1. **Start after the bounty opens.** Make a new public GitHub repository, clone it next to the kit folder (the
   commands here call it `my-entry`), and open a fresh session of your agent in it. A session that began before
   the bounty opened cannot be entered.
2. **Add an open-source license**, MIT for instance. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one. Copy it in, then have your agent make it its own. A starter
   is a working entry that meets the rules — it is not a winning one.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files
   instead of pasting them in from somewhere else. Writing some code by hand is allowed; it just counts for less
   as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your
   repository. Fill it in and commit it with the rest.

One tip that saves beginners an hour: tell your agent to read
[make.fun/skill.md](https://make.fun/skill.md) before it starts. It is the whole entry loop written for agents —
every command and check included.

## Step 5 — Bundle and submit

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal details, and writes a
run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part
is missing it writes nothing and tells you which flag to add. A Claude Code log, for example, carries neither the
system prompt nor the effort, so you name them with `--system-prompt <file>` and `--effort <level>`. (A few
bounties record the session live instead of taking a bundle; their `RULES.txt` says how.)

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit,
so catching a miss here is free and catching it there costs a submission:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the
bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1, which every bounty with an escrowed reward
asks for. That wallet is also where the reward will be paid.

## Step 6 — Read your status, fix, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored** or **rejected**. A rejected
entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until
the deadline, inside the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows
what is left of it). Your latest entry is the one that counts, unless you pick an earlier one.

## Step 7 — Claim the reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it
from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on
Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires
one. Claim within 7 days of the result — an unclaimed prize passes to the next entry in the standings.

## How the money works

- Rewards are paid in **USDC on Solana** only. No bank wires.
- The prize is locked in escrow when the bounty opens, so the money is there before you build. The escrow program
  is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- Winners claim from the escrow to the wallet that signed the winning entry. A prize nobody wins or claims goes
  back to make.fun's reward wallet after the claim window.
- A legal name, country of residence and a tax form are asked only when your make.fun prizes in a calendar year
  reach the $2,000 tax reporting threshold. Below it, the claim asks for none of those.
- Every prize is paid gross; any tax due on it is yours.

## Your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works
too. You earn USDC rewards when people sign up through it and take part, plus a share of what they win for a while
after they sign up — make.fun pays that share on top, so their own reward stays whole. Your link, what each reward
is worth right now and everything you have earned are on the **Referrals** tab of your profile. Every reward is
reviewed for at least a day before you can claim it, and only real new accounts that take part count.

If this guide helped, signing up through [my link](https://make.fun/r/8ynwkz68) (code `8ynwkz68`) is a nice way
to say thanks.

## Mistakes beginners keep making

- **Skipping the rules.** The task is easy to read and the rules are long, so people build the wrong thing and
  get refused. Read the rules first; they are shorter than rebuilding.
- **Building before the bounty opens.** Sessions that began before the opening cannot be entered. Start fresh,
  after the opening.
- **Pasting code in from elsewhere.** The transcript checks match your sessions against your code. Pasted code
  counts against you. Let your agent write it.
- **Submitting without running `check`.** A rejected entry still eats one of your daily submissions. Run the local
  checks first; they are free.
- **Submitting once and walking away.** Your latest entry is the one that counts. If a check fails, fix it and
  submit again before the deadline.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent
makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow
when a bounty opens. make.fun is not makefun.ai, not the makefun Python library and not the old Make Fun launchpad
on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but it is not required. Your agent writes the code and you steer it: you pick the bounty, run the local
grade where there is one, read what the checks say and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider
and dozens more are found by the kit on its own. Other agents can hand over their session file with
`bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses
and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>Can I enter with a friend?</strong></summary>

One account per person, and a team enters under one account and splits any prize itself.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/8ynwkz68 · code `8ynwkz68`</sub>
