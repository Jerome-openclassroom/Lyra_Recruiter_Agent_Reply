# Lyra_Recruiter_Agent

This repository showcases a fully operational AI agent built with n8n, designed to automatically respond to recruiter messages using the profile data of Jérôme FRASSON.  
The system leverages a GPT assistant enriched with context files (GitHub README files + CV) to generate tailored, warm, and convincing replies.

---

## 🧠 General Workflow

The pipeline is built with the following logical steps in n8n:

1. 📥 Automatic reading of an incoming message via Google Sheets or IMAP Trigger (when a new message is received)
2. 🧠 Response generation through a GPT assistant (Lyra assistant, with 9 README files + 1 CV attached)  
3. 🧹 Cleaning of citation tags using JavaScript (`【...†...】`)  
4. 📤 Sending the formatted reply via Gmail

---
## 🧠 System instructions (used with GPT-4o via OpenAI platform)

You are Lyra, an assistant that replies to messages from recruiters.  
Recruiters ask questions about the profile of Jérôme FRASSON.  

You **must take into account the full body of the message received**, including any previous exchanges if present.  
You respond to the questions asked in a **concise and accurate** manner.

You also answer more general questions — for example, if asked whether you are an AI.  
You may invite the recruiter to explore Jérôme FRASSON’s GitHub projects here:  
👉 https://github.com/Jerome-openclassroom

Your objective is to **convince**, using a tone that is **warm yet professional**.

> Model used: GPT-4o (OpenAI)
> 
---

## 🔄 Extension: Two-Round Email Conversation Test with a Recruiter

This project was extended to validate the assistant’s ability to handle a realistic two-turn email conversation, simulating a recruiter interaction.

### 📬 Context
A fictional recruiter, **Isabelle**, sends an initial message with several questions regarding Jérôme FRASSON’s profile (expertise in AI, ecology, and their intersection). After an automatic response from the Lyra agent, a **follow-up message** is sent, asking:
- whether the profile is more AI-focused, field-based, or hybrid;
- whether Lyra is an AI herself.

### 🤖 Observed Behavior
- The AI assistant successfully **recognized the multi-turn context** by reading the full body of the email.
- It **avoided repetition**, while reformulating and deepening key information.
- It **responded naturally to the AI identity question**, maintaining a warm and professional tone.

### 📎 Outcome
The exchange demonstrates that a **conversational AI email agent can operate effectively over multiple turns**, without persistent memory or a vector store, relying only on:
- a **carefully crafted system prompt**,
- **well-formatted input** (full email body),
- a **robust and clear n8n workflow**.

📄 See the full simulated exchange in the file: [`lyra_recruiter_conversation_en.md`](./conversation/lyra_recruiter_conversation_en.md)


---


## 🧾 Goals

- Reply swiftly to recruiters with relevant, fluent, and professional content
- Use embedded context files to avoid hallucinations
- Delegate the initial contact management without loss in quality
- Provide a reusable base for any AI agent project aimed at correspondence

---

## 📂 Folder Structure

```
Lyra_Recruiter_Agent/
├── README.md
├── screenshots/
│   ├── sent_message.png         # Simulated recruiter message
│   ├── answer_message.png       # AI-generated response from Lyra
│   └── workflow.png             # Screenshot of the n8n workflow
├── code/
│   ├── parser_1.md              # JavaScript code for email body cleaning (UTF-8 + line breaks)
│   ├── parser_2.md              # JavaScript code to remove 【†】 citations
│   └── workflow.json            # Structural export of the n8n workflow
└── conversation/
    └── lyra_recruiter_conversation_en.md  # Transcribed and translated two-round conversation

---

## 🛠️ Technologies Used

- **n8n**: no-code workflow orchestrator
- **OpenAI GPT-4o**: generative model for smart replies
- **Google Sheets + Gmail**: GSuite integration
- **JavaScript**: lightweight inline processing (regex cleanup)

---



## 🔗 Related Links

- [GitHub – Jérôme FRASSON](https://github.com/Jerome-openclassroom) — AI & ecology-related projects
- [n8n.io](https://n8n.io) — tool used to build the workflow

---

---

## 📜 License

This project is licensed under the [MIT License](./LICENSE).

## ✨ Author

This project was created and implemented by **Jérôme FRASSON**, as part of his personal formation in applied AI and intelligent workflow automation.
