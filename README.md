# WeatherWise: Python-Based Weather Dashboard

WeatherWise is a Python application built in Google Colab that combines real-time weather data retrieval, visualisation, and natural language interaction into a single console-based dashboard. The project demonstrates intentional prompting techniques using AI assistance to guide design, debugging, and iterative improvements.

---

## 🌦 Features

* **Live Weather Retrieval**: Get current weather conditions and 3-day forecasts using `fetch_my_weather` API.
* **Interactive Menu System**: Console-based menu with options for forecasts, charts, NLP queries, and moon phases.
* **Visualisation**: Generate temperature and precipitation charts using `matplotlib`.
* **Natural Language Questions**: Ask questions like "Will it rain tomorrow in Perth?" and receive accurate responses.
* **Robust Error Handling**: Handles missing data, invalid locations, and poor input.
* **Mock Data Support**: Enables consistent testing with simulated data.
* **Fuzzy Location Matching**: Suggests corrections for misspelled city names.

---

## 🔧 Setup Instructions

### Requirements

* Google Colab (preferred)
* Python 3.8+
* Required Libraries:

  ```bash
  pip install pyinputplus
  pip install rapidfuzz
  ```

### How to Run

1. Open the notebook (`WeatherWiseFinalNotebook.ipynb`) in [Google Colab](https://colab.research.google.com).
2. Run all cells in sequence.
3. At the bottom of the notebook, run `main()` to start the application.

---

## AI Prompting Techniques Used

This project was built through intentional prompting with ChatGPT. Techniques demonstrated include:

* Problem restatement
* Pseudocode before implementation
* Input/output identification
* Requesting modularity improvements
* Edge case testing and refinement
* Before/after iterative prompting

See the `ai_conversations` folder for full transcripts.

---

## 📁 Project Structure

```
WeatherWise/
├── WeatherWiseFinalNotebook.ipynb            # Final notebook with full implementation
├── ai_conversations/                # Text logs of AI conversations
│   ├── conversation1.txt
│   ├── conversation2.txt
│   └── ...
├── README.md                        # This file
```

---

## ✨ Credits

* Built by: Thomas Brain Angel
* Lecturer: Michael Borck
* API Used: fetch_my_weather (weather data)
* AI Assistant: ChatGPT (OpenAI)

---
