# Attune: Product Brief

*A DISC-focused sales tool for live calls.*

## Problem
B2B reps run one script for every prospect, but prospects take in information differently: some want the bottom line in 20 seconds, others want data, reassurance or rapport first. Reps trained in DISC rarely apply it live, because reading a style takes attention they don't have and rewriting a script mid-call is impossible. Existing DISC sales tools mostly guess a prospect's style before the call from public profiles, which is unreliable and feels like profiling. Nothing combines a live, behavior-based read with the rep's own script adapted during the call.

## Persona
**An individual B2B account executive or SDR** running cold, discovery and demo calls on a laptop beside a dialer or video call. Some DISC training. On a call, they can spare glances and taps, not reading or typing.

## Jobs to be done
1. *When I'm minutes into a call*, help me form a quick, defensible read of how this person likes to communicate, *so I stop guessing.*
2. *When I know their style*, give me my own script adapted for them, right now, *so I sound like I'm talking to them, not at them.*
3. *When my script has legal or compliance wording*, guarantee that text never changes, *so adapting is safe.*
4. *After calls*, show me whether my reads are fast and right, *so I improve.*

## How it works
Prepare the script → start the call → tap how the prospect answers a few natural questions, at any point → the read updates live (primary, secondary, confidence and a one-line "why") → each upcoming section appears next to an adapted version → correct the read with one tap at any time.

## The questions
Five short, conversational questions double as real discovery, so they never feel like a test. The rep taps *how* the prospect answered (e.g. "short and blunt", "talks it through"), never a label. Several can be answered from lines already in the rep's script, such as the reaction to the opener or to the close. Optional observations (pace, tone, conversation style, formality) add the rest of the signal.

## Scope

**Shipped**
- Call editor: scripts in named sections, locked compliance text, private rep notes, templates
- Live Call Screen: questions in any order with skip, observations, deterministic scoring, read card with correction, style guide, side-by-side reader with change highlighting, keyboard navigation
- Hand-written D/I/S/C versions for a built-in school cold call script (14 sections × 4 styles)

**Next**
- AI adaptation of any script, streamed section by section, behind the same lock and fact checks
- Call-type modes, placeholder fill-in before dialing, personal stats

**Not in v1**
Accounts, teams, CRM integration, call recording or transcription, voice-based detection, billing, and any inference from social profiles.

## Success metric
**Time to an accurate read.**
- **Speed:** median of 2 minutes or less from call start to a Medium-confidence read.
- **Accuracy:** at least 75% of reads rated "accurate" by the rep after the call, and at least 90% "accurate or partly".
- **Guarding against self-confirmation:** a rep tends to confirm their own read, so Attune also tracks signals that are harder to fool yourself on: how consistent the answers are, the prospect's own stated preference for how to receive information, and whether the call booked a next step.

## Key design decisions
| Decision | Why |
|---|---|
| Transparent, weighted scoring in the browser instead of AI | Instant, explainable ("why" line), and works offline |
| The read is a hypothesis with a confidence level, and the rep can override it | DISC is a simplified model; the rep's judgment should win |
| Adaptation strength follows confidence | A tentative read shouldn't rewrite the script |
| Locked text is enforced in code, not trusted to a model | Compliance wording must come back word for word |
| Adapted versions may restructure and add connective lines, never new facts | Truthfulness on a live call is non-negotiable |
| Rep notes kept separate from spoken text | Stage directions shouldn't be rewritten or read aloud |
| No accounts; data stays in the browser | Privacy first; nothing about a prospect leaves the device |

## Risks and mitigations
| Risk | Mitigation |
|---|---|
| Wrong reads that *feel* accurate | Confidence levels, mixed-signal warnings, extra accuracy signals beyond the rep's own rating |
| Prospects feeling profiled, or reps labeling people | Questions are genuine discovery; no labels shown to or stored about prospects; responsible-use guidance in the app; no social-profile scraping; never for hiring |
| AI inventing claims or changing locked text | Lock placeholders verified in code; checks that reject new numbers or renamed placeholders; fall back to the original |
| Latency on a live call | Adapt only unread sections, in parallel; show the original until the adapted version is ready |

## Roadmap
v0.1 editor, locks, questions and scoring → v0.2 live reader, AI adaptation, stats → v1.0 evaluation across sample scripts and simulated prospects, accessibility and mobile polish → future: a possible Salesforce add-on.
