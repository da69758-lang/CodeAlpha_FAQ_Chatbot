<div align="center">

# 💡 MindSpark

### *Intelligent Desktop Chat Assistant — v1.0*

[![Java](https://img.shields.io/badge/Java-17%2B-f97316?style=for-the-badge&logo=java&logoColor=white)](https://www.java.com/)
[![JavaFX](https://img.shields.io/badge/JavaFX-21-8b5cf6?style=for-the-badge&logo=java&logoColor=white)](https://openjfx.io/)
[![Groq API](https://img.shields.io/badge/Groq-API-06b6d4?style=for-the-badge&logoColor=white)](https://console.groq.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)

<br/>

*A polished, multilingual AI chatbot desktop app powered by Groq & Llama 3 — built with JavaFX for students, educators, and professionals.*

<br/>

---

</div>

## 🌟 What is MindSpark?

**MindSpark** is a fully-featured desktop AI assistant that combines a built-in **FAQ engine** (powered by TF-IDF cosine similarity) with live **Groq LLM** responses. It instantly handles common university queries offline and seamlessly escalates complex questions to the AI — all wrapped in a sleek, native JavaFX interface with dark/light themes, voice input, multilingual support, and much more.

---

## ✨ Features

| # | Feature | Description |
|---|---------|-------------|
| 1 | 🎙 **Voice Input** | Speak your questions — transcribed in real time via Groq Whisper API |
| 2 | 🔊 **Text-to-Speech** | AI responses read aloud with per-message speak/stop controls |
| 3 | 🔍 **Chat Search** | Full-text search across all sessions with highlighted snippets |
| 4 | 📌 **Pin Messages** | Pin any message from any chat and view all pins in one panel |
| 5 | 💾 **Session Persistence** | All conversations saved to disk and restored on next launch |
| 6 | 🔔 **Notification Sound** | Synthesised ping tone when AI finishes — no audio file needed |
| 7 | 📊 **Word Count & Read Time** | Every message shows word count and estimated reading time |
| 8 | 📤 **Export Chats** | Save conversations as `.txt` or styled `.html` files |
| 9 | 🌐 **Multi-Language UI** | Full interface in English, Arabic (RTL), Urdu (RTL), and French |
| 10 | ⌨️ **Keyboard Shortcuts** | 20+ shortcuts with a built-in shortcut reference panel |

### Additional Highlights

- **Dual AI Engine** — Local FAQ matching for university queries + Groq LLM for everything else
- **4 AI Models** — Switch between `llama-3.3-70b-versatile`, `llama-3.1-8b-instant`, `mixtral-8x7b-32768`, and `gemma2-9b-it`
- **10 AI Personas** — General Assistant, Coding Expert, Science Teacher, Math Tutor, Creative Writer, Language Translator, Doctor Advisor, Legal Advisor, Career Coach, Fitness Trainer
- **Dark / Light Theme** — Toggle live from Settings
- **Markdown Rendering** — Responses rendered with full Markdown (code blocks, tables, bold, lists)
- **Animated Chat Bubbles** — Smooth fade-in and slide-up on every message
- **File Upload** — Attach `.txt`, `.md`, `.java`, `.py`, `.json`, or `.csv` as context
- **Regenerate Response** — Re-ask the last prompt with one click or `Ctrl+R`
- **Font Size Slider** — Adjustable from 11px to 20px
- **Splash Screen** — Branded animated loading screen on launch

---

## 🏗️ Project Structure

```
src/
└── main/
    └── java/
        └── com/faqchatbot/
            ├── Main.java                     # JavaFX entry point & window bootstrap
            ├── ChatController.java           # Central UI controller (input, send, history)
            ├── ChatBubble.java               # Message bubble component (pin, copy, TTS, stats)
            ├── ChatSession.java              # Session data model (messages, metadata, JSON I/O)
            ├── ChatSearchPanel.java          # Feature 3 — cross-session search modal
            ├── FAQData.java                  # Hardcoded FAQ dataset (university Q&A)
            ├── FAQEngine.java                # TF-IDF + cosine similarity search engine
            ├── GroqClient.java               # Groq REST API client (multi-model, multi-persona)
            ├── SessionManager.java           # Disk-based session load / save / delete
            ├── Sidebar.java                  # Session list sidebar with delete support
            ├── SettingsPanel.java            # Settings modal (API key, model, persona, theme)
            ├── PinManager.java               # Feature 4 — in-memory pin store with listeners
            ├── PinnedPanel.java              # Feature 4 — pinned messages modal
            ├── FileHandler.java              # TXT/HTML export + file upload reader
            ├── MarkdownRenderer.java         # Flexmark-based Markdown to HTML renderer
            ├── NotificationSoundManager.java # Feature 6 — PCM sine-wave ping generator
            ├── I18nManager.java              # Feature 9 — i18n string table (en/ar/ur/fr)
            ├── KeyboardShortcutsPanel.java   # Feature 10 — shortcuts reference modal
            ├── SpeechManager.java            # TTS engine wrapper (Windows PowerShell)
            └── VoiceInputManager.java        # Feature 1 — microphone capture & transcription
resources/
    ├── style.css                             # Full dark/light theme stylesheet
    └── assets/
        └── icon.png                          # App icon
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Java 17+ |
| UI Framework | JavaFX 21 |
| AI API | [Groq Cloud](https://console.groq.com/) |
| HTTP Client | Java `java.net.http.HttpClient` |
| JSON | org.json |
| Markdown | [Flexmark-Java](https://github.com/vsch/flexmark-java) |
| Audio | `javax.sound.sampled` (PCM synthesis, no external files) |
| Persistence | JSON files saved to `~/MindSpark/sessions/` |
| Build Tool | Maven |

---

## 🚀 Getting Started

### Prerequisites

- Java **17** or higher
- Maven **3.8+**
- A free [Groq API key](https://console.groq.com/)

### Clone & Build

```bash
git clone https://github.com/YOUR_USERNAME/MindSpark.git
cd MindSpark
mvn clean package
```

### Run

```bash
mvn javafx:run
```

Or run the packaged JAR:

```bash
java -jar target/mindspark-1.0.jar
```

### Set Your API Key

1. Launch the app
2. Click **⚙️ Settings** in the header or press `Ctrl+,`
3. Paste your Groq API key in the **API Configuration** field
4. Click **✓ Save & Close**

Your key is active for the current session. To persist it permanently, paste it directly in `GroqClient.java`:

```java
private static String API_KEY = "gsk_your_key_here";
```

> ⚠️ Never commit your API key to GitHub. Use the Settings panel instead.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Enter` | Send message |
| `Shift + Enter` | New line in input |
| `Ctrl + R` | Regenerate last response |
| `Ctrl + L` | Clear chat |
| `Ctrl + N` | New chat session |
| `Ctrl + F` | Search all chats |
| `Ctrl + P` | Open pinned messages |
| `Ctrl + ,` | Open settings |
| `Ctrl + ?` | Show keyboard shortcuts panel |
| `Ctrl + E` | Export chat |
| `Ctrl + M` | Start / stop mic recording |
| `Ctrl + S` | Toggle notification sound |
| `Ctrl + T` | Toggle text-to-speech |
| `Ctrl + 1–4` | Switch language (EN / AR / UR / FR) |
| `Escape` | Close any open dialog |

---

## 🌐 Multi-Language Support

Switch the entire UI language instantly from **Settings → Language** or via `Ctrl+1` through `Ctrl+4`.

| Code | Language | Direction |
|------|----------|-----------|
| `en` | English | LTR |
| `ar` | العربية (Arabic) | **RTL** |
| `ur` | اردو (Urdu) | **RTL** |
| `fr` | Français (French) | LTR |

RTL layouts are automatically applied to input fields, message bubbles, and result lists.

---

## 🧠 FAQ Engine

The built-in FAQ engine answers common **university-related questions** without any internet connection, covering topics like:

- Admission requirements and deadlines
- Tuition fees and scholarships
- Exam schedules and attendance rules
- Hostel, library, transport, and campus facilities
- Transcripts, GPA calculation, and results

It uses **TF-IDF vectorisation** with **cosine similarity** scoring. If the confidence score falls below the threshold (`0.1`), the query is automatically sent to the Groq LLM.

To add your own FAQs, edit `FAQData.java`:

```java
faqs.put("Your question here?", "Your answer here.");
```

---

## 📤 Export Formats

| Format | What you get |
|--------|-------------|
| **TXT** | Plain-text transcript with timestamps and a formatted header |
| **HTML** | Styled dark-theme page with coloured user/AI bubbles, ready to open in any browser |

---

## 🔧 Settings Reference

All runtime settings are in the **Settings panel** (`Ctrl+,`):

| Setting | Options |
|---------|---------|
| API Key | Groq key (`gsk_…`) |
| AI Model | llama-3.3-70b · llama-3.1-8b · mixtral-8x7b · gemma2-9b |
| AI Persona | 10 built-in roles |
| Theme | 🌙 Dark / ☀️ Light |
| Text-to-Speech | On / Off |
| Notification Sound | On / Off + live test button |
| Font Size | 11px – 20px slider |
| Language | EN / AR / UR / FR |

---

## 📋 Maven Dependencies

```xml
<dependencies>
    <!-- JavaFX -->
    <dependency>
        <groupId>org.openjfx</groupId>
        <artifactId>javafx-controls</artifactId>
        <version>21</version>
    </dependency>
    <dependency>
        <groupId>org.openjfx</groupId>
        <artifactId>javafx-web</artifactId>
        <version>21</version>
    </dependency>

    <!-- JSON -->
    <dependency>
        <groupId>org.json</groupId>
        <artifactId>json</artifactId>
        <version>20240303</version>
    </dependency>

    <!-- Markdown -->
    <dependency>
        <groupId>com.vladsch.flexmark</groupId>
        <artifactId>flexmark-all</artifactId>
        <version>0.64.8</version>
    </dependency>
</dependencies>
```

---

## 🤝 Contributing

Contributions are welcome! Here's how to get involved:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m "Add: your feature description"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

Please keep code style consistent with existing files and test your changes locally before submitting.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Ubaidullah Waheed**
📧 ubaidullahwaheed685@gmail.com
🔗 [GitHub](https://github.com/Danish Ali) · [LinkedIn](https://linkedin.com/in/Danish Ali)

---

## 🙏 Acknowledgements

- [Groq](https://groq.com/) — blazing-fast LLM inference API
- [Flexmark-Java](https://github.com/vsch/flexmark-java) — Markdown parsing and rendering
- [JavaFX](https://openjfx.io/) — modern Java UI toolkit
- University FAQ dataset compiled for academic use

---

<div align="center">

**⭐ If MindSpark helped you, please give it a star!**

Made with ☕ and Java

</div>
