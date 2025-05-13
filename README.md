# 🏥 AI Healthcare Assistant with ReAct using LlamaIndex
This project is an intelligent AI-powered Healthcare Assistant built using LlamaIndex, Groq’s blazing-fast LLMs (like llama-3-70b), and Wikipedia-based tools to answer medical questions about diseases, symptoms, and medications. It uses ReAct-style agent prompting to combine reasoning and tool use for reliable responses.

# 🚀 Features
- 🔍 Answers symptom-related queries using Wikipedia as a knowledge base.

- 💊 Recommends medications and dosages from a local JSON file.

- 🧠 Powered by llama-3.3-70b-versatile model via Groq API.

- 📚 Vector-based RAG setup using HuggingFace embeddings.

- 🤖 ReAct Agent handles multi-step reasoning using tools only — no LLM memory.

# 🛠️ Setup Instructions
1. 🔑 API Keys & Dependencies
Make sure to save your Groq API key in Colab:

```python
from google.colab import userdata
# Make sure to store 'GROQ_API_KEY' in Colab's user secrets
```

Install required libraries:

```bash
pip install llama-index llama-index-llms-groq llama-index-embeddings-huggingface
pip install nest_asyncio
```

2. 💼 Clone the Repository & Add Medication File
```bash
git clone https://github.com/shaadclt/Heathcare-Assistant-Agent-ReAct.git
cd Heathcare-Assistant-Agent-ReAct
```
Place your Medications and dosages.json file in the project directory.

# 📁 Project Structure
```bash
.
├── Medications and dosages.json     # JSON file with diseases and medications
├── healthcare_assistant_agent_react.ipynb     # Main notebook for the assistant
├── README.md
├── LICENSE.txt
```

# 📚 How It Works
1. **Embeddings**: Uses BAAI/bge-small-en-v1.5 to convert medication info into embeddings.

2. **LLM**: Uses llama-3.3-70b-versatile via Groq API for fast, smart reasoning.

3. **Tools**:

  - `WikipediaToolSpec`: For symptoms and disease info.

  - `QueryEngineTool`: For retrieving medication data from local JSON.

4. Agent: A `ReActAgent` coordinates tool usage with context-specific instructions.

# 🧪 Example Query
```python
response = healthcare_agent.chat("Which medication should I take for arthritis?")
print(response.response)
```
**Sample Output:**

```pgsql
Response: You can consider medications such as Ibuprofen or Naproxen for arthritis. Dosages typically range from 200mg to 400mg twice daily. Always consult a physician before use.
```

# 🧠 Agent Prompt Context
```text
You are a healthcare assistant who can answer questions regarding 
diseases, their symptoms and medications for them.

Use the Wikipedia tools to answer questions about symptoms and possible 
diseases associated with those symptoms. 
Use the medication tool to find list of medications and dosages for a given
disease.

Use only the tools provided to answer questions and NOT your own memory.
```

# 📄 License
This project is open-source and available under the [MIT License](LICENSE.txt).

# ✨ Contributions
PRs and suggestions welcome! Feel free to fork the repo and enhance tool specs, add datasets, or support more agents.
