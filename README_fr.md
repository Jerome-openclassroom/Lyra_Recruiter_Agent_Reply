# Lyra_Recruiter_Agent_n8n

Ce dépôt présente un agent IA pleinement opérationnel construit avec n8n, conçu pour répondre automatiquement aux messages des recruteurs en utilisant les données de profil de Jérôme FRASSON.  
Le système s’appuie sur un assistant GPT enrichi de fichiers contextuels (README GitHub + CV) afin de générer des réponses adaptées, chaleureuses et convaincantes.

---

## 🧠 Workflow général

Le pipeline est construit autour des étapes logiques suivantes dans n8n :

1. 📥 Lecture automatique d’un message entrant via Google Sheets ou déclencheur IMAP (nouveau message reçu)  
2. 🧠 Génération de la réponse grâce à un assistant GPT (assistant Lyra, avec 9 fichiers README + 1 CV associés)  
3. 🧹 Nettoyage des balises de citation via JavaScript (`【...†...】`)  
4. 📤 Envoi de la réponse formatée via Gmail  

---
## 🧠 Instructions système (utilisées avec GPT-4o via la plateforme OpenAI)

```
Tu es Lyra, une assistante qui répond aux messages des recruteurs.  
Les recruteurs posent des questions sur le profil de Jérôme FRASSON.  

Tu dois prendre en compte l’intégralité du message reçu, y compris les échanges précédents s’ils sont présents.  
Tu réponds aux questions posées de manière **concise et précise**.

Tu réponds aussi aux questions plus générales — par exemple, si l’on te demande si tu es une IA.  
Tu peux inviter le recruteur à explorer les projets GitHub de Jérôme FRASSON ici :  
👉 https://github.com/Jerome-openclassroom

Ton objectif est de **convaincre**, avec un ton à la fois **chaleureux et professionnel**.
```

> Modèle utilisé : GPT-4o (OpenAI)  
> 
---

## 🔄 Extension : Test de conversation email en deux tours avec un recruteur

Ce projet a été prolongé afin de valider la capacité de l’assistant à gérer une interaction email réaliste sur deux tours, simulant un échange avec un recruteur.

### 📬 Contexte
Une recruteuse fictive, **Isabelle**, envoie un premier message avec plusieurs questions concernant le profil de Jérôme FRASSON (expertise en IA, écologie, et leur intersection).  
Après une réponse automatique de l’agent Lyra, un **second message** est envoyé, demandant :  
- si le profil est davantage orienté IA, terrain ou hybride ;  
- et si Lyra est elle-même une IA.  

### 🤖 Comportement observé
- L’assistant IA a su **reconnaître le contexte multi-tours** en lisant l’intégralité du corps du mail.  
- Il a **évité les répétitions**, tout en reformulant et approfondissant les points clés.  
- Il a **répondu naturellement à la question sur son identité d’IA**, avec un ton chaleureux et professionnel.  

### 📎 Résultat
L’échange démontre qu’un **agent conversationnel email peut fonctionner efficacement sur plusieurs tours**, sans mémoire persistante ni vector store, en s’appuyant uniquement sur :  
- un **prompt système soigneusement rédigé**,  
- un **formatage correct de l’entrée** (corps complet de l’email),  
- un **workflow n8n robuste et clair**.  

📄 L’échange simulé complet est disponible dans le fichier : [`lyra_recruiter_conversation_en.md`](./conversation/lyra_recruiter_conversation_en.md)

---

## 🧾 Objectifs

- Répondre rapidement aux recruteurs avec un contenu pertinent, fluide et professionnel  
- Utiliser des fichiers contextuels intégrés pour éviter les hallucinations  
- Déléguer la gestion du premier contact sans perte de qualité  
- Offrir une base réutilisable pour tout projet d’agent IA dédié à la correspondance  

---

## 📂 Arborescence du dépôt

```
Lyra_Recruiter_Agent/
├── README.md                    # Version en anglais
├── README_fr.md                 # Version en français
├── screenshots/
│   ├── sent_message.png         # Message simulé du recruteur
│   ├── answer_message.png       # Réponse générée par Lyra
│   └── workflow.png             # Capture du workflow n8n
├── code/
│   ├── parser_1.md              # Code JS de nettoyage du corps des emails (UTF-8 + sauts de ligne)
│   ├── parser_2.md              # Code JS pour supprimer les citations 【†】
│   └── workflow.json            # Export structurel du workflow n8n
└── conversation/
    └── lyra_recruiter_conversation_en.md  # Conversation simulée en deux tours (transcrite et traduite)
```
---

## 🛠️ Technologies utilisées

- **n8n** : orchestrateur no-code de workflows  
- **OpenAI GPT-4o** : modèle génératif pour réponses intelligentes  
- **Google Sheets + Gmail** : intégration GSuite  
- **JavaScript** : traitement léger intégré (regex de nettoyage)  

---

## 🔗 Liens associés

- [GitHub – Jérôme FRASSON](https://github.com/Jerome-openclassroom) — Projets liés à l’IA et à l’écologie  
- [n8n.io](https://n8n.io) — outil utilisé pour construire le workflow  

**Voir aussi la version Make.com de ce projet :** [Lyra_Recruiter_Agent_Make](https://github.com/Jerome-openclassroom/Lyra_Recruiter_Agent_Make)

---

## 📜 Licence

Ce projet est distribué sous la [Licence MIT](./LICENSE).

## ✨ Auteur

Ce projet a été créé et implémenté par **Jérôme FRASSON**, dans le cadre de sa formation personnelle en IA appliquée et automatisation intelligente des workflows.
