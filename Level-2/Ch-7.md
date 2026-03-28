# **Chapter 2.7 — Mini Project**

## 🎯 Build: Prompt → Multiple Variations Generator

*(Your first practical AI music tool)*

---

## 🎯 Objective of This Project

By the end of this mini project, you will:

* Build a simple system that generates **multiple music variations**
* Learn how to **experiment like a composer**
* Understand how **prompt + parameters affect output**
* Create a reusable workflow for your future projects

---

# 🧠 1. Big Idea: Why Multiple Variations?

In real music composition:

👉 A composer never creates just one version

They:

* Try different melodies
* Change tempo
* Experiment with mood

---

## 🎧 Real-Life Analogy

Like writing a sentence:

> First draft → edit → improve → final version

---

👉 Same with AI music:

> Generate → compare → select best

---

# 🧩 2. What You Will Build

---

## 🎯 System Flow

```text
Prompt → Generate 5–10 Variations → Compare → Select Best
```

---

## 🎵 Example

Input:

> “soft emotional piano melody”

Output:

* Version 1 → calm
* Version 2 → slightly dramatic
* Version 3 → more variation
* Version 4 → richer background
* Version 5 → unique pattern

---

👉 You choose the best one

---

# ⚙️ 3. Basic Setup (Simple Python Example)

We’ll use **MusicGen (via Audiocraft)**

---

## 📦 Install (Colab or Local)

```bash
pip install audiocraft
```

---

---

## 🧠 Core Idea in Code

We will:

* Keep same prompt
* Generate multiple outputs

---

## 🧪 Code Example

```python
from audiocraft.models import MusicGen
from audiocraft.data.audio import audio_write

# Load model
model = MusicGen.get_pretrained('facebook/musicgen-small')

# Set parameters
model.set_generation_params(
    duration=15,
    temperature=0.7,
    top_k=50
)

# Your prompt
prompt = ["soft emotional piano melody with slow tempo"]

# Generate multiple variations
num_variations = 5

for i in range(num_variations):
    audio = model.generate(prompt)
    
    # Save each version
    audio_write(f"variation_{i}", audio[0].cpu(), model.sample_rate)
    
print("Generated multiple variations successfully!")
```

---

# 🔍 4. What This Code Does

---

## Step-by-Step

* Loads MusicGen model
* Sets parameters (duration, temperature, top_k)
* Uses same prompt
* Generates **5 different outputs**
* Saves them as audio files

---

👉 Each output is slightly different because of **sampling randomness**

---

# 🎛️ 5. Improve Your Generator (Important)

Now we upgrade it.

---

## 🎯 Idea: Slight Parameter Variation

Instead of same settings, change parameters each time

---

## 🧪 Improved Code

```python
import random
from audiocraft.models import MusicGen
from audiocraft.data.audio import audio_write

model = MusicGen.get_pretrained('facebook/musicgen-small')

prompt = ["soft emotional piano melody with slow tempo"]

for i in range(5):
    
    # Randomize parameters
    temperature = random.uniform(0.5, 1.0)
    top_k = random.choice([30, 50, 80])
    
    model.set_generation_params(
        duration=15,
        temperature=temperature,
        top_k=top_k
    )
    
    audio = model.generate(prompt)
    
    audio_write(f"variation_{i}", audio[0].cpu(), model.sample_rate)

print("Smart variations generated!")
```

---

# 🎧 6. What You Will Notice

Each variation will differ in:

* Melody
* Rhythm
* Richness
* Creativity

---

👉 Some will be:

* Better
* Worse
* Interesting

---

👉 That’s the goal!

---

# 🧪 7. Practical Experiments

---

## 🎵 Experiment 1 — Same Prompt

Prompt:

> “soft piano melody”

---

👉 Observe differences across 5 outputs

---

---

## 🧪 Experiment 2 — Change Prompt

Try:

> “sad piano melody with strings”

---

👉 Compare with previous results

---

---

## 🧪 Experiment 3 — Style Blending

Try:

> “piano melody with lofi beat and ambient pads”

---

👉 Observe richness

---

---

## 🧪 Experiment 4 — High Creativity Mode

```python
temperature = 1.0
top_k = 100
```

---

👉 Observe:

* More variation
* Sometimes messy

---

---

# 🧠 8. How to Choose the Best Output

---

## 🎯 Listen for:

* Clear melody 🎵
* Emotional feel ❤️
* Variation 🔄
* Smoothness 🎧

---

👉 Select best version manually

---

---

# 🛠️ 9. Optional Upgrade Ideas

---

## 🚀 Idea 1 — Save Parameters

Save settings with each file:

```python
print(f"Variation {i}: temp={temperature}, top_k={top_k}")
```

---

---

## 🚀 Idea 2 — Create Folder

Store all outputs neatly:

```python
import os
os.makedirs("outputs", exist_ok=True)
```

---

---

## 🚀 Idea 3 — Add User Input

Let user enter prompt:

```python
prompt = [input("Enter your music prompt: ")]
```

---

---

# 🎯 10. What You Learned

---

You now understand:

* How to generate multiple variations
* How randomness affects music
* How to experiment like a composer
* How to build a simple AI music tool

---

---

# 🧠 Final Understanding

👉 AI gives possibilities
👉 You select creativity

---

---

### One-Line Summary

> **Great music comes from exploring multiple variations — not from a single AI output.**

---


