###Grounded Q&A Assistant for Higher Education 🎓 (Salesforce + Heroku + LLM)
**The "Build and Buy" Strategy for edu**

This project is a proof-of-concept AI assistant that demonstrates a powerful "build and buy" strategy for the Salesforce ecosystem. It enables university staff to ask natural-language questions about student policies and receive accurate, grounded answers, showcasing that Salesforce is not a walled garden.

While customers can "buy" solutions like Data Cloud and Agentforce for standard use cases, our approach proves we can "build" a custom solution to solve specialized, high-value problems that require more architectural control.

This is critical when:

A declarative tool isn't enough: The problem requires custom logic or a different programming language to orchestrate the solution.

Data lives in a legacy system: Student policies are in a non-standard database or a popular pubsec document management system like PowerDMS, without a native Data Cloud connector.

Advanced data processing is needed: We can add extra steps to the process—like advanced data cleaning or a multi-step grounding—that the customer controls entirely.

Extreme security is a must: The LLM calls and associated data are kept completely separate from the core Salesforce org, addressing extreme data security requirements.

This project's architecture provides a powerful, flexible, and compliant way to solve these challenges.

**TLDR the assistant's job**:

Accepts questions via Salesforce UI

Sends the input and context to a Flask app hosted on Heroku

Grounds the prompt using relevant student data and reference docs

Calls a large language model (e.g. OpenAI GPT-4, Claude)

Returns the answer and stores it back in the Salesforce record

faster.

**Steps and status (hashtag upon completion)**

Phase 1: Local Setup & Validation (2 hours)
The goal is to set up your tools and confirm that a basic Python app can talk to an LLM.

Get Your Tools Ready: Install Python, get your LLM API key, and make sure you have a simple code editor like VS Code installed. Don't worry about Salesforce or Heroku yet.

Write a Simple Python Script: Create a Python file (test_llm.py) with just a few lines of code. This script will make a direct API call to your LLM and print the response to your terminal.

Create Your Grounding Data: Don't use a database. Create a simple text file (policies.txt) and paste a few paragraphs of fake student policy text into it. We'll use this later.

Validate the Connection: Run your Python script from the command line. If it prints a response from the LLM, you've successfully completed the most critical step.

Phase 2: Heroku & Flask API (4 hours)
Now we'll turn your local Python script into a simple web server that lives on Heroku.

Create a Flask App: Create a new Python file (app.py) that uses the Flask framework. This app will have one single API endpoint (a URL) that does three things:

It will read a simple question from the request.

It will read the content from your policies.txt file.

It will use the content from policies.txt to "ground" the LLM's response.

Deploy to Heroku: With just a few command-line commands, deploy this simple app to Heroku. You will get a public URL for your app, which is what Salesforce will call.

Validate the API: Use a browser or a tool like cURL to test your new public Heroku URL. If you can send it a question and it returns an answer from the LLM, you're good to go.

Phase 3: The Salesforce UI (4 hours)
This is where you build the "front end" that the user will interact with.

Create a New LWC: Use the Salesforce extensions in VS Code to create a new, simple Lightning Web Component.

Build the UI: The component's HTML will have just two elements: a text input field for the user's question, and a div to display the answer when it comes back.

Secure the Connection: In your Salesforce setup, create a Named Credential that points to your Heroku app's public URL. This is a secure, no-code way to connect Salesforce to your Heroku app.

Connect the LWC: Write a very basic JavaScript function in your LWC that, when a button is clicked, sends the question to your Named Credential and displays the returned answer in the designated div.

Phase 4: Final Touches & Demo Prep (2 hours)
This phase is for preparing your narrative and making the demo look polished.

Create a Sample Case: In your Salesforce org, create a new Case record. You'll add your new LWC to this record's page layout.

Get Your Diagram Ready: A simple diagram with boxes and arrows is all you need. You can draw this on a whiteboard or use a simple tool.

Practice Your Demo Script: Walk through the demo a few times, explaining each step: "Here's the problem... here's the solution... this is where our custom LWC lives... this is what happens when I click the button..."

This plan is focused on the absolute minimum needed to get a powerful, working prototype. It's a fantastic way to learn the fundamentals and have a compelling story ready to go in a very short amount of time.
