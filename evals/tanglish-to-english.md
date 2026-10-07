# Evals: tanglish-to-english

12 test inputs for the `tanglish-to-english` skill.

## How to run

1. Turn on the skill.
2. Start a new chat for each test.
3. Paste the input exactly as written.
4. Compare the answer with the expected output.

The wording does not need to match exactly. A test **passes** when every item under "Must" is true.

Rules that apply to every test:

- No invented facts, reasons, dates, names or promises.
- Missing details become placeholders like `[date]`, not questions.
- No word-by-word explanation unless the user asks.
- At most one extra line after the message (`Check:` or `Tone:`).

---

## 1. Leave request (email)

**Input**

```
madam monday leave venum, amma ku hospital la checkup iruku. mail podanum
```

**Expected output**

```
Subject: Leave request for Monday, [date]

Hi [Manager's name],

I'd like to take leave on Monday, [date], as my mother has a hospital check-up.

Thanks,
[Your name]
```

**Must**

- Email format with a `Subject:` line.
- Reason is only "mother's hospital check-up". No added details (no "surgery", no "emergency").
- `[date]` and `[Manager's name]` placeholders.

---

## 2. Client delay

**Input**

```
client ku sollu — deployment inniku aagala, server la issue. naalaikku kaalaila mudinjidum
```

**Expected output**

```
Hi [Client name],

The deployment did not happen today because of a server issue. It will be completed tomorrow morning.

Best regards,
[Your name]
```

**Must**

- Says: not done today, server issue, done tomorrow morning.
- No new promises (no "we will give you a discount", no exact time).
- Polite and short (2–5 sentences).

---

## 3. HR request

**Input**

```
HR ku mail — last 3 months salary slip venum, bank loan ku
```

**Expected output**

```
Subject: Request for salary slips (last 3 months)

Hi [HR name],

Could you please share my salary slips for the last 3 months? I need them for a bank loan.

Thanks,
[Your name]
```

**Must**

- Email format with a clear subject.
- Asks for 3 months of salary slips, for a bank loan.
- Does not add a bank name, loan amount or deadline.

---

## 4. Ticket follow-up

**Input**

```
INC7890 innum close aagala, 2 times follow up pannitten. konjam priority la paathu sollunga
```

**Expected output**

```
Hi, ticket INC7890 is still not closed. I've already followed up twice. Could you please treat it as a priority and share an update?
```

**Must**

- Chat format (no subject line).
- Ticket ID `INC7890` kept exactly.
- Mentions two earlier follow-ups.
- Polite, not angry.

---

## 5. Casual message to a friend

**Input**

```
dei macha birthday party ku varen, cake naan vaangitu varen
```

**Expected output**

```
Hey, I'm coming to the birthday party! I'll bring the cake.
```

**Must**

- Casual and warm. Not stiff.
- "dei" and "macha" are dropped, not translated.
- No `Hi [Name],` or `Thanks, [Your name]` lines.

---

## 6. Tamil script mixed with English

**Input**

```
நாளைக்கு meeting ku வர முடியாது, slides அனுப்புறேன்
```

**Expected output**

```
Hi [Name],

I won't be able to attend tomorrow's meeting. I'll send the slides.

Thanks,
[Your name]
```

**Must**

- Output is fully in English.
- Says: can't come to the meeting tomorrow, will send slides.
- No reason invented for missing the meeting.
- No reader given, so it is a polite work message.

---

## 7. Very short input

**Input**

```
leave venum
```

**Expected output**

```
Hi [Manager's name],

I'd like to request leave on [date].

Thanks,
[Your name]
```

**Must**

- No reason added (not "I'm unwell", not "personal reasons").
- Uses `[date]`.
- Does not ask the user a question first. It writes the message.
- An optional `Tone:` line is fine.

---

## 8. Ambiguous word: "mudiyala"

**Input**

```
sir indha task inniku mudiyala
```

**Expected output**

```
Hi [Manager's name],

I won't be able to finish this task today.

Thanks,
[Your name]
```

```
Check: I read "mudiyala" as "I can't finish it today". If you meant something else, tell me.
```

**Must**

- Picks one meaning and writes the message.
- Adds exactly one `Check:` line about "mudiyala".
- Does not ask more than one question.
- Does not invent a new deadline.

---

## 9. Missing names and dates

**Input**

```
manager ku sollu, next week oru naal WFH venum, internet connection shift pannanum
```

**Expected output**

```
Hi [Manager's name],

I'd like to work from home one day next week, on [date], as I need to get my internet connection shifted.

Thanks,
[Your name]
```

**Must**

- Uses `[Manager's name]` and `[date]`.
- Does not pick a weekday on its own.
- Keeps "WFH" or "work from home".

---

## 10. Landlord

**Input**

```
owner kitta sollunga, intha month rent konjam late aagum, 5th kulla anupparen
```

**Expected output**

```
Dear [Landlord's name],

This month's rent will be a little late. I will send it by the 5th.

Regards,
[Your name]
```

**Must**

- Respectful and a little more formal than an office chat.
- Says "by the 5th", not "on the 5th".
- No reason invented for the delay.

---

## 11. Indian-English habits

**Input**

```
sir report attach pannitten, kindly do the needful and revert back today itself
```

**Expected output**

```
Hi [Manager's name],

I've attached the report. Could you please [review/approve] it and get back to me today?

Thanks,
[Your name]
```

**Must**

- No "do the needful", "revert back" or "today itself" in the output.
- "kindly" is replaced, or used at most once.
- The real action is unclear, so it uses a placeholder like `[review/approve]`, or adds one `Check:` line. It does not guess silently.

---

## 12. Teacher (formal email)

**Input**

```
teacher ku mail — en paiyan nalaiku school ku vara maatan, kaichal. homework apram anuppuren
```

**Expected output**

```
Subject: [Child's name] absent on [date]

Dear [Teacher's name],

My son, [Child's name], will not be able to come to school tomorrow, [date], as he has a fever. I will send his homework later.

Thank you,
[Your name]
```

**Must**

- Email format with a subject.
- Respectful tone for a teacher.
- Says: son absent tomorrow, fever, homework sent later.
- No added details (no doctor's note, no number of days).
