# Lyra_Recruiter_Agent

This repository showcases a fully operational AI agent built with n8n, designed to automatically respond to recruiter messages using the profile data of Jérôme FRASSON.  
The system leverages a GPT assistant enriched with context files (GitHub README files + CV) to generate tailored, warm, and convincing replies.

---

## 🧠 General Workflow

The pipeline is built with the following logical steps in n8n:

1. 📥 Automatic reading of an incoming message via Google Sheets  
2. 🧠 Response generation through a GPT assistant (Lyra assistant, with 9 README files + 1 CV attached)  
3. 🧹 Cleaning of citation tags using JavaScript (`【...†...】`)  
4. 📤 Sending the formatted reply via Gmail

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
│   ├── sent_message.jpg         # Simulated recruiter message
│   ├── answer_message.jpg       # AI-generated response from Lyra
│   └── workflow.jpg             # Screenshot of the n8n workflow
└── code/
    ├── parser.md                # JavaScript code to remove 【†】 citations
    └── workflow.json            # Structural export of the n8n workflow
```

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
