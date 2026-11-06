# 🩺 Health Chatbot

A conversational health assistant built with **Python**, **Streamlit**, and **Groq** — created during the **5-Day Data Science with Gen AI Workshop** by [Innomatics Research Labs](https://in.linkedin.com/school/innomatics-research-labs/).

**🔗 Live Demo:** https://healthchatbot-qrm3kmjp9abe3jtjttj77x.streamlit.app/

**💻 Repository:** https://github.com/SrinisthaD/health_chatbot

> ⚠️ **Disclaimer:** This is a learning project and is **not medical advice**. Always consult a qualified healthcare professional for medical concerns. In case of a possible emergency, seek urgent medical care.

---

## ✨ Features

- 💬 **Conversational health Q&A** powered by Groq's `openai/gpt-oss-120b` model
- 🛡️ **Health-only guardrails** — politely refuses off-topic questions (sports, politics, coding, etc.)
- 🧠 **Session-state chat memory** — maintains context across multiple turns
- 🧹 **Clear Chat** button to reset the conversation
- ⚡ **Fast inference** via the Groq API
- 🚨 **Safety-first prompt design** — no diagnoses, no prescriptions, emergency guidance included
- ☁️ **Deployed** on Streamlit Community Cloud

---

## 🛠️ Tech Stack

| Layer | Tool | Version |
|-------|------|---------|
| Language | Python | `3.14.2` |
| LLM Provider | Groq SDK | `1.7.0` |
| Model | `openai/gpt-oss-120b` | — |
| Frontend | Streamlit | `1.66.1` |
| Env Management | python-dotenv | `1.2.4` |
| Deployment | Streamlit Community Cloud | — |

**Key libraries:** `groq`, `streamlit`, `python-dotenv`

---

## ⚙️ How It Works

1. **User input** is captured via Streamlit's `st.chat_input`.
2. The message is **appended to `st.session_state.messages`**, which preserves chat history across reruns.
3. A **strict system prompt** is prepended to every request, enforcing:
   - Health-only topic scope
   - No diagnoses or prescriptions
   - Emergency guidance for urgent cases
   - A disclaimer with medical information
4. The message list is sent to **Groq's `openai/gpt-oss-120b`** model (`temperature=0.3`, `max_tokens=700`).
5. The response is **displayed in the chat** and stored in session state for continuity.

---

## 🚀 Run Locally

### Prerequisites
- Python **3.10+** (built and tested on 3.14.2)
- A **Groq API key** — get one free at [console.groq.com](https://console.groq.com)

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/SrinisthaD/health_chatbot.git
cd health_chatbot

# 2. (Optional) Create and activate a virtual environment
python -m venv venv
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Add your Groq API key
# Create a .env file in the project root with:
# GROQ_API_KEY=your_api_key_here

# 5. Run the app
streamlit run groq_app.py
