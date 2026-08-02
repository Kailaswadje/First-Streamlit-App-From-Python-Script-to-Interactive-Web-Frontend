# 🖥️ First Streamlit App — From Python Script to Interactive Web Frontend (Part 5)

The moment a data scientist becomes a full-stack builder: a **first Streamlit application** that turns pure Python into a live web interface — title, text inputs, a submit button, and dynamic output — in under ten lines of code, no HTML, CSS, or JavaScript required.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-Frontend-FF4B4B?logo=streamlit&logoColor=white)
![Level](https://img.shields.io/badge/Level-Frontend%20Fundamentals-brightgreen)
![Series](https://img.shields.io/badge/GenAI%20Series-Part%205-blueviolet)

---
### 🔗 Live Demo → ... **[https://frontend-first-app.onrender.com](https://frontend-first-app.onrender.com)**

## 📌 Why This Tiny App Matters

Every AI project eventually faces the same question: *how do users actually interact with this?* Notebooks are for building; **apps are for using**. Streamlit is the fastest bridge between the two — and this app is the deliberate first step: mastering the widget → state → rerun model that every Streamlit application, including full LLM chatbots, is built on.

In this series, it's the stepping stone between the chatbot logic of Part 4 and the deployed [LangChain-OpenAI Chatbot](https://github.com/Kailaswadje/Langchain-Openai-Chatbot) web app that follows.

---

## ✨ What the App Does

A simple detail-collection form with live verification:

1. Displays a **page title**
2. Collects the user's **name** via a single-line text input
3. Collects a short **self-description** via a multi-line text area
4. Waits for a **button click**
5. On submit — echoes the captured details back for verification

Small on purpose: every core Streamlit concept, nothing else.

---

## 🔍 The Code, Line by Line

```python
import streamlit as st

st.title("Hello this is the First front end session")

Name = st.text_input("Enter your name ")
About_yourself = st.text_area("Please say a few words about yourself")

click_button = st.button("Click to submit your details")

if click_button == True:
    st.text("Great !!! we have got your details. lets verify the same ")
    st.text(f"User Name:{Name}")
    st.text(f"Other Details:{About_yourself}")
```

| Line | Widget / Concept | What It Teaches |
|---|---|---|
| `st.title()` | Page heading | Instant page structure — no HTML |
| `st.text_input()` | Single-line input | Widgets **return their current value** into plain Python variables |
| `st.text_area()` | Multi-line input | Same pattern scales to any widget type |
| `st.button()` | Action trigger | Returns `True` only on the run where it was clicked |
| `if click_button:` | Conditional rendering | UI that responds to user actions |
| `st.text(f"...")` | Output display | Dynamic content from captured state |

---

## 🧠 The Big Idea — Streamlit's Execution Model

The non-obvious concept this app quietly demonstrates:

> **Streamlit reruns the entire script top-to-bottom on every interaction.**

- Type in a box → script reruns → `Name` holds the new value
- Click the button → script reruns → `st.button()` returns `True` **for that run only**
- The `if` block renders because this particular rerun was triggered by the click

There is no callback wiring, no event listeners, no state management boilerplate — the script *is* the app. Understanding this rerun loop is the single prerequisite for building anything bigger in Streamlit, and it's why this "hello world" deserves its own project.

---

## 🗂️ Folder Contents

```
05-first-streamlit-app/
├── GenAI_05_First_App.py      # The application
├── requirements.txt           # Dependencies
├── README.md                  # This documentation
└── Project_Explanation.docx   # 250-word project summary
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9+

### Installation & Run

```bash
# Clone the repository
git clone https://github.com/Kailaswadje/genai-learning-series.git
cd genai-learning-series/05-first-streamlit-app

# Install dependencies
pip install -r requirements.txt

# Run the app
streamlit run GenAI_05_First_App.py
```

Streamlit opens the app automatically at `http://localhost:8501`. Type your details, hit submit, and watch the rerun model in action.

---

## 🧪 Try This — Learning Experiments

Small modifications that teach the execution model fast:

- [ ] Add `st.write("script ran")` at the top — watch it print on **every** interaction, proving the full-rerun behaviour
- [ ] Replace `st.text()` with `st.success()` / `st.info()` for styled output
- [ ] Add a `st.selectbox()` for a dropdown field and include it in the verification output
- [ ] Type in the inputs, click submit, then type again — notice the output vanishes (button is `True` for one run only) and reason about why

---

## 🧠 Key Takeaways

- **Widgets are just function calls that return values** — frontend state lands directly in Python variables
- **The whole script reruns on every interaction** — Streamlit's core mental model, demonstrated in its simplest form
- **`st.button()` is momentary** — `True` for a single run; persistent behaviour needs `st.session_state` (the natural next lesson)
- **Ten lines is a real web app** — the barrier between "data science script" and "usable tool" is far lower than it looks
- Every Streamlit LLM app — including my chatbot project — is this exact pattern with an API call inside the `if` block

---

## 📚 GenAI Series Navigation

| Part | Project | Focus |
|---|---|---|
| 01 | OpenAI API Hands-On | SDK fundamentals: chat, embeddings, images |
| 02 | Prompt Engineering with OpenAI | Zero-shot, few-shot, CoT, real tasks |
| 03 | Prompt Engineering with Gemini | Portability, grounding, hallucination probes |
| 04 | Conversational Chatbots | Memory, LangChain, flipped interaction |
| **05 (this folder)** | First Streamlit App | Frontend fundamentals, the rerun model |
| ➡️ Next | [LangChain-OpenAI Chatbot](https://github.com/Kailaswadje/Langchain-Openai-Chatbot) | Parts 4 + 5 combined into a deployed chat app |

---

## 🔮 Possible Extensions

- [ ] Persist submissions across reruns with `st.session_state`
- [ ] Add input validation (empty name warning with `st.warning()`)
- [ ] Save submitted details to a CSV — a working mini registration tool
- [ ] Restyle with `st.columns()` and a sidebar for layout practice

---

## 👤 Author

**Kailas Wadje**
MSc Data Science & AI, University of Liverpool

- GitHub: [@Kailaswadje](https://github.com/Kailaswadje)
- LinkedIn: [linkedin.com/in/kwadaje](https://www.linkedin.com/in/kwadaje/)

---

## 🙏 Acknowledgements

Hands-on practice completed as part of the **Learnbay GenAI programme**.

---

⭐ If this demystified Streamlit's magic for you, consider giving it a star!
