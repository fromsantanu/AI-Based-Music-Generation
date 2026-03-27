## **Chapter 1.4 — Installing & Running MusicGen**

---

### 🎯 What You Will Learn in This Chapter

* How to run **MusicGen on Google Colab (easy way)**
* How to install and run it on your **local computer (advanced way)**
* Generate your **first AI music output**

---

## 🚀 1. Two Ways to Use MusicGen

Before we start, understand this clearly:

| Method       | Difficulty | Best For             |
| ------------ | ---------- | -------------------- |
| Google Colab | ⭐ Easy     | Beginners            |
| Local Setup  | ⭐⭐⭐ Medium | More control, faster |

---

### 🧠 Simple Analogy

* **Colab** = Renting a ready kitchen (everything is set)
* **Local setup** = Building your own kitchen

---

## ☁️ 2. Method 1 — Google Colab (Recommended)

### ✅ Why Use Colab?

* No installation needed
* Free GPU (faster generation)
* Works in browser

---

### 🪜 Step-by-Step Setup

#### Step 1: Open Colab

Go to:
👉 [https://colab.research.google.com](https://colab.research.google.com)

---

#### Step 2: Create New Notebook

Click:

> **File → New Notebook**

---

#### Step 3: Enable GPU (Important)

Go to:

> Runtime → Change runtime type → Select **GPU**

---

#### Step 4: Install MusicGen

In a code cell, paste:

```python
!pip install audiocraft
```

---

#### Step 5: Load MusicGen Model

```python
from audiocraft.models import MusicGen
model = MusicGen.get_pretrained('small')
```

---

#### Step 6: Generate Music

```python
model.set_generation_params(duration=10)

audio = model.generate(
    descriptions=["happy indian classical flute music"]
)
```

---

#### Step 7: Play the Audio

```python
from IPython.display import Audio
Audio(audio[0].cpu(), rate=32000)
```

---

### 🎧 What You Just Did

👉 You gave a **text prompt**
👉 AI generated **music from it**

---

### 💡 Try These Prompts

* “sad piano melody”
* “bollywood romantic song”
* “fast electronic dance beat”

---

## 💻 3. Method 2 — Local Setup (Your Computer)

### ⚠️ Before You Start

You need:

* Python installed (3.9 or above)
* A decent computer (GPU recommended but optional)

---

### 🪜 Step-by-Step Setup

#### Step 1: Install Python Libraries

Open terminal / command prompt:

```bash
pip install audiocraft
```

---

#### Step 2: Create Python Script

Create a file:

```bash
musicgen_test.py
```

---

#### Step 3: Add Code

```python
from audiocraft.models import MusicGen
from audiocraft.data.audio import audio_write

model = MusicGen.get_pretrained('small')

model.set_generation_params(duration=10)

audio = model.generate(
    descriptions=["calm meditation music with flute"]
)

audio_write("output", audio[0].cpu(), model.sample_rate)
```

---

#### Step 4: Run the Script

```bash
python musicgen_test.py
```

---

### 🎧 Output

👉 A file will be created:

```
output.wav
```

👉 You can play it like any music file

---

## ⚖️ Colab vs Local (Simple View)

| Feature  | Colab      | Local                  |
| -------- | ---------- | ---------------------- |
| Setup    | Very easy  | Medium                 |
| Speed    | Good (GPU) | Depends on your system |
| Control  | Limited    | Full control           |
| Best for | Beginners  | Advanced users         |

---

## 🧠 Important Understanding

👉 MusicGen is a **text-to-music model**

You give:

```
"romantic guitar melody"
```

It creates:

```
Actual audio file
```

---

## 🎯 Common Beginner Mistakes

❌ Forgetting to enable GPU in Colab
❌ Using very long duration (slow generation)
❌ Giving vague prompts like “music”

---

## 💡 Pro Tip (Very Useful)

Start simple:

👉 First try:

* “happy piano”
* “sad violin”

Then slowly add details:

* “sad violin slow emotional background music”

---

## 🧠 Final Understanding

👉 You now have a **working AI music system**
👉 You can generate music using **just text**
👉 This is the foundation of everything ahead

---


