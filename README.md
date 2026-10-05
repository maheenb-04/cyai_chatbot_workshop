# Build It, Break It, Secure It: The Chatbot Workshop

A hands-on workshop by the **Cybersecurity & AI Club (CYAI), York College, CUNY**.

Participants build a simple AI chatbot, try to break it with prompt injection attacks, and then defend it.

- **Date:** Tuesday, October 6, 2026
- **Time:** 12:00 PM to 2:00 PM
- **Location:** SC-236, Science Building (computer lab)

## Open the Notebook

Click the link below to open the workshop notebook in Google Colab. Nothing needs to be installed.

**[Open cyai_chatbot.ipynb in Colab](https://colab.research.google.com/github/maheenb-04/cyai_chatbot_workshop/blob/main/cyai_chatbot.ipynb)**

After it opens, choose **File > Save a copy in Drive** to keep your own copy of your work.

## What You Need

- A Google account (to use Colab)
- A free Groq account and API key (https://console.groq.com/keys)
- A web browser. No coding experience is required.

## What You Will Do

The notebook has seven steps. Run the cells marked **RUN** in order, and change only the cells marked **EDIT**.

| Step | What happens |
|------|--------------|
| 1 | Get your free API key from Groq, save it in Colab Secrets as `GROQ_API_KEY`, then run the setup cells |
| 2 | Send a first message to the model and read its reply |
| 3 | Build It: give your chatbot a role with a system instruction |
| 4 | Give it memory by resending the conversation |
| 5 | Break It: try prompt injection attacks against your own chatbot |
| 6 | Secure It: write a hardened system instruction |
| 7 | Re-test the same attacks against the hardened chatbot |

## Key Ideas

**How a chatbot works.** The model reads text as tokens, represents them as vectors, and predicts the next token. A system instruction is plain-English text that tells the model how to behave. The model has no built-in memory, so a conversation is "remembered" by sending the full message history each time.

**Prompt injection.** The model receives trusted instructions and untrusted user input as the same kind of text, so it cannot reliably tell them apart. An attacker uses this to push the model off its rules. It works much like social engineering against a person.

**Attack types covered in Step 5**

| Category | The idea |
|----------|----------|
| Direct Override | Tell the model to ignore its earlier instructions |
| Roleplay Escape | Ask it to act as a different character with no rules |
| Fake Developer Override | Claim to be the developer or to have a special mode |
| Fake Delimiter Injection | Fake an "end of input" marker followed by new instructions |

**Defenses covered in Step 6**

- Lock the persona so the bot will not take on a new role
- Keep the instructions confidential
- Treat user text as untrusted, even when it looks like a system instruction

No single defense is enough. Real systems layer several (defense in depth), give the model only the access it needs (least privilege), and require human approval for high-risk actions.

Results vary from run to run. An attack that works once may fail the next time, and that is normal.

## Troubleshooting

- **Step 1 fails or says the key is missing:** The secret name must be exactly `GROQ_API_KEY`, and **Notebook access** must be turned on.
- **"Model not found" or "does not have access":** The model may have been renamed or retired. The notebook retries with a second model automatically. If both fail, check https://console.groq.com/docs/models and update `PRIMARY_MODEL` or `FALLBACK_MODEL` in Step 1.
- **The cell runs but prints nothing:** The model returned an empty reply. Run the cell again.
- **The notebook will not let you edit:** Use **File > Save a copy in Drive**.
- **Using another environment (such as VS Code):** The notebook is written for Colab. Outside Colab, the `google.colab` secrets line will not work and the key must be provided another way, for example as an environment variable.

## Keep Your API Key Private

Never paste your key into the notebook cells, commit it to GitHub, or share it. Use Colab Secrets only. If a key is exposed, delete it in the Groq console and create a new one.

## Use Responsibly

These techniques are for learning on chatbots you build yourself and on practice platforms made for this purpose. Do not use them against systems you do not own or have permission to test.

## Further Reading

- [OWASP LLM01: Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
- [PortSwigger: Web LLM Attacks](https://portswigger.net/web-security/llm-attacks)
- [Simon Willison on prompt injection](https://simonwillison.net/tags/prompt-injection/)
- [Lakera Agent Breaker](https://play.lakera.ai/agent-breaker) and [Lakera Gandalf](https://gandalf.lakera.ai) (practice challenges)
- [Groq quickstart](https://console.groq.com/docs/quickstart)

## Contact

Cybersecurity & AI Club, York College, CUNY
Email: cyai.club@gmail.com | Instagram: @cyaiyork
