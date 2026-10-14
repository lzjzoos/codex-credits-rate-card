# Codex Credits Explained: How They Work, What a Task Actually Costs, and How to Buy More Without Upgrading Your Plan (Rate Card, 12-Month Rules, and a $1-Off Top-Up Code)

You're three hours into a refactor, Codex is in a groove, and then the usage panel tells you the weekly allowance is gone. You can wait for the reset, finish the boring parts by hand, or use the thing OpenAI built for exactly this moment: Codex credits, a pay-as-you-go balance that takes over the instant your plan's included usage runs out.

Credits are also easy to misunderstand. They're not API credits. They don't reset your limits. They're billed per token, not per prompt. And they share one balance with more features than most people realize. Here's how the whole system works, what tasks realistically cost, which plans can buy credits at all, and when buying credits beats upgrading.

## What Codex credits actually are

Codex credits are a flexible top-up balance attached to your ChatGPT account. Your plan's included usage — the rolling 5-hour quota and the weekly quota — always gets consumed first. Credits sit untouched until that allowance is exhausted, and then eligible tasks automatically start drawing from the balance. No mode switch, no killed session, no plan change.

Three behaviors define how they behave in practice:

1. **The handover is automatic.** Once you cross a limit, subsequent prompts keep running on credits. A task in progress isn't cut off mid-flight either: if the balance hits zero during an active turn, OpenAI lets that turn finish, subject to fair-use protections. The next turn pauses until credits are added or normal quota recovers.
2. **They top up, they don't reset.** Buying credits doesn't enlarge your 5-hour or weekly allowance and doesn't change your plan. It adds overflow capacity, nothing more.
3. **The balance is shared.** Codex across the CLI, IDE extensions, the desktop app, and cloud tasks draws from the same pool as ChatGPT Work, ChatGPT for Excel, and Workspace Agents, wherever those features exist on your plan. Regular chat isn't metered against it.

One quirk worth knowing early: the balance can go negative. If concurrent tasks or a long multi-step run drain it mid-operation, your account can dip below zero. Any future purchase or auto-reload offsets that negative amount before adding usable capacity.

## The three balances people mix up

OpenAI runs three separate wallets, and confusing them is the most common mistake in every credits discussion:

| Balance | Where it lives | What it pays for |
| --- | --- | --- |
| Usage credits (Codex & ChatGPT Work) | Your ChatGPT account / Codex app | Codex overflow, ChatGPT Work tasks, ChatGPT for Excel |
| ChatGPT wallet funds | ChatGPT web account, in US dollars | Eligible checkout purchases and gift card redemptions |
| Platform API credits | OpenAI's developer platform, prepaid USD | API requests made with your developer API key |

The boundaries are strict. Usage credits can't fund developer API calls, wallet dollars can fund some credit pack checkouts but won't feed auto-reload, and API credits can't pay for ChatGPT subscription features at all. If you've ever topped up the wrong balance and wondered why Codex still complained about limits, this is usually why.

## The token-based rate card, decoded

In April 2026, OpenAI moved Codex pricing away from "credits per message" estimates to a token-based card, aligned with how the API actually bills. Most Plus, Pro, Business, and Enterprise workspaces are on the new card now; a small subset of older Enterprise accounts still sees the legacy per-message averages.

The current card, in credits per million tokens:

| Model | Input tokens | Cached input tokens | Output tokens |
| --- | --- | --- | --- |
| GPT-5.6 Sol | 125 | 12.50 | 750 |
| GPT-5.6 Terra | 50 | 5 | 300 |
| GPT-5.6 Luna | 5 | 0.5 | 30 |
| GPT-5.5 | 125 | 12.50 | 750 |
| GPT-5.5 Cyber | 312.5 | 31.25 | 1,875 |
| GPT-5.4 | 62.50 | 6.250 | 375 |
| GPT-5.4-Mini | 18.75 | 1.875 | 113 |
| GPT-5.3-Codex | 43.75 | 4.375 | 350 |
| GPT-5.2 | 43.75 | 4.375 | 350 |
| GPT-5.3-Codex-Spark | Research preview | Research preview | Research preview |
| GPT-Image-2.0 (image) | 200 | 50 | 750 |
| GPT-Image-2.0 (text) | 125 | 31.25 | 250 |

A few things worth pulling out of that table:

- **Cached input is the bargain.** It bills at roughly a tenth of uncached input, and OpenAI doesn't charge for cache writes. Stable repo context is cheap; fresh context is what costs.
- **Output dominates.** On Sol, output tokens bill at six times the input rate. Reasoning tokens count as output too, so deep-reasoning modes burn credits faster than the token counts alone suggest. Ultra reasoning goes further, running maximum reasoning and sometimes extra agents.
- **Fast mode costs more.** Supported models bill at a higher rate when you turn it on.
- **Code review runs GPT-5.3-Codex**, at the 43.75 / 4.375 / 350 rates above.
- **GPT-5.5 Cyber** is only available through OpenAI's Daybreak / Trusted Access for Cyber program.
- **GPT-5.4 and GPT-5.4 mini retired** from Codex for ChatGPT sign-in users on August 31, 2026. GPT-5.6 Terra and Luna are the designated replacements. API-key usage wasn't affected, which is why older guides still list those models.

For anyone on a legacy Enterprise card, the old averages still apply: roughly 14 credits per local task on Sol, 6 on Terra, 1 on Luna, and about 34 credits per cloud task or code review on the retired GPT-5.4 rows.

## What a Codex task actually costs

OpenAI's own reference point: a typical task on GPT-5.6 Sol lands somewhere between **5 and 40 credits**. That range is wide because three variables — model, context size, and output volume — swing the bill hard.

To make it concrete, take an illustrative task shape: 100,000 uncached input tokens (fresh files and instructions), 500,000 cached input tokens (repo context already billed at the discount), and 20,000 output tokens. That's an example, not an official benchmark, but the arithmetic comes straight from the rate card:

- **GPT-5.6 Sol:** 12.5 + 6.25 + 15 ≈ 34 credits
- **GPT-5.6 Terra:** 5 + 2.5 + 6 ≈ 13.5 credits
- **GPT-5.6 Luna:** 0.5 + 0.25 + 0.6 ≈ 1.4 credits

Same workload, roughly a 25x spread, entirely from model choice. This is also why two developers on the same plan can burn credits at completely different speeds. A targeted single-file edit reading a couple thousand tokens costs a fraction of an autonomous multi-file refactor that loops through terminal commands and test output.

For teams budgeting headcount, OpenAI pegs average Codex spend at around **$100–$200 per developer per month**, with large variance depending on model mix, parallel instances, automations, and fast-mode use.

## Where to check your balance and buy credits

OpenAI exposes the balance in three places: **Settings → Usage** in ChatGPT, the **Usage & Billing** section of the Codex desktop app, and the `/status` command inside the Codex CLI, which shows your 5-hour and weekly percentages plus exact reset times. The Usage panel is also where you'll find the **Add credits** button, your consumption history, and auto-reload settings.

Auto-reload works in three steps: set a minimum trigger balance, set a target balance, and OpenAI charges your default payment method for the difference whenever the floor is breached. Two details matter. Auto-reload buys usage credits directly — it never tops up your general wallet — and it requires a working default payment method on the account.

On pricing, there's no single published number anymore. Credits launched in October 2025 at $40 per 1,000 credits, but OpenAI's current help docs state that amounts, denominations, and prices vary by account, region, and plan — the checkout shows your actual price. Terms are consistent, though:

> Purchased credits expire **12 months** after purchase and are non-refundable except where required by law. They're tied to the account they were bought on and can't be transferred.

That expiry-plus-non-refundable combination is the practical argument for buying smaller amounts more often rather than stockpiling.

### Buying through a third-party channel

Direct purchase isn't practical for everyone. Card declines, unsupported regions, and app-store subscriptions all get in the way, which is why third-party top-up platforms exist. Bewild is one of the platforms serving this space, and it's currently running code **ACCPAY**, which takes **$1 off** an order — the link below carries the code automatically.

Before ordering from any reseller, do two things: check on the page which pack sizes and payment methods are actually offered for your plan and region, and keep in mind the credits themselves follow OpenAI's terms once they land. If you subscribe through the iOS App Store or Google Play, flag that before paying, since app-store billing can interfere with top-ups.

👉 [Open Bewild's Codex credit page with code ACCPAY applied](https://bewild.ai/?code=ACCPAY)

## Which ChatGPT plans can buy Codex credits

Credit purchase isn't open to every account type, and management differs sharply between personal and workspace plans:

| ChatGPT plan | Price | Can you buy credits? | Where credits are managed | Top up |
| --- | --- | --- | --- | --- |
| ChatGPT Free | $0/mo | Limited rollout — visible only if your account is enrolled | Settings → Usage, if enrolled | [ Check availability for Free accounts](https://bewild.ai/?code=ACCPAY) |
| ChatGPT Go | $8/mo | Limited rollout | Settings → Usage, if enrolled | [ Check availability for Go accounts](https://bewild.ai/?code=ACCPAY) |
| ChatGPT Plus | $20/mo | Yes, where available | Personal Settings → Usage or Codex app | [ Top up a Plus account](https://bewild.ai/?code=ACCPAY) |
| ChatGPT Pro | $100–$200/mo | Yes, where available | Personal Settings → Usage or Codex app | [ Top up a Pro account](https://bewild.ai/?code=ACCPAY) |
| Business / Enterprise / Edu | Workspace pricing | Yes — pooled workspace credits | Admin-managed in workspace Billing | [ Review workspace credit options](https://bewild.ai/?code=ACCPAY) |

On Business and Enterprise plans, credits are workspace pools rather than personal balances, so if you can't add credits yourself, that's a conversation with your workspace owner or admin. Plus users also have a specific reason to care about credits: OpenAI's pricing pages note that Plus includes only limited usage of the flagship reasoning tier, and credits are the official way to get more of it without jumping to Pro.

## Credits vs. the other ways past a limit

Credits are one of five options when your quota runs dry, and picking the right one depends on how often you actually hit the wall:

| Option | How it works | Cost | Fits when |
| --- | --- | --- | --- |
| Purchased credits | Overflow balance drawn automatically after included limits | Metered per token; varies by account and region | Occasional overflow, crunch weeks |
| Paid instant reset | Pulls your next weekly allowance forward immediately | One-time fee, shown at checkout; personal Plus and Pro only | You need this week back, now |
| Banked reset | Promotional grants redeemed in Settings → Usage | Free, offer-dependent | You have an active promo |
| Wait for recovery | Rolling 5-hour and scheduled weekly resets | Free | You can schedule around limits |
| API key billing | Authenticate the Codex CLI with an OpenAI API key | Platform token rates | You already run API infrastructure |

The judgment is straightforward once you know your own usage pattern. If you hit the wall a few times a month or want a safety net during a crunch week, credits are the flexible answer. If you're hitting hard limits three or more times a week, do the math on a Pro upgrade instead — at that volume, repeated overflow purchases usually lose to the bigger included allowance. And if you're running heavy automation and already have API infrastructure, authenticating Codex with an API key sidesteps subscription windows entirely, at platform token rates.

## How to make your credits last longer

None of these tricks change the rates; they change how many tokens you feed the meter:

- **Right-size the model.** Routine edits on Luna or Terra cost a fraction of the same work on Sol. Save the expensive models for the problems that need them.
- **Leave fast mode off** unless you're actually waiting on a result. It bills at a higher rate.
- **Trim context.** OpenAI's own advice: shrink AGENTS.md (nest it by directory in large repos), disable MCP servers you aren't using, and point Codex at the relevant files instead of the whole tree.
- **Watch reasoning depth.** Reasoning tokens bill as output, and modes like Ultra may spawn additional agents, each generating their own tokens.
- **Check the usage page every week or two.** That's OpenAI's suggested rhythm, and it tells you early whether credits or an upgrade is the better spend.

## Codex credits FAQ

**Do Codex credits expire?**
Yes. Purchased credits expire 12 months after purchase with no rollover. Promotional credits follow the terms of the specific offer.

**Are Codex credits the same as API credits?**
No. They're separate balances on separate systems. Usage credits pay for Codex, ChatGPT Work, and ChatGPT for Excel overflow; API credits pay for developer platform requests. Neither converts into the other.

**Does buying credits reset my 5-hour or weekly limits?**
No. Your plan's included usage is always consumed first and resets on its normal schedule. Credits only kick in after a limit is reached.

**Why did my balance go negative?**
Concurrent tasks or a long multi-step run drained the balance mid-execution. Your next purchase or auto-reload offsets the negative amount before adding new capacity.

**How many credits does a typical task use?**
On GPT-5.6 Sol, OpenAI's estimate is 5 to 40 credits per task. Lighter models like Terra and Luna cost far less for the same work.

**Can I transfer credits to another account or get a refund?**
No. Credits are tied to the purchasing account, have no cash value, and are non-refundable except where the law requires it — so confirm the account and quantity before paying.

## The short version

Codex credits are OpenAI's official overflow balance: your plan goes first, credits cover the gap, and everything is metered per token under a rate card where model choice moves the bill by a factor of 25. They expire after 12 months, don't transfer, and don't reset your limits — they just keep the session alive when the weekly quota would otherwise stop it.

Buy them through Settings → Usage if your account and payment method cooperate. If they don't, third-party platforms fill the gap, and Bewild's current welcome code takes a dollar off to soften the first order:

👉 [Grab the $1-off ACCPAY code at Bewild](https://bewild.ai/?code=ACCPAY)

Occasional overflow, buy credits. Weekly walls, upgrade. Everything else is just picking the right model for the task in front of you.
