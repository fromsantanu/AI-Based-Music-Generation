## **Level 2 Capstone Project: Multi-Style Music / Song Generator**

---

### **1. Project Overview**

In Level 1, you built a simple system:
👉 One prompt → One music output

Now in Level 2, we take a big step forward:

👉 One prompt → Multiple styles → Multiple outputs

This project will allow users to generate **different versions of the same musical idea** in various styles, moods, and instruments.

---

### **2. Core Idea (Simple Understanding)**

Think of this like asking different musicians to perform the same song:

* A **classical musician** plays it softly
* A **rock artist** plays it with energy
* A **folk artist** gives it a regional feel

👉 Same idea, different expression

Your system will do exactly this using AI.

---

### **3. Learning Objectives**

By completing this project, you will learn:

* How to control AI outputs using **detailed prompts**
* How to generate **multiple variations systematically**
* How to simulate **styles (genre, mood, instruments)**
* Why outputs sometimes feel “flat” and how to improve them
* How to structure prompts for better musical results

---

### **4. Real-Life Analogy**

Imagine a film director giving instructions:

* “Play something emotional” → unclear
* “Play a slow violin piece, sad mood, background for rainy scene” → clear

Now imagine:
👉 The director asks **3 different composers** for the same scene

That’s your system:
**One idea → multiple interpretations**

---

### **5. System Architecture**

```
User Prompt
     ↓
Prompt Expansion Layer
     ↓
Style Variations Generator
     ↓
MusicGen Model
     ↓
Multiple Audio Outputs
     ↓
Comparison / Playback
```

---

### **6. Core Features**

---

#### **6.1 Base Prompt Input**

User enters a main idea:

Example:

* “Peaceful morning in a village”
* “Emotional love theme”

---

#### **6.2 Style Selection / Auto Expansion**

The system either:

✔ Lets user choose styles
OR
✔ Automatically generates variations

Examples of styles:

* Classical
* Folk (Bengali, Indian)
* Electronic
* Rock
* Ambient

---

#### **6.3 Prompt Expansion Engine (Important)**

This is the **brain of Level 2**

👉 It converts a simple prompt into multiple detailed prompts

---

**Example:**

Input:

```
"Peaceful morning"
```

Expanded prompts:

```
1. "Soft flute, peaceful morning, slow tempo, Indian village atmosphere"
2. "Ambient piano, calm sunrise mood, relaxing and minimal"
3. "Light acoustic guitar, warm tone, countryside feeling"
```

👉 This is where real control happens

---

#### **6.4 Multi-Output Generation**

```python
outputs = model.generate(expanded_prompts)
```

👉 Each prompt produces a different audio result

---

#### **6.5 Playback & Comparison**

User can:

* Listen to all outputs
* Compare styles
* Choose the best one

---

### **7. Step-by-Step Implementation**

---

#### **Step 1: Load Model**

```python
from audiocraft.models import MusicGen

model = MusicGen.get_pretrained('small')
model.set_generation_params(duration=12)
```

---

#### **Step 2: Take User Input**

```python
user_prompt = input("Enter your idea: ")
```

---

#### **Step 3: Create Style Variations**

```python
styles = [
    "soft flute, Indian classical",
    "ambient piano, calm mood",
    "acoustic guitar, warm and peaceful"
]

expanded_prompts = [f"{user_prompt}, {style}" for style in styles]
```

---

#### **Step 4: Generate Multiple Outputs**

```python
outputs = model.generate(expanded_prompts)
```

---

#### **Step 5: Save Outputs**

```python
from audiocraft.data.audio import audio_write

for i, audio in enumerate(outputs):
    audio_write(f"output_{i}", audio.cpu(), model.sample_rate)
```

---

### **8. Key Concept: Why Multi-Style Matters**

Without variation:

👉 You get **one interpretation**

With variation:

👉 You explore **creative space**

---

Think like this:

* Level 1 → One answer
* Level 2 → Many possible answers

This is closer to **real music composition**

---

### **9. Common Problems & Solutions**

---

#### **Problem 1: Outputs Feel Similar**

**Cause:** Prompts too similar

**Fix:**

* Change instruments
* Change tempo
* Change mood

---

#### **Problem 2: Music Feels “Flat”**

**Cause:** No structure in prompt

**Fix:**
Add details like:

* intro, buildup, rhythm

---

#### **Problem 3: No Cultural Feel**

**Fix:**
Add regional elements:

* “Bengali folk style”
* “Raga-based melody”
* “Tabla rhythm”

---

### **10. Advanced Feature (Optional)**

---

#### **10.1 Parameter Control**

```python
model.set_generation_params(
    duration=15,
    temperature=1.2
)
```

👉 Higher temperature = more creativity
👉 Lower temperature = safer output

---

#### **10.2 User-Controlled Inputs**

Instead of free text only:

* Mood dropdown (Happy, Sad, Calm)
* Instrument dropdown (Flute, Piano, Tabla)
* Style dropdown (Classical, Folk, EDM)

---

### **11. Evaluation Criteria**

---

#### **11.1 Diversity**

* Are outputs clearly different?

#### **11.2 Prompt Quality**

* Are prompts meaningful and structured?

#### **11.3 Musical Relevance**

* Does output match style?

#### **11.4 User Experience**

* Easy to generate and compare?

---

### **12. Final Deliverables**

Your project should include:

✔ Input system
✔ Prompt expansion logic
✔ Multi-style generation
✔ At least 5–10 test cases
✔ Saved audio outputs

---

### **13. Example Test Case**

**Input:**
“Rainy evening”

**Outputs:**

1. Soft piano, emotional
2. Ambient synth, cinematic
3. Light guitar, nostalgic
4. Indian flute, monsoon mood

👉 Same idea → multiple feelings

---

### **14. Suggested Mini UI (Optional)**

You can build a simple interface:

* Input box
* Style selection
* Generate button
* Audio players

---

### **15. Final Insight**

Level 2 is where things become **creative and exploratory**

You are no longer just generating music…

👉 You are **exploring possibilities**

Think of this system as:

**“A room full of musicians, each giving their own version of your idea”**

---

