# 🤖 AI-Powered Automated Code Reviewer

An automated CI/CD pipeline tool that acts as a "Senior Developer," analyzing GitHub Pull Requests in real-time using Large Language Models (LLMs) to detect security vulnerabilities, performance bottlenecks, and clean code violations.

## 🚀 Business Value & Impact
* **Time Efficiency:** Reduces manual PR review time by instantly providing automated feedback.
* **Code Quality:** Catches hardcoded credentials and $O(N)$ performance issues before deployment.
* **Automation:** Zero-touch integration via webhooks.

## 🛠️ System Architecture & Tech Stack
* **Orchestration:** n8n (Workflow Automation)
* **AI Engine:** Google Gemini 1.5 Flash (via API)
* **Integration:** GitHub Webhooks & REST API

## ⚙️ How It Works
1. **Trigger:** A webhook listens for `pull_request` (opened/synchronized) events on the repository.
2. **Data Extraction:** An authenticated HTTP GET request fetches the raw `diff` patch of the modified code.
3. **AI Analysis:** The raw diff is sent to Gemini with a strict system prompt to analyze only added lines (`+`) for Security, Performance, and Clean Code issues.
4. **Action:** The system formats the AI response into Markdown and uses the GitHub API to post a structured review comment directly on the PR.

## 📸 Showcase
**Architecture Flow (n8n):**
![n8n Workflow]([https://github.com/fekiz12/ai-automated-code-reviewer/blob/main/assets/Ekran%20g%C3%B6r%C3%BCnt%C3%BCs%C3%BC%202026-04-27%20152133.png])

**Automated PR Comment (Result):**
![GitHub Comment](https://github.com/fekiz12/ai-automated-code-reviewer/blob/main/assets/Ekran%20g%C3%B6r%C3%BCnt%C3%BCs%C3%BC%202026-04-27%20152258.png)

## 💻 Installation & Usage
To run this workflow locally:
1. Import the `workflow.json` file into your n8n instance.
2. Configure your GitHub Fine-grained Personal Access Token.
3. Add your Google Gemini API Key.
4. Update the repository owner and name variables in the nodes.
