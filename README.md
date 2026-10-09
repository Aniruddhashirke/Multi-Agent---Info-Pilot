# 🛰️ InfoPilot — Multi-Tool AI Assistant

InfoPilot is an AI-powered assistant built using **Large Language Models (LLMs), LangChain, and specialized API tools** to answer user queries with relevant external information. It intelligently selects the appropriate tool depending on the user's intent, retrieves real-time information, and combines results into a conversational response.

The project integrates weather updates, general web search, and financial news retrieval into a single interactive chatbot powered by a Groq-hosted language model.

## ✨ Features

- 🤖 **AI-Powered Conversations:** Uses an LLM to understand natural-language questions and generate responses.
- 🌤️ **Real-Time Weather Updates:** Retrieves current weather conditions, temperature, humidity, wind speed, and precipitation for a specified location.
- 🔎 **Web Search:** Searches the web for general knowledge, current events, people, companies, and other information.
- 📈 **Financial News:** Fetches recent financial and stock-market news for companies, sectors, and stock tickers.
- 🧠 **Intelligent Tool Selection:** Chooses the most relevant tool based on the user's query.
- 🔗 **Multi-Tool Responses:** Can use multiple tools to answer questions requiring different types of information.
- 💬 **Interactive Chat Interface:** Provides a conversational interface built with Gradio.
- 🛡️ **Error Handling:** Handles missing API keys, unsuccessful requests, timeouts, and empty search results.
- 🔍 **Tool Transparency:** Displays the tools used to generate a response.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangChain | Agent orchestration and tool integration |
| Groq | LLM inference |
| OpenAI GPT-OSS 20B | Configured language model |
| WeatherAPI | Current weather information |
| SerpAPI | Google search results |
| Marketaux | Financial news retrieval |
| Requests | HTTP API communication |
| python-dotenv | Environment variable management |
| Gradio | Interactive chatbot interface |
| Jupyter Notebook | Development and experimentation |

## 🏗️ System Architecture

User
  ↓
Gradio Chat Interface
  ↓
LangChain AI Agent
  ↓
Groq LLM (GPT-OSS 20B)
  ↓
Tool Selection & Routing
  ↓
  ├──→ Weather Tool → WeatherAPI
  │
  ├──→ Web Search Tool → SerpAPI
  │
  └──→ Financial News Tool → Marketaux API
  ↓
External API Responses
  ↓
LLM Response Processing
  ↓
Final Answer Generation
  ↓
Display Response on Gradio Interface


### How It Works

1. The user submits a natural-language query through the Gradio interface.
2. The LangChain agent processes the conversation and determines whether external information is required.
3. The configured language model selects the appropriate tool based on the user's intent.
4. The selected tool retrieves information from its corresponding external API.
5. The agent uses the retrieved results to formulate a concise response.
6. The chatbot displays the answer and, when applicable, the tools used.

## 📂 Project Structure

```text
InfoPilot/
├── InfoPilot.ipynb    # Main notebook and application code
├── .env               # Local API credentials (not committed)
├── .gitignore         # Files excluded from version control
└── README.md          # Project documentation
```

The application is currently implemented in a Jupyter Notebook. The structure above describes the recommended repository organization.

## ⚙️ Installation and Setup

### Prerequisites

- Python 3.10 or newer recommended
- Jupyter Notebook or Google Colab
- An internet connection
- API credentials for the services used by the application

### Step 1: Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd InfoPilot
```

Replace the placeholder with your actual GitHub repository URL.

### Step 2: Create a Virtual Environment (Recommended)

```bash
python -m venv venv
```

Activate it on Windows:

```powershell
.\venv\Scripts\Activate.ps1
```

Activate it on macOS or Linux:

```bash
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -U langchain langchain-core langchain-groq requests==2.32.4 python-dotenv gradio jupyter
```

### Step 4: Configure API Keys

Create a `.env` file in the project directory and configure the following variables using your own API credentials:

```env
GROQ_API_KEY=your_groq_api_key
SERPAPI_API_KEY=your_serpapi_api_key
MARKETAUX_API_KEY=your_marketaux_api_key
FREEWEATHER_API_KEY=your_weatherapi_key
```

Obtain credentials from the respective service providers:

- **Groq:** https://console.groq.com/
- **SerpAPI:** https://serpapi.com/
- **Marketaux:** https://www.marketaux.com/
- **WeatherAPI:** https://www.weatherapi.com/

The notebook currently prompts for missing API keys interactively using `getpass()`. If you use the `.env` file, load its values before running the configuration cells:

```python
from dotenv import load_dotenv

load_dotenv()
```

**Important:** Keep API keys private. Never upload your `.env` file to GitHub.

### Step 5: Run the Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open `InfoPilot.ipynb` and execute the cells in order, from dependency installation and API configuration through agent initialization and Gradio interface launch.

## 💡 Example Queries

Try the following queries after starting the application:

**Weather**
- What is the current weather in Mumbai?
- What is the temperature in Nagpur?
- Tell me the humidity and wind speed in Pune.

**General Web Search**
- Who is the current CEO of NVIDIA?
- What are the latest developments in artificial intelligence?
- Explain the applications of blockchain technology.

**Financial News**
- What is the latest financial news about NVIDIA?
- Find recent stock-market news about Reliance Industries.
- What are the latest earnings developments for Microsoft?

**Multiple Tools**
- What is the weather in Bengaluru and the latest financial news about Infosys?
- Give me the current weather in Mumbai and recent financial news about TCS.

## 🔐 Security and Reliability

InfoPilot incorporates basic safeguards to improve reliability:

- Checks whether required API keys are configured.
- Uses request timeouts to avoid waiting indefinitely for API responses.
- Handles unsuccessful API requests and empty search results.
- Instructs the agent not to fabricate information that should come from external tools.
- Keeps API credentials outside the application logic.

For production use, add API rate limiting, stronger input validation, structured logging, secure secret management, and appropriate handling of provider errors.

## 🚀 Future Enhancements

Potential improvements include:

- Add a dedicated stock-price and market-data tool.
- Introduce conversation memory and user preferences.
- Add source citations and clickable references in the chatbot.
- Implement streaming responses for a more responsive interface.
- Build a dedicated frontend using React or Next.js.
- Add authentication and user-specific chat history.
- Deploy the application using Hugging Face Spaces, Render, or another suitable hosting platform.
- Add automated tests and monitoring for tool failures.
- Support additional specialized agents for research, productivity, and data analysis.

## 🎯 Project Objective

The objective of InfoPilot is to demonstrate how LLMs can be combined with external APIs and tool-calling capabilities to build a practical AI assistant that retrieves relevant information instead of relying solely on the model's internal knowledge.

## 🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Implement and test your changes.
4. Commit your changes with a descriptive message.
5. Submit a pull request.

## 📄 License

This project is available for educational and research purposes. Add a suitable open-source license, such as the MIT License, if you intend to permit reuse and redistribution.

## 👨‍💻 Author

**Aniruddha Shirke**

Artificial Intelligence and Data Science Student

Yeshwantrao Chavan College of Engineering, Nagpur

---

⭐ If you find this project useful, consider starring the repository and contributing to its development.
