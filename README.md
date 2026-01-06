
# Autonomous Multi-Agent Orchestration System

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![LangGraph](https://img.shields.io/badge/LangGraph-Agentic-orange)
![Llama 3](https://img.shields.io/badge/Model-Llama%203%20(Groq)-purple)

## 🚀 Project Overview

The **Autonomous Multi-Agent Orchestration System** is a sophisticated agentic workflow engine designed to solve complex, multi-step problems by delegating sub-tasks to specialized AI agents. 

Unlike traditional chatbots that rely on a single prompt, this system uses a **Supervisor Architecture** built on **LangGraph**. A central "Supervisor" LLM (Llama 3) analyzes user intent and dynamically routes queries to the most appropriate tool-enabled agent (e.g., Math, Search, Weather, or Reasoning). The system features a **real-time React frontend** that visualizes the agent's decision-making process (Chain-of-Thought) via Server-Sent Events (SSE).

## 🏗️ Architecture

The system utilizes a **Directed Acyclic Graph (DAG)** to manage state and control flow between agents.

```mermaid
graph TD
    User(User Query) --> Supervisor{Supervisor Agent<br/>
    
    Supervisor -->|Calculations| MathAgent[Math Agent]
    Supervisor -->|Current Events| SearchAgent[Search Agent]
    Supervisor -->|Live Data| WeatherAgent[Weather Agent]
    
    MathAgent --> Supervisor
    SearchAgent --> Supervisor
    WeatherAgent --> Supervisor
    
    Supervisor -->|Final Answer| Response(Streaming Response via SSE)

```

## ✨ Key Features

* **🤖 Supervisor-Worker Architecture:** A centralized decision-making node (Supervisor) that routes tasks to specialized workers, preventing context pollution and improving accuracy.
* **⚡ Real-Time Reasoning (SSE):** Uses Server-Sent Events to stream the agent's internal "thought process" and tool outputs to the UI instantly, reducing perceived latency.
* **🧠 Advanced Tool Use:** Integrated with **Tavily Search**, **OpenWeatherMap**, and **Python REPL** to handle queries requiring real-time data or precise calculation.
* **🔄 State Management:** Leverages **LangGraph** to maintain global state across multiple agent turns, allowing for iterative error correction and refinement.
* **🌐 Modern Frontend:** Built with **React.js** and **Tailwind CSS** to provide a clean, chat-interface with live status updates (e.g., "Searching Wikipedia...", "Calculating...").

## 🛠️ Tech Stack

* **Orchestration:** LangGraph, LangChain
* **LLM Engine:** Llama 3 (via Groq API) for sub-second inference.
* **Backend:** Flask (Python), Server-Sent Events (SSE).
* **Frontend:** React.js, Tailwind CSS, Framer Motion.
* **Tools:** Tavily Search API, OpenWeatherMap API, Wikipedia.

## 🚀 Installation & Setup

### Prerequisites

* Python 3.10+
* Node.js & npm
* API Keys for **Groq**, **Tavily**, and **OpenWeatherMap**.

### 1. Clone the Repository

```bash
git clone [https://github.com/ishaq019/Autonomous-Multi-Agent-Orchestration-System.git](https://github.com/ishaq019/Autonomous-Multi-Agent-Orchestration-System.git)
cd Autonomous-Multi-Agent-Orchestration-System

```

### 2. Backend Setup

Navigate to the server directory and install dependencies.

```bash
cd backend
pip install -r requirements.txt

```

Create a `.env` file in the `backend` folder:

```env
GROQ_API_KEY=your_groq_key
TAVILY_API_KEY=your_tavily_key
OPENWEATHERMAP_API_KEY=your_weather_key

```

Run the Flask server:

```bash
python app.py

```

### 3. Frontend Setup

Open a new terminal, navigate to the frontend directory, and start the React app.

```bash
cd frontend
npm install
npm start

```

## 📸 Usage

1. Open your browser to `http://localhost:3000`.
2. Enter a complex query like:
> *"What is the current temperature in New York and what is that value times 15?"*


3. Watch as the **Supervisor** delegates the weather check to the *Weather Agent*, retrieves the result, passes it to the *Math Agent* for calculation, and synthesizes the final answer.

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements.

## 📄 License

This project is licensed under the MIT License.

```

***

### **Consultant's Tip for Your Resume:**
When you upload this code, ensure your folder structure matches the `cd backend` and `cd frontend` commands in the README.
* **Root Folder**
    * `backend/` (Put your `app.py` and python files here)
    * `frontend/` (Put your React files here)
    * `README.md` (The file above)
    * `requirements.txt` (List your python libraries)

This structure proves to a recruiter that you know how to separate concerns in a full-stack application.

```
