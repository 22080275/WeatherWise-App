
# PROMPTING.md

This document outlines the intentional prompting strategies used during the development of the **WeatherWise** application. The goal was to apply structured AI prompting to guide the implementation, improvement, and refinement of the codebase using ChatGPT.

## 💡 AI Tool Used

- **Tool**: ChatGPT (GPT-4)
- **Purpose**: Guidance for architectural decisions, modular code writing, debugging, visualization logic, and natural language processing.

---

## 🧭 Project Implementation Option Exploration

### Conversation Summary
At the start, I used ChatGPT to explore the three implementation options described in the assessment: 

1. **Advanced Weather Dashboard**
2. **Weather-Aware Chatbot**
3. **Hybrid Approach (Recommended)**

### My Prompt
```
Can you help me compare the three implementation options for the weather project and which one would suit me best? I’m comfortable with Python, matplotlib, and I’d like a balance of UI and chat features.
```

### AI Response Summary
ChatGPT suggested that the **Hybrid Approach** would allow both structured dashboard features and a conversational interface, aligning well with my strengths. It also noted it was the recommended option in the assessment guide.

### Result
I chose the Hybrid Approach and structured the project to include both visualizations and an NLP interface.

---

## 🧠 Prompting Strategies Used

| Strategy | Example |
|----------|---------|
| **1. Restate the problem** | I asked ChatGPT to reword the assignment brief in clearer terms to ensure my understanding. |
| **2. Identify input/output requirements** | I prompted ChatGPT to help me list all the inputs/outputs for the main menu and individual functions. |
| **3. Request pseudocode first** | Before implementing visualisation features, I asked for pseudocode to plan structure. |
| **4. Challenge edge cases** | I asked how to handle invalid city names, empty inputs, and API failures. |
| **5. Request modular improvements** | I asked ChatGPT to split long functions into reusable components like `create_temperature_visualisation()` and `parse_weather_question()`. |
| **6. Ask for code explanations** | Every key function includes embedded `#` comments from ChatGPT explaining what each line does. |
| **7. Iterative improvement** | I refined multiple functions after testing initial AI code — such as adding error handling and validating user locations. |
| **8. Query design trade-offs** | I asked whether to use multiple notebooks or a single modular notebook layout for final submission. |
| **9. Before/After refinement** | I improved the `get_weather_data()` function to use caching and handle mock data properly. |
| **10. Explore third-party integration** | I asked whether to use `wttr.in`, OpenWeatherMap, or the provided `fetch_my_weather` library, and how best to work with it. |

---

## 🔁 Before/After Examples

### Example 1: `get_weather_data()` function

**Initial Prompt:**
```
Write a function to get weather data for a city using fetch-my-weather.
```

**Initial Output:**
```python
def get_weather(location):
    return get_weather(location)
```

**Follow-up Prompt:**
```
Can you add error handling, input validation, and support for mock data?
```

**Improved Output:**
```python
def get_weather_data(location, forecast_days=3, use_mock=False):
    try:
        response = get_weather(
            location=location,
            view_options=str(forecast_days - 1),
            units="m",
            format="json",
            with_metadata=True,
            use_mock=use_mock
        )
        if hasattr(response, "metadata") and response.metadata.error_type:
            print(f"❌ Error occurred: {response.metadata.error_message}")
            return None
        return response.data
    except Exception as e:
        print(f"❌ Unexpected error while fetching weather: {e}")
        return None
```

**Why It Was Effective:**
This made the function production-ready, compliant with mock testing, and protected against crashes.

---

### Example 2: Temperature Chart

**Initial Prompt:**
```
Draw a temperature graph from weather data.
```

**Initial Code:**
```python
plt.plot(data)
```

**Follow-up Prompt:**
```
Please use max and min temperature with dates, title, and axis labels.
```

**Final Output:**
```python
def create_temperature_visualisation(weather_data, output_type='display'):
    dates = []
    max_temps = []
    min_temps = []
    for day in weather_data.weather:
        dates.append(day.date)
        max_temps.append(int(day.maxtempC))
        min_temps.append(int(day.mintempC))
    plt.plot(dates, max_temps)
    ...
```

**Why It Was Effective:**
Prompting helped add all required context for readability and clarity.

---

### Example 3: Handling NLP Questions

**Initial Prompt:**
```
Help me parse a question like 'Will it rain tomorrow in Perth?'
```

**Initial Code:**
Basic regex and no location validation.

**Follow-up Prompt:**
```
Can you improve it to extract time, attribute, and support variations like 'Is it windy tomorrow in Fremantle?'
```

**Final Code Excerpt:**
```python
def parse_weather_question(question):
    time_keywords = {...}
    attribute_keywords = {...}
    match = re.search(r"\b(?:in|for)\s+([a-zA-Z\s]+)", question)
```

**Why It Was Effective:**
It helped create a more flexible NLP parser that could adapt to varied inputs.

---

## 🧾 Summary

This project involved continuous prompting with AI to clarify, structure, and improve a hybrid weather app. I used at least 10 prompting strategies and have documented full conversations in `/ai_conversations` to reflect those strategies.

