# PDF Chatbot with RAG (Retrieval-Augmented Generation)

A powerful chatbot that allows you to upload PDF documents and ask questions about their content using AI. Built with Streamlit, LangChain, and Groq LLM.

![PDF Chatbot Demo](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=Streamlit&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

## Features

- 📄 Upload and process multiple PDF files
- 🤖 AI-powered question answering using Groq's LLM
- 🔍 Semantic search with FAISS vector database
- 💬 Interactive chat interface
- 📚 View source documents and page references
- ⚡ Fast response times with LLaMA 3.1 model

---

## Table of Contents

1. [Installation](#installation)
2. [Getting API Keys](#getting-api-keys)
3. [Configuration](#configuration)
4. [Running Locally](#running-locally)
5. [Deploying to Streamlit Cloud](#deploying-to-streamlit-cloud)
6. [Usage](#usage)
7. [Common Errors & FAQs](#common-errors--faqs)
8. [Project Structure](#project-structure)
9. [Technologies Used](#technologies-used)

---

## Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/Bhashita439/Document-Q-A-Assistant-using-RAG.git
cd Document-Q-A-Assistant-using-RAG
```

### Step 2: Create Virtual Environment (Recommended)

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**On macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Getting API Keys

### 🔑 Groq API Key (Required)

Groq provides fast LLM inference with their optimized infrastructure.

#### Steps to Get Groq API Key:

1. **Visit Groq Console**
   - Go to: [https://console.groq.com](https://console.groq.com)

2. **Sign Up / Login**
   - Click "Sign Up" if you're new
   - Use Google/GitHub for quick signup
   - Or create account with email

3. **Navigate to API Keys**
   - After login, go to the left sidebar
   - Click on "API Keys"

4. **Create New API Key**
   - Click "Create API Key" button
   - Give it a name (e.g., "PDF Chatbot")
   - Click "Submit"

5. **Copy Your API Key**
   - **IMPORTANT:** Copy the key immediately
   - You won't be able to see it again!
   - It looks like: `gsk_xxxxxxxxxxxxxxxxxxxxxxxxxxxx`

6. **Save It Securely**
   - Store it in a password manager
   - Never share it publicly
   - Don't commit it to GitHub

---

## Configuration

### Step 1: Create Environment File

We've provided a `sample.env` file. Follow these steps:

1. **Locate the `sample.env` file** in the project root

2. **Copy and rename it to `.env`:**

   **On Windows (Command Prompt):**
   ```cmd
   copy sample.env .env
   ```

   **On macOS/Linux (Terminal):**
   ```bash
   cp sample.env .env
   ```

   **Or manually:**
   - Right-click `sample.env`
   - Select "Copy"
   - Paste and rename to `.env`

### Step 2: Add Your API Key

Open the `.env` file in any text editor and replace the placeholder:

**Before:**
```bash
GROQ_API_KEY=your_groq_api_key_here
```

**After:**
```bash
GROQ_API_KEY=gsk_1a2b3c4d5e6f7g8h9i0j1k2l3m4n5o6p7q8r9s0t
```

⚠️ **Important:** 
- No spaces around the `=` sign
- No quotes needed
- Keep the `.env` file in the project root directory

### Step 3: Verify `.gitignore`

Make sure your `.env` file won't be committed to Git:

Check if `.gitignore` contains:
```
.env
venv/
__pycache__/
*.pyc
```

---

## Running Locally

### Step 1: Activate Virtual Environment

Make sure your virtual environment is activated (see Installation Step 2)

### Step 2: Run the Streamlit App

```bash
streamlit run main2.py
```

Or if you named your file differently:
```bash
streamlit run your_filename.py
```

### Step 3: Access the Application

The app will automatically open in your default browser at:
```
http://localhost:8501
```

If it doesn't open automatically, manually go to the URL shown in the terminal.

---

## Deploying to Streamlit Cloud

### Prerequisites
- GitHub account
- Your code pushed to a GitHub repository

### Step 1: Push Code to GitHub

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

⚠️ **Make sure `.env` is in `.gitignore`** - Never push API keys to GitHub!

### Step 2: Go to Streamlit Cloud

1. Visit: [https://streamlit.io/cloud](https://streamlit.io/cloud)
2. Click "Sign up" or "Sign in with GitHub"
3. Authorize Streamlit to access your GitHub

### Step 3: Deploy New App

1. Click **"New app"** button
2. Fill in the deployment settings:
   - **Repository:** Select your GitHub repo
   - **Branch:** `main` (or your default branch)
   - **Main file path:** `main2.py`

### Step 4: Add Secrets (API Keys)

This is crucial - you need to add your API key securely:

1. Click on **"Advanced settings"**
2. In the **"Secrets"** section, add:

```toml
GROQ_API_KEY = "gsk_your_actual_groq_api_key_here"
```

⚠️ **Important:** 
- Use TOML format (with quotes)
- Must match the variable name in your `.env` file

### Step 5: Deploy

1. Click **"Deploy!"**
2. Wait for the app to build (usually 2-5 minutes)
3. Your app will be live at: `https://your-app-name.streamlit.app`

### Step 6: Share Your App

Copy the URL and share it with anyone! They can use the app without needing API keys.

---

## Usage

### 1. Upload PDFs

- Click **"Browse files"** in the sidebar
- Select one or multiple PDF files
- Click **"Process Documents"**
- Wait for processing to complete

### 2. Ask Questions

- Type your question in the chat input at the bottom
- Press Enter or click Send
- The AI will answer based on your documents

### 3. View Sources

- Click **"View document sources"** below any answer
- See which pages and documents were used
- Verify the accuracy of responses

### Example Questions:

- "What is this document about?"
- "Summarize the main points"
- "What are the key findings in section 3?"
- "Who are the authors mentioned?"
- "What is the conclusion?"

---

## Common Errors & FAQs

### ❌ Error: "ModuleNotFoundError"

**Problem:** Missing dependencies

**Solution:**
```bash
pip install -r requirements.txt --upgrade
```

---

### ❌ Error: "GROQ_API_KEY not found"

**Problem:** API key not configured properly

**Solution:**
1. Check if `.env` file exists in the project root
2. Verify the key is spelled correctly: `GROQ_API_KEY`
3. No spaces around `=` sign
4. Restart the Streamlit app after adding the key

---

### ❌ Error: "Rate limit exceeded"

**Problem:** Too many requests to Groq API

**Solution:**
- Wait a few minutes before trying again
- Groq has generous free tier limits
- Check your usage at: https://console.groq.com

---

### ❌ Error: "Failed to process documents"

**Problem:** PDF processing issue

**Solution:**
1. Ensure PDFs are not password-protected
2. Check if PDFs contain actual text (not just images)
3. Try with a smaller PDF first
4. Check file size - very large PDFs may timeout

---

### ❓ FAQ: "Can I use other LLM models?"

**Answer:** Yes! Edit line 91 in `main2.py`:

```python
model_name="llama-3.1-8b-instant"  # Current model
```

Available Groq models:
- `llama-3.1-8b-instant` (fastest)
- `llama-3.1-70b-versatile` (more capable)
- `mixtral-8x7b-32768` (good balance)
- `gemma-7b-it` (Google's model)

---

### ❓ FAQ: "How much does this cost?"

**Answer:** 
- Groq offers a **generous free tier**
- No credit card required to start
- Check current limits at: https://console.groq.com/docs/rate-limits

---

### ❓ FAQ: "Can I process multiple PDFs at once?"

**Answer:** Yes! 
- Select multiple files when uploading
- They'll all be processed into one searchable database
- Ask questions across all documents

---

### ❓ FAQ: "My chat history disappeared!"

**Answer:** 
- Chat history is stored in session state
- It clears when you refresh the page
- Use the "Clear Chat History" button to reset intentionally

---

### ❓ FAQ: "Can I deploy this for free?"

**Answer:** Yes!
- Streamlit Cloud has a free tier
- Groq API has a free tier
- Perfect for personal projects and demos

---

### ❓ FAQ: "How do I update the app after changes?"

**Local:**
```bash
# Save your changes
# Restart Streamlit
streamlit run main2.py
```

**Streamlit Cloud:**
- Just push to GitHub
- Streamlit automatically redeploys
- No manual action needed!

---

### ❓ FAQ: "PDF contains images/tables - will it work?"

**Answer:**
- Text is extracted automatically
- Tables might not format perfectly
- Image-only PDFs won't work (text needed)
- For scanned PDFs, use OCR preprocessing

---

## Project Structure

```
Document-Q-A-Assistant-using-RAG/
│
├── main2.py                 # Main application file
├── requirements.txt         # Python dependencies
├── sample.env              # Sample environment file
├── .env                    # Your actual API keys (not in Git)
├── .gitignore             # Files to ignore in Git
├── README.md              # This file
│
└── .streamlit/            # Streamlit configuration (optional)
    └── config.toml        # Theme and settings
```

---

## Technologies Used

| Technology | Purpose |
|------------|---------|
| **Streamlit** | Web interface and deployment |
| **LangChain** | LLM orchestration framework |
| **Groq** | Fast LLM inference (LLaMA 3.1) |
| **FAISS** | Vector database for semantic search |
| **HuggingFace** | Sentence embeddings |
| **PyPDF** | PDF text extraction |

---

## Requirements.txt

```txt
streamlit
langchain>=0.1.0
langchain-groq
langchain-community
langchain-text-splitters
langchain-core
langchain-huggingface
faiss-cpu
pypdf
sentence-transformers
python-dotenv
```

---

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Support

If you encounter any issues:

1. Check the [Common Errors & FAQs](#common-errors--faqs) section
2. Open an issue on GitHub
3. Contact: bhashitanalluri1438@gmail.com

---

## Acknowledgments

- **Groq** for providing fast LLM inference
- **LangChain** for the excellent framework
- **Streamlit** for making deployment easy
- **HuggingFace** for embeddings models

---

## Star the Project ⭐

If you find this useful, please give it a star on GitHub!

---

**Made with ❤️ by [Bhashita Nalluri](https://github.com/Bhashita439)**
