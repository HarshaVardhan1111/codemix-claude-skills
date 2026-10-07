# codemix-claude-skills

Claude skills that turn Indian code-mixed text (Tanglish, Hinglish and more) into clear, professional English.

## Who it is for

Many people think and type in a mixed language. But at work, they must send messages in English.

These skills are for you if:

- You type in Tanglish (or another mix) every day.
- You need to write to a manager, HR, a client, a teacher or a landlord.
- You want a polite English message you can send right away.

## Skills

| Skill | Language | Status |
|---|---|---|
| [tanglish-to-english](tanglish-to-english/) | Tamil + English | Available |
| hinglish-to-english | Hindi + English | Planned |
| tenglish-to-english | Telugu + English | Planned |

## Examples

**1. Leave request**

You type:

```
sir naalaikku leave venum, udambu sari illa. work handover pannitten
```

Claude writes:

```
Subject: Leave request for [date]

Hi [Manager's name],

I'm not feeling well, so I'd like to take leave tomorrow, [date]. I've already handed over my pending work.

Thanks,
[Your name]
```

**2. Delay message to a client**

You type:

```
client ku reply pannanum — report late aagum, friday kulla anupparen, sorry sollu
```

Claude writes:

```
Hi [Client name],

Sorry for the delay. The report will take a little longer than planned, and I'll send it to you by Friday.

Best regards,
[Your name]
```

**3. Message to a friend**

You type:

```
macha inniku dinner ku vara mudiyathu, office la late aagum. next week paakalam
```

Claude writes:

```
Hey, sorry, I can't make it to dinner today — I'll be stuck late at the office. Let's catch up next week!
```

Text in `[brackets]` is a placeholder. Replace it before you send.

## Install

First, download `tanglish-to-english.skill` from the [latest release](https://github.com/HarshaVardhan1111/codemix-claude-skills/releases/latest).

### claude.ai

1. Go to **Settings > Capabilities**. Turn on **Code execution and file creation**.
2. Go to **[Customize > Skills](https://claude.ai/customize/skills)**.
3. Click **+**, then **+ Create skill**.
4. Click **Upload a skill**.
5. Upload `tanglish-to-english.skill`. [verify] The `.skill` file is a ZIP file. If the upload does not accept it, rename it to `tanglish-to-english.zip` and try again.

On a Team or Enterprise plan, an admin must turn on skills first. See [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude).

### Claude Code

Copy the skill folder to `~/.claude/skills/tanglish-to-english/`:

```bash
git clone https://github.com/HarshaVardhan1111/codemix-claude-skills.git
mkdir -p ~/.claude/skills
cp -r codemix-claude-skills/tanglish-to-english ~/.claude/skills/
```

Claude Code finds the skill on its own. If Claude Code was already open and the `skills` folder is new, run `/reload-skills`.

### Claude API

Skills run inside the code execution tool. First, upload the skill once. Then use its ID in your requests.

```python
import anthropic
from anthropic.lib import files_from_dir

client = anthropic.Anthropic()

# Step 1: upload the skill (do this once, then save skill.id)
skill = client.skills.create(files=files_from_dir("tanglish-to-english"))

# Step 2: use the skill
response = client.messages.create(
    model="YOUR_MODEL_ID",  # any current Claude model
    max_tokens=1024,
    container={
        "skills": [{"type": "custom", "skill_id": skill.id, "version": "latest"}]
    },
    tools=[{"type": "code_execution_20250825", "name": "code_execution"}],
    messages=[{"role": "user", "content": "sir naalaikku leave venum, udambu sari illa"}],
)

for block in response.content:
    if block.type == "text":
        print(block.text)
```

See [Using Agent Skills with the API](https://platform.claude.com/docs/en/build-with-claude/skills-guide) for more.

## How to use

Just type or paste your Tanglish. You do not need a special command.

You can say who it is for ("send to my manager") or where it goes ("WhatsApp", "email"). If you don't, Claude writes a polite work message.

## Limitations

- **Spelling varies.** Tanglish has no fixed spelling (venum, vendum, venun). Claude matches by sound, but it can still misread a word.
- **It never adds facts.** If you did not give a reason, a date or a name, Claude will not invent one. It uses placeholders like `[date]` instead.
- **Always review the message before you send it.** Check names, dates and meaning.

## Roadmap

- More languages: Hinglish, Tenglish, Kanglish, Manglish.
- Reverse mode: explain English emails in simple Tanglish.
- Ready templates: leave, salary slip, bank, landlord.
- Better Tamil script support.

## Contributing

Tamil speakers can add words or fix meanings. You can also add a new language. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[MIT](LICENSE)
