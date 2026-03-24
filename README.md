# Quiz Forge - AI-Powered MCQ Generator

TTransform your study materials into interactive quizzes. AI-powered MCQ generation from documents with multi-format export.

## 📋 Overview

Quiz Forge is an intelligent quiz generation tool that automatically creates multiple-choice questions (MCQs) from your documents. Simply upload a PDF, DOCX, or TXT file, specify the number of questions, and let AI generate well-structured quiz questions with options and correct answers.

## ✨ Features

- **Multi-Format Support**: Upload PDF, DOCX, or TXT files
- **AI-Powered Generation**: Uses Google Gemini 2.5 Flash for intelligent question creation
- **Customizable Output**: Generate any number of MCQs from your document
- **Multiple Export Formats**: Download results as TXT or PDF
- **User-Friendly Interface**: Simple web-based UI for easy access
- **Fast Processing**: Efficient text extraction and question generation

## 🚀 Technology Stack

- **Backend**: Flask (Python web framework)
- **AI/LLM**: Google Gemini API with LangChain
- **Document Processing**:
  - pdfplumber (PDF extraction)
  - python-docx (DOCX extraction)
- **PDF Generation**: fpdf2
- **Server**: Gunicorn (production)
- **Frontend**: HTML/CSS/JavaScript

## 📦 Installation

### Prerequisites

- Python 3.8+
- Google API Key (for Gemini API)
- pip (Python package manager)

### Local Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/quiz-forge.git
   cd quiz-forge
   ```

2. **Create a virtual environment**

   ```bash
   python -m venv venv

   # On Windows
   venv\Scripts\activate

   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**

   Create a `.env` file in the project root:

   ```env
   GOOGLE_API_KEY=your_google_api_key_here
   ```

5. **Run the application**

   ```bash
   python app.py
   ```

   The app will be available at `http://localhost:5000`

## 💻 Usage

1. **Open the Application**: Navigate to `http://localhost:5000` in your browser

2. **Upload a Document**:
   - Click the upload box
   - Select a PDF, DOCX, or TXT file
   - Specify the number of MCQs you want to generate

3. **Generate MCQs**:
   - Click "Generate Questions"
   - Wait for AI to process and create questions

4. **Download Results**:
   - View generated MCQs on the results page
   - Download as TXT or PDF format

## 📁 Project Structure

```
quiz-forge/
├── app.py                 # Main Flask application
├── requirements.txt       # Project dependencies
├── .env                   # Environment variables (create this)
├── README.md             # This file
├── Templates/
│   ├── index.html        # Home page & upload form
│   └── results.html      # Results display page
├── uploads/              # Temporary upload storage
├── results/              # Generated MCQs storage
└── .gitignore           # Git ignore rules
```

## 🔐 Environment Variables

```env
GOOGLE_API_KEY=your_google_gemini_api_key
PORT=5000               # Optional: server port (default: 5000)
FLASK_ENV=development   # Optional: flask environment
```

**Getting a Google API Key:**

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project
3. Enable the Generative AI API
4. Create an API key
5. Add it to your `.env` file

## 🚢 Deployment

### Quick Deploy on Render.com

1. Push your code to GitHub
2. Connect your repository to [Render.com](https://render.com)
3. Set environment variables in Render dashboard:
   - `GOOGLE_API_KEY`: Your Google API key
4. Deploy with automatic updates

### Deploy on Railway.app

1. Connect your GitHub repo to [Railway.app](https://railway.app)
2. Add environment variables
3. Auto-deploys on every push

### Deploy with Docker

Create a `Dockerfile`:

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:8000"]
```

Build and run:

```bash
docker build -t quiz-forge .
docker run -p 8000:8000 -e GOOGLE_API_KEY=your_key quiz-forge
```

### Deploy on Heroku

1. Create `Procfile`:

   ```
   web: gunicorn app:app
   ```

2. Deploy:
   ```bash
   heroku login
   heroku create
   heroku config:set GOOGLE_API_KEY=your_key
   git push heroku main
   ```

## 📝 Example MCQ Output

```
## MCQ
Question: What is machine learning?
A) A branch of artificial intelligence
B) A programming language
C) A database management system
D) A network protocol

Correct Answer: A
```

## 🔄 API Endpoints

| Endpoint               | Method | Description                      |
| ---------------------- | ------ | -------------------------------- |
| `/`                    | GET    | Home page with upload form       |
| `/generate`            | POST   | Generate MCQs from uploaded file |
| `/download/<filename>` | GET    | Download generated results       |

## 🐛 Troubleshooting

**Issue**: "No module named 'pdfplumber'"

- Solution: Run `pip install -r requirements.txt`

**Issue**: "Invalid API key"

- Solution: Check your `.env` file and ensure `GOOGLE_API_KEY` is correct

**Issue**: "File format not supported"

- Solution: Ensure file is PDF, DOCX, or TXT format

**Issue**: "Port already in use"

- Solution: Change port in app.py or use `PORT=8000 python app.py`

## 📋 Requirements

See [requirements.txt](requirements.txt) for all dependencies:

- Flask 3.0.0+
- LangChain & LangChain-Google-GenAI
- pdfplumber
- python-docx
- fpdf2
- python-dotenv
- gunicorn (production)

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 💡 Future Enhancements

- [ ] User accounts & saved quizzes
- [ ] Multiple language support
- [ ] Difficulty level selection
- [ ] Quiz analytics & statistics
- [ ] Batch file processing
- [ ] Custom branding for PDFs
- [ ] Integration with LMS platforms

## 📧 Support

For issues, questions, or suggestions:

- Open an issue on GitHub
- Contact: [your-email@example.com]

## 🎓 Use Cases

- **Educators**: Create quizzes from course materials
- **Students**: Generate practice questions from study materials
- **Content Creators**: Quickly produce assessment materials
- **Training Programs**: Automate quiz creation for training modules

---
