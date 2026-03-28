# 🎬 Chapter 3.7 — Mini Project

## 👉 Build: Prompt → Full Audio Pipeline

This chapter is where everything comes together.

> 🎯 You will build a **complete working system** that converts
> **Prompt → Lyrics → Music → Voice → Final Song**

---

## 🧠 Project Goal (Simple View)

You type:

```text
"Sad Hindi song about separation"
```

👉 System generates:

🎧 A **complete audio song**

---

## 🏗️ Full Pipeline Architecture

```text
Prompt
 ↓
Lyrics Generator
 ↓
Music Generator
 ↓
Voice Generator
 ↓
Mixing + Processing
 ↓
Final Audio File
```

---

## 🧩 Step-by-Step Implementation

We will build this in **simple stages**.

---

# 🔹 Step 1: Project Setup

---

### Install Required Libraries

```bash
pip install fastapi uvicorn pydub
```

---

### Folder Structure

```text
project/
 ├── main.py
 ├── modules/
 │    ├── lyrics.py
 │    ├── music.py
 │    ├── voice.py
 │    ├── mixer.py
 ├── output/
```

---

👉 Keep things clean and modular

---

# 🔹 Step 2: Lyrics Generator Module

---

### `modules/lyrics.py`

```python
def generate_lyrics(prompt):
    # Simulated (replace with LLM later)
    return """
    Verse:
    Dil mera toot gaya
    Sapna mera chhoot gaya

    Chorus:
    Kyun tu door chala gaya
    Dil mera ro pada
    """
```

---

👉 Later you can connect:

* ChatGPT API
* Claude API

---

# 🔹 Step 3: Music Generator Module

---

### `modules/music.py`

```python
from pydub import AudioSegment

def generate_music(prompt):
    # Placeholder: load sample music
    return AudioSegment.from_file("sample_music.wav")
```

---

👉 Replace later with:

* MusicGen
* Suno API

---

# 🔹 Step 4: Voice Generator Module

---

### `modules/voice.py`

```python
from pydub import AudioSegment

def generate_voice(lyrics):
    # Placeholder: load sample voice
    return AudioSegment.from_file("sample_voice.wav")
```

---

👉 Replace later with:

* TTS
* Singing models

---

# 🔹 Step 5: Mixing Module

---

### `modules/mixer.py`

```python
def mix_audio(music, voice):
    # Adjust volume
    voice = voice + 4
    music = music - 6

    # Combine
    final = music.overlay(voice)

    return final
```

---

# 🔹 Step 6: Main Pipeline

---

### `main.py`

```python
from fastapi import FastAPI
from modules.lyrics import generate_lyrics
from modules.music import generate_music
from modules.voice import generate_voice
from modules.mixer import mix_audio

app = FastAPI()

@app.post("/generate-song")
def generate_song(data: dict):

    prompt = data["prompt"]

    # Step 1: Lyrics
    lyrics = generate_lyrics(prompt)

    # Step 2: Music
    music = generate_music(prompt)

    # Step 3: Voice
    voice = generate_voice(lyrics)

    # Step 4: Mix
    final_audio = mix_audio(music, voice)

    # Save output
    output_path = "output/final_song.wav"
    final_audio.export(output_path, format="wav")

    return {
        "message": "Song generated",
        "file": output_path,
        "lyrics": lyrics
    }
```

---

# 🔹 Step 7: Run the System

---

```bash
uvicorn main:app --reload
```

---

👉 Open browser:

```
http://localhost:8000/docs
```

---

👉 Test API:

* Enter prompt
* Click execute
* Get result

---

# 🔹 Step 8: Connect UI (Optional)

---

If you already have UI:

```javascript
fetch("http://localhost:8000/generate-song", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ prompt: "sad Hindi song" })
})
.then(res => res.json())
.then(data => console.log(data))
```

---

👉 Now your system is interactive

---

# 🧪 Example Run

---

### Input

```text
"Romantic Hindi song, soft mood"
```

---

### Output

* Lyrics generated ✔
* Music loaded ✔
* Voice added ✔
* Mixed audio ✔

---

🎧 Final file:

```
output/final_song.wav
```

---

# ⚠️ Limitations (Current Version)

Right now:

* Using placeholder music ❌
* Using sample voice ❌

---

👉 But structure is correct ✅

---

# 🚀 How to Improve (Next Level)

---

## Upgrade 1: Real Lyrics

Replace:

```python
generate_lyrics()
```

👉 With:

* OpenAI / Claude API

---

## Upgrade 2: Real Music

Replace:

```python
generate_music()
```

👉 With:

* MusicGen

---

## Upgrade 3: Real Voice

Replace:

```python
generate_voice()
```

👉 With:

* Singing AI models

---

## Upgrade 4: Better Mixing

Add:

* Reverb
* Timing sync
* EQ

---

# 🧠 Key Learning from Project

---

### 1. Pipeline Thinking

You learned:

```text
Break → Build → Connect
```

---

### 2. Modular Design

Each part:

* Independent
* Replaceable

---

### 3. Real System Building

You now have:

* Backend
* Audio pipeline
* Expandable system

---

# 💡 Pro Insight

> This project is not about perfection
> It is about building a **working system you can improve**

---

# 🏁 Final Result

You have built:

🎧 **Your own AI Music Generator Pipeline**

---

# 📌 What You Can Do Next

---

### Option 1: Improve Quality

* Better lyrics
* Better voice

---

### Option 2: Add Features

* Genre selection
* Language selection
* Mood control

---

### Option 3: Build Product

* Web app
* Mobile app
* API service

---

# 🚀 Final Thought

> You started with generating random music…
> Now you can **build your own AI music studio system**

---

If you want next, I can help you:

✅ Convert this into a **full production-ready project**
✅ Add **real APIs (OpenAI + MusicGen)**
✅ Build a **clean UI (NiceGUI)**

Just tell me 👍

