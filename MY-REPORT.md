# **SYNTAX SULTANS - COT6930 Assignment 2**
### *A Discord-Based Chatbot for Enhancing Student Learning*

## **1. Overview**
This project explores advanced **prompt engineering techniques** to enhance the **requirement analysis** for a **Discord-based educational chatbot** using the `phi4` model. The chatbot aims to simplify **advanced concepts** for students through **interactive learning and toy examples**.

## **2. Research Objective**
Our research focuses on answering the question:

> **How can different prompting techniques improve the requirement analysis process for developing an effective Discord-based AI study companion using phi4?**

### **Key Areas of Investigation**
- Evaluating **prompting techniques** such as **Zero-Shot, Few-Shot, Chain of Thought (CoT), Prompt Chaining, Generate Knowledge, and Retrieval-Augmented Generation (RAG)**.
- Optimizing **chatbot capabilities** to improve **engagement, personalization, and knowledge retention**.
- Experimenting with **temperature, context length, and predictive tokens** to improve response quality.

## **3. Team Members**
- **Pavan Vamsi Namballa** (Z23752169)
- **Anuja Chandran Girija** (Z23797197)
- **Neethika Prodduturi** (Z23814182)

**Academic Supervisor:** Dr. Fernando Koch

---

## **4. Setup & Repository Structure**
### **Installation**
1. **Clone this repository**:
   ```bash
   git clone https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2.git
   cd COT6930-SyntaxSultans-Assignment-2
   ```
2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

### **Project Files**
- **`/prompt-eng/`** → Contains implementation files for different prompting techniques.
- **`zero_shot.ipynb`** → Initial experiment with **zero-shot prompting**.
- **`few_shot.ipynb`** → Implementation of **few-shot prompting** for structured chatbot responses.
- **`chain_of_thought.ipynb`** → Step-by-step **logical reasoning approach** for chatbot interactions.
- **`prompt_chaining.ipynb`** → Breaking down complex chatbot tasks into multiple sequential prompts.
- **`generate_knowledge.ipynb`** → Ensuring chatbot retrieves **background knowledge before responding**.
- **`rag.ipynb`** → **Retrieval-Augmented Generation** to improve factual accuracy.
- **`auto_reasoning.ipynb`** → Using **automatic reasoning** for structured chatbot development.

---

## **5. Prompt Engineering Techniques Used**
We explored **eight key prompt engineering methods** and their impact on chatbot requirement analysis:

### **1️⃣ Zero-Shot Prompting**
- Directly asks the model a question without examples.
- **Findings:** Quick but lacks structure and depth.

### **2️⃣ Few-Shot Prompting**
- Provides **2-3 examples** before asking the model to respond.
- **Findings:** Improves **coherence, completeness, and accuracy**.

### **3️⃣ Chain of Thought (CoT) Prompting**
- Encourages **step-by-step reasoning** instead of an immediate answer.
- **Findings:** Enhances explanations, especially for **math, logic, and science**.

### **4️⃣ Prompt Chaining**
- Uses **multiple sequential prompts** to refine chatbot responses.
- **Findings:** Helps **break down complex topics** into interactive steps.

### **5️⃣ Generate Knowledge Prompting**
- Asks the model to **first generate relevant knowledge** before answering.
- **Findings:** Produces **more structured and insightful responses**.

### **6️⃣ Retrieval-Augmented Generation (RAG)**
- Retrieves factual data before generating responses.
- **Findings:** Improves **fact-based accuracy** but lacks **interactive learning**.

### **7️⃣ Automatic Reasoning**
- Uses **deductive and inductive logic** for chatbot decision-making.
- **Findings:** Ensures **logical consistency in requirement analysis**.

### **8️⃣ Hyperparameter Tuning**
- Adjusting **temperature, context length, and prediction tokens**.
- **Findings:**  
  - **Temperature 1.0** → Best balance between **creativity and coherence**.  
  - **Temperature 0.5** → More structured, but **less engaging**.  
  - **Temperature 1.4** → More creative, but **less structured**.

---

## **6. Key Findings**
### ✅ **Best Approach for Educational Chatbot Development**
After experimenting with all techniques, the most effective **combination** for an educational chatbot was:

1️⃣ **Prompt Chaining** → **Breaks down complex topics** into step-by-step explanations.  
2️⃣ **Few-Shot Prompting** → Ensures **structured, high-quality responses**.  
3️⃣ **Generate Knowledge Prompting** → Enhances **depth and clarity of explanations**.  

This approach **maximized student engagement, adaptability, and learning retention**.

---

## **7. Running the Chatbot**
You can test the chatbot using the Discord bot integration:

1. **Set up API keys** in `.env`:
   ```
   DISCORD_TOKEN=your_discord_bot_token
   OPENAI_API_KEY=your_openai_api_key
   ```
2. **Run the chatbot**:
   ```bash
   python discord_chatbot.py
   ```
3. **Interact with the bot on Discord** using:
   ```
   !ask How does Newton’s Third Law work?
   ```

---

## **8. Future Work**
- Experimenting with **multi-modal AI (text + images)** for educational explanations.
- Implementing **interactive quizzes and gamification**.
- Enhancing **context retention** using memory-based models.

---

## **9. Conclusion**
This research demonstrates how **advanced prompt engineering techniques** optimize the development of AI-driven **educational chatbots**. By **combining structured prompting methods**, we improve **chatbot adaptability, reasoning, and student engagement**, making AI study companions more effective for **interactive learning**.

---

### **🔗 Connect with Us**
📩 **Contact:** [Your Email]  
📂 **GitHub Repo:** [https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2)  

