## **Chapter 1.5 — First Music Generation**

---

### 🎯 What You Will Learn in This Chapter

* How to go from **text prompt → music output**
* How to **improve prompts step by step**
* How to **save generated audio files**

---

## 🎵 1. From Prompt → Music (Core Idea)

![Image](https://docs.lunarbase.ai/assets/images/ai_music_graph-04cd8b8efd9099633e510bc153bd3329.png)

### Simple Idea

This is the most exciting part:

👉 You **describe music in words**
👉 AI converts it into **actual sound**

---

### 💡 One-Line Understanding

> Prompt = **instruction** → AI = **music creator**

---

### 🧠 Real-Life Analogy

Think of giving instructions to a musician:

* You: “Play something sad on piano”
* Musician: plays music

👉 MusicGen works the same way

---

## ✍️ 2. Your First Prompt

Let’s generate your first music.

---

### 🪜 Basic Code (Colab or Local)

```python
from audiocraft.models import MusicGen
from IPython.display import Audio

model = MusicGen.get_pretrained('small')

model.set_generation_params(duration=8)

audio = model.generate(
    descriptions=["happy piano melody"]
)

Audio(audio[0].cpu(), rate=32000)
```

---

### 🎧 What Happens

* Input: `"happy piano melody"`
* Output: 🎵 Short music clip

---

## 🎯 3. Understanding Prompts (Very Important)

Your prompt controls everything.

---

### ❌ Weak Prompt

```id="nf6ytv"
music
```

👉 Result: Random, unclear output

---

### ✅ Better Prompt

```id="d2o0g7"
happy piano melody
```

👉 Result: Clearer mood + instrument

---

### ✅ Strong Prompt

```id="k51q6v"
slow emotional piano melody with soft background strings
```

👉 Result: Much richer and controlled music

---

### 🧠 Simple Rule

> More clear description = better music

---

## 🧩 4. Prompt Structure (Easy Formula)

You can think like this:

```id="g2k41c"
[Mood] + [Instrument] + [Style] + [Extra detail]
```

---

### 🎧 Examples

* “sad violin solo”
* “fast electronic dance music with heavy bass”
* “romantic bollywood style song with flute and tabla”

---

### 🧠 Real-Life Analogy

Like ordering food:

* “food” ❌
* “spicy chicken biryani” ✅

👉 More detail = better result

---

## 💾 5. Saving the Audio File

Playing is useful, but **saving is important**.

---

### 🪜 Code to Save Audio

```python
from audiocraft.data.audio import audio_write

audio_write("my_music", audio[0].cpu(), model.sample_rate)
```

---

### 🎧 Output File

```id="6h3mbr"
my_music.wav
```

👉 You can:

* Play it on your phone
* Upload it
* Edit it later

---

## 🔁 6. Full Example (Complete Flow)

```python
from audiocraft.models import MusicGen
from audiocraft.data.audio import audio_write
from IPython.display import Audio

# Load model
model = MusicGen.get_pretrained('small')

# Set duration
model.set_generation_params(duration=10)

# Generate music
audio = model.generate(
    descriptions=["calm meditation music with flute and soft background pads"]
)

# Play
Audio(audio[0].cpu(), rate=32000)

# Save
audio_write("meditation_music", audio[0].cpu(), model.sample_rate)
```

---

## ⚠️ Common Beginner Mistakes

❌ Writing too vague prompts
❌ Expecting lyrics (MusicGen is mostly instrumental)
❌ Using very long duration (slow generation)

---

## 💡 Pro Tips (Very Useful)

### 1. Start Simple

👉 “piano melody”

### 2. Add Details Slowly

👉 “slow sad piano melody”

### 3. Add Environment

👉 “slow sad piano melody with rain background”

---

## 🎯 Practice Exercise (Try This)

Generate 3 versions:

1. “happy flute music”
2. “sad flute music”
3. “fast flute dance music”

👉 Compare how mood changes output

---

## 🧠 Final Understanding

👉 Prompt = your **creative control tool**
👉 AI turns your words into **real sound**
👉 Saving lets you **build your own music library**

---

