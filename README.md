# ZimFlow

A Chrome extension powered by Google Gemini Nano and Gemma 3, specifically built for educational purposes in offline environments.

- Leverages Chrome's native Gemini Nano AI to provide local translation and content summarization capabilities for web pages
- Connects to a locally deployed Gemma 3 through the extension, enabling multimodal AI assistance for tutoring, question answering, and homework support
- Operates entirely offline with all AI functionality running locally, making it ideal for students in regions with limited or no internet access

---

## Demo Video
https://youtu.be/LpxsPkc8Kys


---

## Key Features

### 1. AI-Powered Translation & Summarization (Chrome Built-in AI)

- **Offline Translation**: Employs Chrome's [Translation API with built-in AI](https://developer.chrome.com/docs/ai/translator-api) to translate content locally across multiple languages
- **Knowledge Summarization**: Utilizes Chrome's [Gemini Nano AI](https://developer.chrome.com/docs/ai/prompt-api) for local inference and structured content summaries

**How It Works:**

1. Click the ZimFlow extension icon to launch the sidepanel
2. Choose either "AI Translate" or "AI Summary" from the left-hand menu
3. Highlight the text you wish to process on any webpage
4. Right-click and select either "Translate" or "Summary" from the ZimFlow context menu
5. Your selected text is immediately sent to the ZimFlow sidepanel
6. Chrome's integrated Gemini Nano AI handles the translation or summarization locally, displaying results in real-time
7. Complete privacy protection with zero internet dependency, perfect for offline learning environments

### 2. AI Tutor with Multimodal Support (Gemma 3)

- **Multimodal Question Answering**: Interfaces with a locally running Gemma 3 AI model, accepting text queries, webpage screenshots, and image uploads for comprehensive multimodal understanding and responses—perfect for educational tutoring and homework assistance

**How It Works:**

1. Click the ZimFlow extension icon, launch the sidepanel, and select "AI Tutor"
2. Type your questions directly to interact with the local Gemma 3 for learning support and homework help
3. Upload various input types including webpage screenshots and images for Gemma 3 to analyze and respond to
4. Full offline operation with local AI processing ensures privacy while serving students without internet connectivity

## Installation & Setup

### Prerequisites

- Chrome Canary or Chrome Beta version 138 or higher with experimental AI features activated (see configuration steps below)

### Installation Steps

1. Chrome Canary or Chrome Beta 138+ is required, with experimental AI features enabled (see below).
2. Clone this repository and install dependencies:
   ```bash
   git clone https://github.com/HectorTa1989/zim-flow.git
   cd zim-flow
   pnpm install
   pnpm run dev
   ```
3. Load the `/build/chrome-mv3-dev` folder as an unpacked extension in the Chrome Extensions page.

### Chrome AI Feature Configuration

Navigate to `chrome://flags/` and enable the following flags:

- `#optimization-guide-on-device-model`
- `#prompt-api-for-gemini-nano`
- `#translation-api`

For detailed instructions, see: [Chrome AI Getting Started Guide](https://developer.chrome.com/docs/ai/get-started)

### Gemma 3 Local Deployment

Gemma 3 requires Ollama for local deployment. Ensure Ollama is installed and running on your machine.

- **Install Ollama:** [Download here](https://ollama.com/download)
- **Download Gemma 3 model:** [Get model](https://ollama.com/library/gemma3)
- **Launch Ollama:**
```bash
   export OLLAMA_ORIGINS=chrome-extension://*
   ollama serve
```

---

## Key Source Files
- [`src/components/GemmaAIViewer.tsx`](https://github.com/HectorTa1989/zim-flow/blob/main/src/components/GemmaAIViewer.tsx) (Gemma3-based multimodal Q&A)
- [`src/components/SummaryViewer.tsx`](https://github.com/HectorTa1989/zim-flow/blob/main/src/components/SummaryViewer.tsx) (Knowledge summarization using Chrome built-in Gemini Nano)
- [`src/components/TranslatorViewer.tsx`](https://github.com/HectorTa1989/zim-flow/blob/main/src/components/TranslatorViewer.tsx) (Offline translation using Chrome built-in Gemini Nano)
- [`src/background.ts`](https://github.com/HectorTa1989/zim-flow/blob/main/src/background.ts) (Handles context menu, message dispatch, etc.)
- [`src/content.ts`](https://github.com/HectorTa1989/zim-flow/blob/main/src/content.ts) (Handles webpage screenshot, communication with background, etc.)

---

## Important Notes

- All AI capabilities function completely offline without requiring an internet connection
- Ensure you're using Chrome Canary or Chrome Beta 138+ with the necessary experimental AI features enabled
