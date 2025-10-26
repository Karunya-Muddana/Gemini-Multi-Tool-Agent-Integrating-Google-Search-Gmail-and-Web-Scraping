# **Gemini Multi-Tool Agent: Demo (Google Search, Gmail & Web Scraping)**

## **Welcome to My First Agentic Project\!**

This is one of my first major projects, created as a way to learn and demonstrate how to connect Google's Gemini AI with other powerful APIs like Google Search and Gmail. I'm excited to share my learning process\! As this is a demo, please keep in mind the disclaimer below.

This project is a demonstration of a multi-tool AI agent built with the **Google Gemini API** (gemini-2.5-flash) and Python. This agent can hold a conversation, understand when to use external tools to gather live information, and perform actions like drafting emails based on its findings.

### **🔴 IMPORTANT: DEMONSTRATION ONLY 🔴**

This repository is intended for **testing and demonstration purposes only.** It is **NOT** meant for production use.

The API keys and credentials in the notebook (Google Search\_API \- Copy.ipynb) are **intentionally hardcoded** with placeholder values (e.g., "Your key here"). This is done for simplicity in this demo.

**DO NOT** commit or post your real, private API keys to GitHub or any public platform. If you do, they will be stolen by automated bots, compromising your accounts and potentially incurring costs.

## **Features**

* **Conversational AI:** Uses the Gemini API for natural and intelligent conversation.  
* **Function Calling:** Leverages Gemini's native function calling (tool use) to connect the model to real-world data and actions.  
* **Real-time Web Search:** Integrates the **Google Custom Search API** to find up-to-date information.  
* **Web Page Scraping:** Uses the trafilatura library to extract the clean, main content from any URL.  
* **Wikipedia Search:** Includes a wiki\_search tool for fetching encyclopedia summaries.  
* **Actionable Tasks:** Connects to the **Gmail API** using OAuth 2.0 to create draft emails on your behalf.

## **How It Works**

This agent is built around a central "main loop" that facilitates the interaction between the user, the Gemini model, and the Python tools.

1. A user provides a prompt (e.g., "What are the latest reviews for the RTX 5070?").  
2. The Gemini model receives the prompt and the list of available tools. Instead of answering directly, it recognizes that it needs external information and returns a **function call** request (e.g., Google Search(query="RTX 5070 reviews")).  
3. The Python script executes the requested function, gets the real-world data (a list of search results), and sends this data back to the model as a "tool response."  
4. The model receives the search results and uses this new context to generate a final, informed answer for the user.  
5. If the user follows up (e.g., "Draft an email to my friend about this"), the model can then call the create\_gmail\_draft\_with\_auth tool, using the information it just gathered.

## **Getting Started**

Follow these steps to get the agent running on your local machine.

### **1\. Clone the Repository**

git clone \[https://github.com/YourUsername/YourRepoName.git\](https://github.com/YourUsername/YourRepoName.git)  
cd YourRepoName

### **2\. Install Dependencies**

It's recommended to use a virtual environment.

python \-m venv venv  
source venv/bin/activate  \# On Windows, use \`venv\\Scripts\\activate\`

Install the required libraries:

pip install google-generativeai google-api-python-client google-auth-oauthlib google-auth-httplib2 wikipedia trafilatura requests jupyter

### **3\. Set Up Credentials (Local Only)**

To run this demo, you must add your own private credentials you can get them from google cloud.

A. Edit the Notebook:  
Open the Google Search\_API \- Copy.ipynb file. In the very first code cell, replace the placeholder strings with your actual API keys:  
\# Replace these placeholders with your real keys  
google\_gemini\_api\_key \= "AIzaSy...YOUR\_GEMINI\_KEY"  
google\_search\_api\_key \= "AIzaSy...YOUR\_SEARCH\_KEY"  
google\_search\_engine\_id \= "your\_search\_engine\_id"  
google\_gmail\_client\_id \= "your\_client\_id...apps.googleusercontent.com"

* **google\_gemini\_api\_key:** Get from [Google AI Studio](https://aistudio.google.com/app/apikey).  
* **Google Search\_api\_key & Google Search\_engine\_id:** Get from the [Google Programmable Search Engine](https://programmablesearchengine.google.com/controlpanel/all) and [Google Cloud Console](https://console.cloud.google.com/apis/credentials).  
* **google\_gmail\_client\_id**: This is part of your OAuth Client ID (see next step).

**B. Add Gmail client\_secrets.json:**

1. Go to the [Google Cloud Console Credentials page](https://console.cloud.google.com/apis/credentials).  
2. Click **Create Credentials** \-\> **OAuth client ID**.  
3. Select **Desktop app** as the Application type.  
4. After creation, **download the JSON file**.  
5. **Rename the downloaded file to client\_secrets.json** and place it in the same directory as your notebook.

### **4\. Run the Notebook**

Now you are ready to run the demo.

jupyter notebook "Google\_Search\_API \- Copy.ipynb"

The first time you try to create a Gmail draft, a browser window will open asking you to authenticate and grant permission to your Google Account.
