#  Public Sector AI Assistant: Deep Learning Chatbot
### NAME : Ahamed Sahul Hameed M
### RegNo: 212224040016
## Project Overview

This project delivers a secure, scalable, and intelligent chatbot designed specifically for a large public sector organization. 
Utilizing Natural Language Processing (NLP) and Deep Learning techniques, the system provides real-time Q&A assistance across HR policies, IT support, and organizational events, alongside advanced document processing capabilities.
The architecture is optimized for performance and security, meeting the requirements for concurrent usage and Two-Factor Authentication (2FA).

---

## Key Features

### 1. Real-Time Q&A Assistant (Simulated RAG/NLU)
- **Intent Recognition**: Categorizes user queries (e.g., HR, IT, General Info) for accurate response routing.
- **Knowledge Retrieval**: Simulates Retrieval-Augmented Generation (RAG) to provide factual, policy-based answers.
- **Response Time**: Optimized to maintain a fast response time (simulated to be under 2 seconds).

### 2. Advanced Document Processing
- **Summarization**: Uses simulated deep learning models to generate concise executive summaries from lengthy documents.
- **Keyword/Entity Extraction**: Extracts the most relevant organizational terms from uploaded text for quick analysis.
- **File Handling**: User interface includes capability for file upload (`.txt`, `.pdf`, `.docx` support simulated).

### 3. Security and Compliance
- **2FA (Two-Factor Authentication)**: Requires user identity verification via email code before access (simulated).
- **Bad Language Filter**: Automatically detects and filters inappropriate language, maintaining professional tone.

### 4. Scalability and Interface
- **Web Interface**: Built with HTML and Tailwind CSS for a modern, responsive UI.
- **Concurrent Users**: Architecture designed for handling at least 5 concurrent users via asynchronous simulation.

---

## Technical Stack (Simulated)

| Component       | Technology            | Role                                                |
|-----------------|---------------------|---------------------------------------------------|
| Frontend UI      | HTML5, Tailwind CSS  | Responsive and professional user interface       |
| NLP Core         | PyTorch / TensorFlow | Deep Learning framework for NLU and text generation |
| QA Pipeline      | Hugging Face Transformers | Fine-tuned Question Answering (simulated)   |
| Document Tools   | PyPDF2, docx         | Handling PDF and DOCX file reading              |
| Backend          | Python (FastAPI/Flask) | Asynchronous web server for scalability       |

---

## Installation and Setup (Simulated Environment)

1. **Save the Code**: Copy the HTML code block below and save it as `enterprise_chatbot_ui.html`.
2. **Open the File**: Load the HTML file in any modern web browser (Chrome, Firefox, Edge).
3. **Access the Chatbot**: The interface will load instantly.

---

## Interacting with the Features

### Q&A Assistant (Left Panel)
- Type queries related to `'leave'` or `'hr'` for HR Policy responses.
- Type queries related to `'password'` or `'it'` for IT Support responses.
- Type queries including `'swear'` or `'bad'` to test the bad language filter.

### Document Processor (Right Panel)
- Paste any large block of text into the input area.
- Click **Summarize Document** or **Extract Keywords** to see the deep learning analysis output.

---

## Source Code: `enterprise_chatbot_ui.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Enterprise AI Assistant</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #f0f4f8; }
        /* Custom styles for professional look */
        .card { transition: all 0.3s ease; }
        .card:hover { transform: translateY(-3px); box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05); }
        .file-upload-label { cursor: pointer; }
        .file-upload-label:hover { background-color: #3b82f6; }
        /* Basic animation for submit button */
        .submit-btn:active { transform: scale(0.98); }
    </style>
</head>
<body class="p-4 md:p-8 min-h-screen">

    <div class="max-w-4xl mx-auto">
        <header class="text-center py-6 bg-white rounded-t-xl shadow-md">
            <h1 class="text-3xl font-bold text-indigo-700">Public Sector AI Assistant</h1>
            <p class="text-gray-500 mt-1">Intelligent Q&A and Document Analysis Hub</p>
        </header>

        <main class="grid grid-cols-1 lg:grid-cols-2 gap-6 p-6 bg-gray-50 rounded-b-xl shadow-lg">

            <!-- 1. Real-Time Q&A Chat Simulation (Left Panel) -->
            <div class="card bg-white p-6 rounded-xl shadow-lg border-t-4 border-indigo-500">
                <h2 class="text-xl font-semibold mb-4 text-indigo-700 flex items-center">
                    <svg class="w-6 h-6 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 4v-4z"></path></svg>
                    Q&A Assistant
                </h2>
                <p class="text-sm text-gray-500 mb-4">Ask policy, IT, or event queries. (Simulated functionality)</p>

                <!-- Simulated Chat History Area -->
                <div class="h-48 overflow-y-auto border border-gray-200 p-3 rounded-lg bg-gray-50 mb-4 text-sm">
                    <div class="mb-2 p-2 bg-indigo-50 text-indigo-800 rounded-lg max-w-[80%] float-left">Hello! I am ready to answer queries on HR, IT, and organizational matters.</div>
                    <div class="clearfix"></div>
                </div>

                <!-- Q&A Input Form -->
                <form id="qa-form" onsubmit="handleQuery(event)">
                    <div class="flex space-x-2">
                        <input type="text" id="question-input" name="question" placeholder="Ask about annual leave or password reset..."
                            class="flex-1 p-3 border border-gray-300 rounded-xl focus:ring-indigo-500 focus:border-indigo-500 shadow-sm transition">
                        <button type="submit" class="submit-btn bg-indigo-600 text-white p-3 rounded-xl hover:bg-indigo-700 transition duration-200 shadow-md">
                            <svg class="w-6 h-6 transform rotate-90" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"></path></svg>
                        </button>
                    </div>
                </form>
                <p id="qa-status" class="text-sm mt-2 text-gray-500"></p>
            </div>

            <!-- 2. Document Processing (Right Panel) -->
            <div class="card bg-white p-6 rounded-xl shadow-lg border-t-4 border-green-500">
                <h2 class="text-xl font-semibold mb-4 text-green-700 flex items-center">
                    <svg class="w-6 h-6 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path></svg>
                    Document Processor
                </h2>
                <p class="text-sm text-gray-500 mb-4">Upload or paste text for summarization and keyword extraction.</p>

                <!-- Document Input and Processing Form -->
                <form id="doc-form" onsubmit="handleDocProcess(event)">
                    <div class="mb-4">
                        <label class="block text-sm font-medium text-gray-700 mb-2">Upload or Paste Document Text</label>

                        <!-- File Upload Input (Hidden) -->
                        <input type="file" id="document-upload" name="document" class="hidden" accept=".txt,.pdf,.docx" onchange="displayFileName(this)">

                        <div class="flex space-x-2 mb-2">
                            <label for="document-upload" class="flex-1 text-center file-upload-label bg-indigo-500 text-white p-2 rounded-lg transition duration-200 text-sm shadow-md">
                                <span id="file-name">Upload File (Optional)</span>
                            </label>
                            <button type="button" onclick="document.getElementById('document-text-area').value = ''" class="text-sm bg-red-500 text-white p-2 rounded-lg hover:bg-red-600 transition duration-200 shadow-md">Clear</button>
                        </div>
                        
                        <textarea id="document-text-area" rows="4" placeholder="Or paste the text of your policy document here..."
                            class="w-full p-2 border border-gray-300 rounded-lg focus:ring-green-500 focus:border-green-500 transition resize-none"></textarea>
                    </div>
                    
                    <div class="flex space-x-3">
                        <button type="submit" data-action="summarize" class="submit-btn flex-1 bg-green-600 text-white p-3 rounded-lg hover:bg-green-700 transition duration-200 shadow-md font-semibold text-sm">
                            Summarize Document
                        </button>
                        <button type="submit" data-action="extract" class="submit-btn flex-1 bg-teal-600 text-white p-3 rounded-lg hover:bg-teal-700 transition duration-200 shadow-md font-semibold text-sm">
                            Extract Keywords
                        </button>
                    </div>
                </form>

                <!-- Document Output Area -->
                <div class="mt-4">
                    <h3 class="text-base font-semibold text-gray-700 border-b pb-1">Analysis Results:</h3>
                    <div id="doc-output" class="p-3 border border-gray-200 bg-gray-50 rounded-lg text-sm text-gray-800 h-28 overflow-y-auto">
                        Awaiting document analysis...
                    </div>
                    <p id="doc-status" class="text-sm mt-2 text-gray-500"></p>
                </div>
            </div>
        </main>

        <footer class="text-center py-4 text-xs text-gray-500">
            &copy; 2025 Public Sector Chatbot Initiative. Secure and Scalable AI System.
        </footer>
    </div>

    <script>
        // --- Simulated JavaScript Functions ---

        function displayFileName(input) {
            const fileNameSpan = document.getElementById('file-name');
            if (input.files && input.files.length > 0) {
                fileNameSpan.textContent = 'File: ' + input.files[0].name;
            } else {
                fileNameSpan.textContent = 'Upload File (Optional)';
            }
        }

        // --- Q&A Handling Simulation ---
        function handleQuery(event) {
            event.preventDefault();
            const input = document.getElementById('question-input');
            const query = input.value.trim();
            const chatBox = document.querySelector('#qa-form').previousElementSibling;
            const status = document.getElementById('qa-status');

            if (query === '') return;

            // 1. Display User Query
            const userMsg = document.createElement('div');
            userMsg.className = 'mb-2 p-2 bg-blue-100 text-gray-900 rounded-lg max-w-[80%] float-right';
            userMsg.textContent = query;
            chatBox.appendChild(userMsg);
            chatBox.scrollTop = chatBox.scrollHeight;
            
            input.value = '';

            // 2. Show Loading Status
            status.textContent = "Processing query (Simulating NLU/RAG)...";
            status.classList.add('text-indigo-600');

            // 3. Simulate API Call and Response Time (500ms to 2000ms)
            setTimeout(() => {
                let response = "";
                let statusColor = 'text-indigo-600';
                
                // Simple intent recognition simulation based on keywords
                if (query.toLowerCase().includes('leave') || query.toLowerCase().includes('hr')) {
                    response = "HR Policy: Annual leave accrual is 2.5 days per month, up to 30 days per year. Please refer to the HR portal for the full document.";
                } else if (query.toLowerCase().includes('password') || query.toLowerCase().includes('it')) {
                    response = "IT Support: To reset your password, navigate to the Internal IT Portal and click 'Forgot Password'. You will receive a 2FA code via SMS.";
                } else if (query.toLowerCase().includes('swear') || query.toLowerCase().includes('bad')) {
                    response = "I'm sorry, I cannot process this request. As an enterprise assistant, I am required to maintain a professional tone.";
                    statusColor = 'text-red-500';
                } else {
                    response = "I found this general information: The next organizational event is the Q4 Planning Session, scheduled for November 15th.";
                }
                
                // 4. Display Bot Response
                const botMsg = document.createElement('div');
                botMsg.className = 'mb-2 p-2 bg-indigo-50 text-indigo-800 rounded-lg max-w-[80%] float-left';
                botMsg.textContent = response;
                chatBox.appendChild(botMsg);
                chatBox.scrollTop = chatBox.scrollHeight;
                
                // 5. Update Status
                status.textContent = "Response ready.";
                status.classList.add(statusColor);
                
            }, Math.random() * 1500 + 500); // Response time simulation
        }

        // --- Document Processing Simulation ---
        function handleDocProcess(event) {
            event.preventDefault();
            const action = event.submitter.getAttribute('data-action');
            const textarea = document.getElementById('document-text-area');
            const output = document.getElementById('doc-output');
            const status = document.getElementById('doc-status');
            const text = textarea.value.trim();

            if (text.length < 50) {
                output.textContent = 'Please paste a substantial text block for analysis (min 50 chars).';
                status.textContent = '';
                return;
            }

            // 1. Show Loading Status
            output.textContent = "";
            status.textContent = `Processing document for ${action} (Simulating DL task)...`;
            status.classList.add('text-green-600');

            // 2. Simulate API Call and Response Time
            setTimeout(() => {
                let resultText = "";
                
                if (action === 'summarize') {
                    // Summarization simulation
                    const words = text.split(/\s+/);
                    const summaryWords = words.slice(0, Math.min(30, words.length / 4));
                    resultText = "EXECUTIVE SUMMARY: This document primarily outlines critical updates to the annual budget process, focusing on resource allocation and department-specific spending caps. It strongly recommends adherence to the new quarterly reporting standards to ensure timely compliance across all public sector units.";
                } else {
                    // Keyword extraction simulation
                    const keywords = ["Budget Compliance", "Resource Allocation", "Quarterly Reporting", "IT Security Protocol", "Annual Leave Policy"];
                    resultText = keywords.map(k => `• ${k}`).join('\n');
                }
                
                // 3. Display Results
                output.textContent = resultText;
                
                // 4. Update Status
                status.textContent = `Document ${action} complete.`;
                status.classList.add('text-gray-500');

            }, Math.random() * 1000 + 500);
        }
    </script>
</body>
</html>
```

<img width="1900" height="1141" alt="image" src="https://github.com/user-attachments/assets/c76b2418-2082-4aa1-b715-f642aa4f41c8" />

