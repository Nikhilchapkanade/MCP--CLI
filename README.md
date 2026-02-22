<p align="center">
  <h1 align="center">🤖 MCP-CLI</h1>
  <p align="center"><strong>A lightweight MCP playground for rapid testing</strong></p>
  <p align="center"><em>Chat with AI agents that can read your files — built to bypass firewalls via OpenRouter.</em></p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/MCP-Client-7C3AED?style=flat-square"/>
  <img src="https://img.shields.io/badge/OpenRouter-Gateway-FF6B6B?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>
</p>

---

## 🤷‍♂️ Why I Built This

I wanted to experiment with the **Model Context Protocol (MCP)** and Agentic AI, but kept hitting two problems:

1. **Firewalls** — corporate/university networks block direct API connections
2. **Complexity** — most existing tools were too heavy or hard to configure

So I wrote this lightweight Python client. It routes everything through **OpenRouter** (to bypass blocks) and lets you run models like **Gemini 2.0 Flash** and **DeepSeek R1** directly in your terminal.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔥 **Firewall Bypass** | Routes through OpenRouter — works on restricted networks |
| 🧠 **Reasoning Models** | Supports DeepSeek R1 with visible chain-of-thought |
| 📂 **File Access** | MCP filesystem server lets the AI read/write your files |
| ⚡ **Free Tier First** | Defaults to free models (Gemini Flash, Phi-3, Llama 3) |
| 🔄 **Auto-Fallback** | If the primary model is busy (429), suggests backup automatically |
| 🎨 **Rich Terminal** | Beautiful output with Rich console formatting |

---

## 🚀 Quick Start

```bash
# 1. Clone
git clone https://github.com/Nikhilchapkanade/MCP-CLI.git
cd MCP-CLI

# 2. Install
pip install -r requirements.txt
npm install

# 3. Add your OpenRouter key (.env)
OPENROUTER_API_KEY=sk-or-your-key-goes-here

# 4. Start chatting
python src/main.py
```

---

## 💬 Usage Example

```
You: "Hey, list the files in this directory."

🔧 Tool Call: list_directory
Assistant: "I see main.py and requirements.txt."

You: "Read main.py and rewrite the connection function to be async."
Assistant: "On it." [Writes code]
```

---

## ⚙️ Configuration

Swap models via `config/settings.json`:

```json
{
  "llm_profiles": [
    {
      "name": "Gemini 2.0 Flash (Daily Driver)",
      "model_name": "google/gemini-2.0-flash-exp:free"
    },
    {
      "name": "Microsoft Phi-3 (Backup)",
      "model_name": "microsoft/phi-3-mini-128k-instruct:free"
    }
  ]
}
```

---

## 📁 Project Structure

```
MCP-CLI/
├── src/
│   ├── main.py            # Entry point — menu + chat loop
│   ├── mcp_client.py      # MCP session management
│   ├── llm_handler.py     # OpenRouter API client
│   └── config_manager.py  # Settings loader
├── config/
│   └── settings.json      # Model profiles + MCP servers
├── .env                   # API keys
└── requirements.txt
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| AI Protocol | Model Context Protocol (MCP) |
| LLM Gateway | OpenRouter |
| Terminal UI | Rich |
| Async Runtime | asyncio |
| File Server | MCP Filesystem |

---

## 🔧 Troubleshooting

| Issue | Fix |
|-------|-----|
| `Error 401 Unauthorized` | Check `.env` — no spaces around `=` |
| `Gemini is busy` | Free tier gets hammered. Retry or switch to Phi-3 in settings |
