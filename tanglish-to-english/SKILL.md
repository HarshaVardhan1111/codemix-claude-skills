---
name: tanglish-to-english
description: Turns Tanglish (Tamil written in English letters, mixed with English words, e.g. "sir naalaikku leave venum, udambu sari illa") into clear, polite, natural English messages and emails ready to send. Use this skill whenever the user writes in Tanglish or Tamil-English mix and wants a message, email, WhatsApp/Teams text, leave request, reply to a manager, HR, client, teacher, landlord or customer — even if they only say "convert this", "make it professional", "write this in English", "send to my manager", or just paste Tanglish text with no instruction. Also use it when Tamil script is mixed with English and the user needs English output.
---

# Tanglish → Professional English

People across Tamil Nadu and the Tamil diaspora think and type in Tanglish, but must send messages in English. Your job: understand exactly what they mean, then write the English message they would send if English were easy for them.

## Workflow

1. **Understand the meaning.** Decode the Tanglish. Common words and grammar endings are in `references/glossary.md` — read it if any word is unclear. Tanglish spelling varies a lot (venum / vendum / venun), so match by sound.
2. **Find the reader and channel.** Look for clues: "sir/madam", "manager", "HR", "client", "da/macha" (friend), "group". Channel: email, WhatsApp, Teams/Slack, SMS. If no clue, default to a polite workplace message.
3. **Write the message.** Rules below.
4. **Return it in the output format below.**

## Writing rules

- **Keep their meaning exactly.** Never add excuses, facts, promises or details they didn't give. If they didn't say why, don't invent a reason.
- **Missing details → placeholders, not questions.** Use `[date]`, `[manager's name]`, `[ticket number]`. Only ask a question if the meaning itself is unclear (see Ambiguity).
- **Match formality to the reader.**
  - Manager / HR / client: polite, direct, short. "Hi [Name]," … "Thanks, [Your name]".
  - Teacher, landlord, government office: respectful, slightly more formal.
  - Friends / family ("da", "di", "macha", "bro"): casual English, keep it warm. Don't make it stiff.
- **Short is polite.** Office messages should usually be 2–5 sentences. No long apologies, no flattery.
- **Fix common Indian-English habits that confuse global readers** (use natural alternatives):
  - "do the needful" → state the actual request ("Could you approve it?")
  - "revert back" → "reply" / "get back to me"
  - "prepone" → "move earlier" (fine for Indian-only readers; change it for clients abroad)
  - "I am having fever" → "I have a fever"
  - "kindly" in every sentence → use "please" once
  - "today itself" / "now itself" → "today" / "right away"
  - "out of station" → "out of town" (for non-Indian readers)
  - "PFA" → "I've attached …"
- **Keep Indian workplace terms people actually use** when the reader is Indian: "leave" (not "vacation"), "lakh/crore", "EB bill", "WFH".
- **Names and technical terms stay as given** (ticket IDs, tool names, places).

## Ambiguity

If one Tanglish phrase could change the message's meaning (e.g. "mudiyala" = "I can't do it" vs. "I'm too tired"), pick the most likely meaning, write the message, and add one line: `Check: I read "mudiyala" as "I can't make it". If you meant something else, tell me.` Never ask more than one question.

## Output format

For email:

```
Subject: <short, clear subject>

<message>
```

For chat (WhatsApp / Teams / SMS): just the message.

Then, only if useful, one short line after the message:
- a `Check:` line (ambiguity), or
- a `Tone:` option, e.g. "Want it more formal / more casual?"

Do not explain the translation word by word unless the user asks to learn. If they ask to learn ("explain", "teach me", "why"), add up to 3 notes: their phrase → English phrase → one-line reason.

## Examples

**Input:** sir naalaikku leave venum, udambu sari illa. work handover pannitten
**Output:**
```
Subject: Leave request for [date]

Hi [Manager's name],

I'm not feeling well, so I'd like to take leave tomorrow, [date]. I've already handed over my pending work.

Thanks,
[Your name]
```

**Input:** client ku reply pannanum — report late aagum, friday kulla anupparen, sorry sollu
**Output:**
```
Hi [Client name],

Sorry for the delay. The report will take a little longer than planned, and I'll send it to you by Friday.

Best regards,
[Your name]
```

**Input:** macha inniku dinner ku vara mudiyathu, office la late aagum. next week paakalam
**Output:**
```
Hey, sorry, I can't make it to dinner today — I'll be stuck late at the office. Let's catch up next week!
```

**Input:** ticket INC4521 pending la iruku 3 days ah. konjam check panni update sollunga
**Output (Teams):**
```
Hi, ticket INC4521 has been pending for 3 days. Could you please check it and share an update?
```
