## **Level 1 Capstone Project: Prompt-Based Music Generator**

---

### **1. Project Overview**

In this project, you will build a **simple AI-powered music generator** where a user gives a text prompt, and the system generates music based on that prompt.

Think of it like this:

👉 You type:
“Calm flute music, morning, peaceful village”

👉 The system responds:
🎵 A short piece of music matching that mood

This is similar to how we describe a scene to a musician—and they play something accordingly. Here, the **AI model becomes your musician**.

---

### **2. Learning Objectives**

By completing this project, you will understand:

* How text prompts control music generation
* How to use a pretrained model like MusicGen
* How to convert user input into meaningful outputs
* How to evaluate whether the generated music matches intent

---

### **3. Real-Life Analogy**

Imagine you are giving instructions to a street musician:

* “Play something happy” → vague result
* “Play a soft flute melody like early morning in a village” → better result

👉 The clearer your instruction, the better the output.

This is exactly how **prompt-based music generation works**.

---

### **4. System Architecture (Simple View)**

```
User Input (Text Prompt)
        ↓
Prompt Processing
        ↓
MusicGen Model
        ↓
Audio Output (WAV/MP3)
        ↓
Playback / Save
```

---

### **5. Core Features**

Your project should include:

#### **5.1 Text Input Interface**

* User enters a prompt
* Example:

  * “Sad piano music”
  * “Fast tabla rhythm with energy”

#### **5.2 Music Generation Engine**

* Uses a pretrained model (e.g., MusicGen)
* Converts text → audio

#### **5.3 Output Handling**

* Play the generated audio
* Save it as a file

#### **5.4 Variation Generator (Optional but Recommended)**

* Generate multiple versions for the same prompt

👉 Like asking 3 musicians to play the same idea differently

---

### **6. Step-by-Step Implementation**

---

#### **Step 1: Install Dependencies**

```bash
pip install audiocraft
```

---

#### **Step 2: Load the Model**

```python
from audiocraft.models import MusicGen

model = MusicGen.get_pretrained('small')
model.set_generation_params(duration=10)
```

👉 Here:

* `small` = lightweight model
* `duration=10` = 10 seconds music

---

#### **Step 3: Take User Input**

```python
prompt = input("Enter your music idea: ")
```

---

#### **Step 4: Generate Music**

```python
audio = model.generate([prompt])
```

---

#### **Step 5: Save Output**

```python
from audiocraft.data.audio import audio_write

audio_write("output", audio[0].cpu(), model.sample_rate)
```

👉 This creates a file like:
`output.wav`

---

### **7. Example Prompts and Outputs**

| Prompt              | Expected Output        |
| ------------------- | ---------------------- |
| Calm flute morning  | Soft, slow melody      |
| Fast tabla rhythm   | Percussion-heavy music |
| Emotional violin    | Deep, expressive tones |
| Festival dhol beats | Energetic, loud rhythm |

---

### **8. Improving the System (Important Insight)**

Sometimes outputs feel:

* Random
* Repetitive
* Not matching mood

👉 Why?

Because prompts are too vague.

---

#### **Bad Prompt**

“Nice music”

#### **Better Prompt**

“Soft romantic piano with slow tempo, emotional mood”

---

### **9. Add Variations (Mini Upgrade)**

```python
outputs = model.generate([prompt] * 3)
```

👉 This gives 3 different versions of the same idea

Like:

* Same story
* Told in different styles

---

### **10. Evaluation Criteria**

Your project should be judged based on:

#### **10.1 Prompt Understanding**

* Does music reflect the input?

#### **10.2 Audio Quality**

* Is it clear or noisy?

#### **10.3 Variation Diversity**

* Are outputs different from each other?

#### **10.4 Usability**

* Is it easy to use?

---

### **11. Limitations (Be Honest About Them)**

This Level 1 system:

* ❌ Cannot generate vocals
* ❌ Has weak song structure (no verse/chorus)
* ❌ Sometimes repeats patterns

👉 Think of it as:
**“AI that can play sounds, but not compose full songs yet”**

---

### **12. Final Deliverable**

Your final project should include:

* A working script or app
* Ability to input prompts
* Generated audio output
* At least 5–10 example prompts tested

---

### **13. Suggested Extensions (Optional)**

If you want to go further:

* Add a simple UI (NiceGUI or Streamlit)
* Add dropdowns:

  * Mood (happy, sad, calm)
  * Instrument (piano, flute, tabla)
* Save multiple outputs automatically

---

### **14. Final Insight**

This project is your **first step into AI music creation**.

You are not just generating sound—you are learning:

👉 How machines interpret human creativity
👉 How ideas become audio

Think of this as:

**“Talking to a musician who only understands structured instructions”**

---

