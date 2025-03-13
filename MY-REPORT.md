## Assignment-2
## COT6930 PROMPT ENGINEERING
## SYNTAXSULTANS: 
A DISCORD BASED CHATBOT THAT WORKS AS A STUDY COMPANION THAT HELPS STUDENTS UNDERSTAND ADVANCED CONCEPTS IN A MUCH SIMPLER WAY.
## 1-Liner Description:
This research explores advanced prompting techniques to enhance requirement analysis for a Discord-based educational chatbot using the phi4 model. The goal is to evaluate different prompting strategies and optimize chatbot capabilities for student learning.

## Authors:
Pavan Vamsi Namballa (Z23752169)
Anuja Chandran Girija (Z23797197)
Neethika Prodduturi (Z23814182)

## Academic Supervisor:		
Dr. Fernando Koch

## Research Question:
How can different prompting techniques improve the requirement analysis process for developing an effective Discord-based AI study companion using phi4 ?


## What is already known about this topic?
Large Language Models (LLMs) like Llama 3.2 or phi4 can generate structured requirement analysis reports.
Prompt engineering techniques (zero-shot, few-shot, chain-of-thought, etc.) influence the accuracy and depth of chatbot design insights.
AI-driven study companions have shown positive impacts in education by simplifying complex topics.

## Our Team’s Work:
## Setup:	
We have opened the Visual Studio Code and Opened the folder
D:\Study at FAU\Semester 3\Gen AI\Assignment-2\prompt-eng.

This is where the repository has been cloned into.
Opened the command prompt terminal and typed the following command:
 

git clone https://github.com/username/repository.git

Our repository has been successfully copied here. 

We then opened the file prompt-eng/_pipeline.py to understand its structure.

It is in this file where the functions required for the project are defined here.

[1] 	load_config()
[2] 	create_payload()
[3] 	model_req()

The most important __main__() function imported functions 2 and 3 and an object of create_payload() has been created where several parameters are defined.

Let us try to understand each of the parameters.

•	Initial values of target and model were "ollama" and "llama3.2:latest" respectively. But this involves downloading the model on my personal computer which demands more space. Hence changed them to “open-webui” and “phi4-latest” which connects to the remote server.
•	The temperature parameter controls the randomness of the model's responses. The smaller the value, the more the responses will be predictable; the larger, the more diverse and creative. The model is at equilibrium between coherence and diversity when it is set to 1.0. A high value will yield uncoherent responses, and a low value will make them redundant.
•	The num_ctx parameter determines the number of tokens the model retains as context. A higher value helps in longer interaction coherence but at the expense of higher computational burdens. Initially set to an impossible 5,555,555, it was later dropped to 500 before being settled at 2048. This introduces effective handling while still maintaining enough context to offer meaningful response.
•	The num_predict parameter dictates the amount of tokens produced by the model. It was initially set to 1 and incrementally increased to 10. This adjustment is an effort to counteract response size insufficiency. A lower value produces short responses, whereas a higher value allows elaboration. Maintaining it at 10 ensures substantial responses without sparsity.

Let us examine each prompt engineering technique in the Github repository.

## 1.	Zero Shot Technique

Let us first examine the code snippet from the initial file ‘zero_shot.ipynb’:

MESSAGE = "What is 984 * log(2)"
PROMPT = MESSAGE

                         temperature=1.0, 
                         num_ctx=100, 
                         num_predict=100
 

As we can see, we have a message called “What is 984*log(2)” which is given as a prompt to the model. Zero-Shot Prompting is a method in which an AI model is presented with a task for the first time with no examples or instructions. The model draws on only its pre-trained knowledge to produce an answer. It is helpful for rapid answers but potentially not accurate for more complicated tasks.

Time Taken for the Response: 7.215 Seconds.

We would like to alter the above code snippet for generating the requirement analysis for our project “Discord-based educational chatbot that helps students understand harder concepts in an easier way”. A new file has been created with the name ‘zero_shot_copy-1.ipynb’.

MESSAGE = "Generate a requirement analysis for an educational chatbot that simplifies advanced topics for students using toy examples."
temperature=0.7, 
num_ctx=200, # We want the model to remember large messages if possible
# hence a large number is given
num_predict=2000  # The value was initially 100, because the question was simple
#However, the generation of a requirement analysis needs a large text as the output.
#Hence, the value is now 200.

Output:

[Output](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/zero-shot-copy-1-req-analysis-response.txt)
 
Time Taken for the Response: 26.456s

Improvization(‘zero_shot_copy-1-improved.ipynb’):

In the previous prompt, the question was generic. No proper context was provided. Improvization is done in such a way that the discord-based chatbot is ready and only thing needed is an enhancement. Since the message is big, the model needs to remember more tokens for retaining the context. Hence, the value of num_ctx is set to 2048. The response should be bigger. So the value for num_predict is set to 1200.

MESSAGE = ("Perform a requirement analysis to enhance an existing Discord chatbot built using the Owlmind framework "
    "into an educational chatbot. The chatbot should simplify advanced topics for students using toy examples. "
    "Focus on educational improvements and provide:\n"
    "1. Additional educational features required.\n"
    "2. Learning methodologies the chatbot should adopt.\n"
    "3. Ways to personalize learning for different student levels.\n"
    "4. AI model improvements to enhance explanations and engagement.\n"
    "5. Example interactions demonstrating improved learning experience.\n"
    "Format the response with clear sections and bullet points for readability.")
temperature=0.7, 
num_ctx=2048, 
num_predict=1200

 [Zero Shot Copy 1 Improved](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/zero-shot-copy-1-improved-req-analysis-response.txt)

Time Taken for the Response: 25.643s

Comparison of responses in Zero-shot technique:

Both responses are consistent logically, making the requirement analysis coherent and reasoned. They vary, however, in that Response 2 goes a step further by focusing more on interaction, engagement, and AI-driven personalization, hence the better response overall. If the goal is to achieve maximum student engagement, retention, and adaptability, Response 2 is the better option.

The first response is more technical and formal, hence an excellent choice for developers or project managers who need a step-by-step explanation of building the chatbot. It has integration information of the platform, security, compliance requirements, and a development timeline—all relevant for planning and project execution. It follows a strict requirement analysis format, hence excellent for a technical proposal but less readable for learning purposes.

The second response is more student-focused and education-driven, thus superior to understanding how the chatbot actually enhances learning. It illustrates advanced educational methods, including active recall, scaffolded learning, peer-to-peer collaboration, and adaptive content delivery—which are critical for a high-quality learning process. The sample interactions are also more interactive, showing how the chatbot would engage students in different learning contexts. It also provides internal analyses that focus on usability, richness of content, and engagement measures—critical factors to ensure the success of a chatbot in real-world educational settings.
The second response is better because it takes a more student-centered, engaging, and dynamic approach to chatbot development. Instead of just listing technical requirements, it talks about how the chatbot is going to enhance learning, such as personal learning paths, adaptive difficulty levels, and AI-driven engagement measures. It also includes realistic chatbot interactions, which show the application of the chatbot in the real world rather than simply outlining theoretical requirements.

While the first response excels at technical planning, the second response excels at discussing how the chatbot will improve education, making it the superior response if the concern of the audience is usability, engagement, and personalized learning.

## 2.	Self-Consistency Technique

The self-consistency approach is an AI technique in which a series of various responses are created to a single question and the most common or logically consistent response is selected. This is achieved for enhancing accuracy by eliminating wrong or random responses, hence being best suited for reasoning-type tasks such as mathematics, logic, and decision-making. By eliminating inconsistent answers, it minimizes hallucinations and gives more accurate outputs. This technique is essential in applications where precision and consistency are critical, as it reinforces the most correct and coherent answer.

The code snippet in the repository consists of the Zero-shot technique where no contextual information is specified. Enhancements are added to the code.

Unlike the first technique, multiple files are not created. The same ipynb file ‘self_consistency.ipynb’ has multiple cells created for several improvements and experimentations.

MESSAGE = ("Perform a requirement analysis to enhance an existing Discord chatbot built using the Owlmind framework "
    "into an educational chatbot. The chatbot should simplify advanced topics for students using toy examples. "
    "Focus on educational improvements and provide:\n"
    "1. Additional educational features required.\n"
    "2. Learning methodologies the chatbot should adopt.\n"
    "3. Ways to personalize learning for different student levels.\n"
    "4. AI model improvements to enhance explanations and engagement.\n"
    "5. Example interactions demonstrating improved learning experience.\n"
    "Format the response with clear sections and bullet points for readability.")

ADDITIONAL=("Generate ten internal analyses and provide the most consistent, well-reasoned requirement analysis."
            "Format the response with clear sections and bullet points for readability.")

#### (2) Adjust the Prompt Engineering Technique to be applied, simulating Workflow Templates

## @TODO 
PROMPT = MESSAGE + ADDITIONAL

temperature=1.0, 
                         num_ctx=100, 
                         num_predict=100

[Self Consistency 1 Output](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/self-consistency-improvement-1-requirement-analysis.txt)
 

Time Taken for the Response: 18.843s

Further Improvements:

By default, the temperature was set to 1.0. I tried to experiment with changing the temperature to 0.5.

[Self Consistency 2 Output](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/self-consistency-improvement-2-requirement-analysis.txt) 

Time Taken for the Response: 20.833s

Comparison of two responses in self-consistency technique:

Both responses adequately address the requirements laid out in the prompt, producing a sound requirement analysis for transforming a Discord chatbot into a learning tool. The answers follow a similar path by breaking down the analysis into categories like additional learning features, learning methodologies, personalization, AI model revision, and example interactions. The answers both ensure logical consistency and present concrete examples of chatbot interactions to demonstrate learning gains.

But more careful examination, Response 2 is the superior and more substantive one. Whereas Response 1 focuses on content delivery and sequenced learning methods such as scaffolding, gamification, and constructivist practices, Response 2 supplements with a broader list of learning practices, such as the Socratic Method, Experiential Learning, Problem-Based Learning, and Spaced Repetition. These approaches engage students' interest and thinking more critically than Response 1's approaches. 	

Personalization is another area in which Response 2 is more detailed. While Response 1 discusses adaptive content, learning styles, and dynamic difficulty adjustment, Response 2 takes it further with skill assessments, personalized learning pathways, and real-time feedback loops. This would enable the chatbot to react to each student's progress and provide a more personalized learning experience. Furthermore, Response 2 suggests utilizing visual learning aids and contextual memory, enabling the chatbot to recall past interactions and create a more integrated and personalized learning experience for students.

For sample interactions, Response 1 is focused largely on science-oriented topics such as quantum mechanics, photosynthesis, and biology quizzes. These are helpful examples but somewhat limited in scope. Response 2, on the other hand, mixes up the application scenarios for the chatbot by including programming concepts (loops and recursion), algebra (quadratic equations), and adaptive quizzes. This broader set of examples renders Response 2 more relevant to different fields of study, enhancing the chatbot's general versatility as a tool for learning.

Both responses are consistent logically, making the requirement analysis coherent and reasoned. They vary, however, in that Response 2 goes a step further by focusing more on interaction, engagement, and AI-driven personalization, hence the better response overall. If the goal is to achieve maximum student engagement, retention, and adaptability, Response 2 is the better option.

## 3.	Prompt-Template Technique

A prompt template is a formatted text model employed to produce AI responses uniformly by having placeholders for dynamic input values. Rather than typing new prompts manually every time, a template offers a reusable model in which variables are inserted to personalize the request. This method enhances efficiency, precision, and scalability, and it's particularly beneficial in chatbots, automation, and content creation. As an example, the prompt *"{prompt_type} Summarize the following {text_type} in {word_limit} words: {text}"* allows users to give the type of content, the word limit, and the text as dynamic values. By employing prompt standardization, this makes the method offer better AI performance with scope also left for difference in application contexts, such as education-based AI tutors, code generation, and content generation for formatting.

We use “prompt_template.ipynb” to do the enhancements.

Let us first create a prompt that follows prompt-template:

## Level-1 prompt:
TEMPLATE_BEFORE = "You are an AI expert in prompt engineering and chatbot development.\n"

MESSAGE = ("Generate a well-structured prompt that can be used to perform a requirement analysis "
           "for enhancing an existing Discord-based chatbot by adding educational functionality. "
           "The chatbot should help students understand advanced concepts easily using toy examples.\n")

TEMPLATE_AFTER = "Ensure that the generated prompt is clear, detailed, and effective for eliciting a comprehensive requirement analysis."

#### (2) Assembling the Final Prompt
PROMPT = TEMPLATE_BEFORE + MESSAGE + "\n" + TEMPLATE_AFTER

temperature=0.7, 
num_ctx=100, 
num_predict=1000

Output Below:

 [Prompt Template Level 1 Prompt Output](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/prompt-template-level-1-prompt.txt)

Level-2 Prompt:

#### (1) Define the Prompt Template
TEMPLATE_BEFORE = (
    "You are an AI expert in chatbot development and educational technology.\n"
    "Your task is to generate a detailed requirement analysis for enhancing an existing Discord-based chatbot "
    "by integrating educational functionality that helps students understand advanced concepts using toy examples.\n\n"
    "Follow the structured guidelines below:\n"
)

MESSAGE = (
    "**Objective:**\n"
    "Perform a thorough requirement analysis aimed at enhancing an existing Discord-based chatbot by integrating "
    "educational functionality that aids students in understanding advanced concepts through simple and relatable toy examples.\n\n"

    "**Scope of Enhancement:**\n"
    "1. **Target Audience:**\n"
    "   - Identify the primary user base (e.g., high school students, undergraduate students).\n"
    "   - Determine specific subject areas or disciplines to focus on (e.g., mathematics, physics, computer science).\n\n"
    
    "2. **Educational Content:**\n"
    "   - Define the types of advanced concepts that need to be addressed.\n"
    "   - Specify how toy examples can be used effectively to simplify these complex topics.\n\n"

    "3. **Functionality Requirements:**\n"
    "   - Interactive learning modules or sessions that guide students step-by-step.\n"
    "   - Features for real-time Q&A and feedback during chat interactions.\n"
    "   - Mechanisms for tracking progress and suggesting further study materials based on user interaction history.\n\n"

    "**Functional Specifications:**\n"
    "1. **Content Delivery:**\n"
    "   - How will the bot present educational content? (e.g., text, images, diagrams)\n"
    "   - What format should toy examples be in? (e.g., simple code snippets, story-based scenarios)\n\n"
    
    "2. **User Interaction:**\n"
    "   - Define how users will initiate a learning session.\n"
    "   - Determine interaction patterns for engaging students effectively.\n\n"
    
    "3. **Adaptability and Personalization:**\n"
    "   - How will the bot assess user understanding and adapt content accordingly?\n"
    "   - What personalization features can be implemented to cater to individual learning paces?\n\n"

    "**Technical Considerations:**\n"
    "1. **Integration with Discord APIs:**\n"
    "   - Ensure compatibility with current Discord functionalities.\n"
    "   - Identify any additional permissions or API capabilities needed.\n\n"

    "2. **Data Handling and Privacy:**\n"
    "   - Outline how user data will be managed, stored, and protected.\n"
    "   - Determine what information is necessary to collect for enhancing learning experiences while complying with privacy laws (e.g., GDPR).\n\n"

    "3. **Scalability and Performance:**\n"
    "   - Assess the current bot’s architecture and identify potential bottlenecks when adding new features.\n"
    "   - Plan for scalability in terms of user load and content complexity.\n\n"

    "**Stakeholder Involvement:**\n"
    "1. **Educational Experts:**\n"
    "   - Collaborate with educators or subject matter experts to ensure the accuracy and relevance of content.\n\n"

    "2. **User Feedback:**\n"
    "   - Establish a method for collecting and incorporating feedback from students using the bot.\n\n"

    "3. **Development Team Coordination:**\n"
    "   - Define roles and responsibilities within the development team for implementing new features.\n\n"

    "**Project Timeline and Milestones:**\n"
    "1. **Initial Research Phase:**\n"
    "   - Gather insights on existing educational tools and best practices.\n\n"

    "2. **Prototype Development:**\n"
    "   - Develop a basic prototype incorporating core functionalities.\n\n"

    "3. **Testing and Iteration:**\n"
    "   - Conduct user testing sessions to gather feedback and refine the bot’s capabilities.\n\n"

    "4. **Final Deployment:**\n"
    "   - Roll out the enhanced bot on Discord servers with monitoring for performance issues.\n\n"

    "**Success Metrics:**\n"
    "1. **User Engagement:**\n"
    "   - Measure the increase in active users interacting with educational content.\n\n"
    
    "2. **Learning Outcomes:**\n"
    "   - Assess improvements in students' understanding of advanced concepts through pre- and post-interaction evaluations.\n\n"

    "3. **Feedback Scores:**\n"
    "   - Gather user satisfaction ratings to gauge the effectiveness of toy examples and other features.\n\n"

    "**Deliverables:**\n"
    "Upon completion of this requirement analysis, provide a comprehensive report detailing:\n"
    "- Detailed user personas and use cases.\n"
    "- A feature list with prioritized requirements.\n"
    "- Technical specifications for implementation.\n"
    "- Proposed timeline with key milestones.\n"
    "- Risk assessment and mitigation strategies.\n"
)

TEMPLATE_AFTER = "Ensure the requirement analysis is well-structured and provides practical implementation insights."

#### (2) Assemble the Final Prompt
PROMPT = TEMPLATE_BEFORE + MESSAGE + "\n" + TEMPLATE_AFTER

#### (3) Configure the Model Request
# Documentation: https://github.com/ollama/ollama/blob/main/docs/api.md
payload = create_payload(target="open-webui",
                         model="phi4:latest", 
                         prompt=PROMPT, 
                         temperature=0.7, 
                         num_ctx=2000, 
                         num_predict=2000)

Output Below:

 [Prompt Template Level 2 Prompt Output](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/prompt-template-level-2-prompt.txt)


## Comparison of Responses:

Both responses offer a formal requirement analysis for implementing educational ability into a Discord-based chatbot. Both, however, are quite dissimilar in depth, structure, and detail.

The first response is all about listing functional needs in a plain, straightforward manner. It stresses fundamental features such as interactive tutorial modules, NLP capabilities, personalized learning paths, and gamification. The response gives a plain but generic image of the functionality that the chatbot will require, thereby being useful in the context of a preliminary brainstorming exercise. It lacks formal structure, does not go deeply into technical aspects, and does not provide a development roadmap.

The second answer is a lot more formalized, however. It segments the requirement analysis into sections, including scope, functional specifications, technical considerations, stakeholder participation, project timeline, and measures of success. Segmenting the requirement analysis in such a formalized manner ensures a comprehensive concept of what needs to be done in order to utilize the chatbot effectively. It also considers practical realities of actual implementation, such as adhering to privacy concerns, scalability, and monitoring user interaction, making it far more realistic for development teams to implement.

In addition, the second response provides a clear project schedule and milestones and outlines specific stages such as research, prototyping, testing, and deployment. It is therefore actionable rather than a list of ideas. It also includes success measures such as tracking user engagement and improvement in learning outcomes, which are important to measure the effectiveness of the chatbot upon implementation.

The second response is better because it is more organized, more detailed, and more realistic for real development. While the first response provides a high-level feature list, the second response provides a well-organized requirement analysis that covers both educational effectiveness and technical feasibility. It is more suitable for project planning and implementation and thus the better response for any individual who wants to actually develop the educational chatbot, not merely design it.

## 4.	Meta Technique


Meta Technique for AI and prompt engineering is a self-referential approach that instructs AI to refine its reasoning, structure, and output quality. Instead of answering a question outright, the AI is requested to analyze its own thinking, polish its response, or select between multiple possible responses before selecting the best one. The technique enhances accuracy, logical reasoning, and structured outputs by instructing the AI to edit itself and improve its responses.

Let us start with a level-1 meta prompt

META_PROMPT = (
    "Generate a prompt that can be used to perform a requirement analysis "
    "for adding educational functionality to an existing Discord-based chatbot."
)

#### (2) Configure the Model Request
payload = create_payload(target="open-webui",
                         model="phi4:latest", 
                         prompt=META_PROMPT, 
                         temperature=0.7, 
                         num_ctx=300, 
                         num_predict=300)

Output:

[Meta Level 1 Prompt](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/meta-level-1-prompt.txt)
[Meta Level 1 Prompt Result](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/meta-level-1-prompt-Result.txt)



Level-2 Meta Prompt:
META_PROMPT = (
    "Generate a prompt that generates another prompt that can be used to perform a requirement analysis "
    "for adding educational functionality to an existing Discord-based chatbot."
)

#### (2) Configure the Model Request
payload = create_payload(target="open-webui",
                         model="phi4:latest", 
                         prompt=META_PROMPT, 
                         temperature=0.7, 
                         num_ctx=300, 
                         num_predict=300)

## Output:

[Meta Level 2 Prompt](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/meta-level-2-prompt.txt)
[Meta Level 2 Prompt Result](https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2-PromptEngineering/blob/main/Outputs/meta-level-2-prompt-Result.txt)


## Comparison of two results:

The Level-1-Prompt result and Level-2-Prompt result provide structured requirement analyses for integrating educational functionalities into a Discord-based chatbot, but they differ in terms of depth, clarity, and comprehensiveness. The Level-1-Prompt result presents an organized list of focus areas but lacks detailed explanations in some sections. In contrast, the Level-2-Prompt result follows a well-structured approach with numbered sections, sub-sections, and detailed explanations, making it easier to understand and implement. The logical sequencing in the Level-2-Prompt result also improves readability and clarity.
When comparing the clarity and depth of information, the Level-1-Prompt result provides broad categories but does not elaborate on the implementation of features. The Level-2-Prompt result, however, not only defines key requirements but also explains how they can be integrated into the chatbot. For example, it details API usage, interaction design, and command syntax, which are essential for a successful implementation. This makes the Level-2-Prompt result more actionable and valuable for developers.
A key differentiator is the handling of functional and non-functional requirements. The Level-1-Prompt result primarily lists functional improvements, such as quizzes and study reminders, but does not explicitly distinguish between functional and non-functional aspects. The Level-2-Prompt result, on the other hand, clearly separates these elements, discussing both the chatbot's core functionalities and non-functional aspects like performance metrics, response speed, and system uptime. This ensures a more complete and structured requirement analysis.
Technical considerations are another area where the Level-2-Prompt result excels. While the Level-1-Prompt result briefly mentions infrastructure and privacy considerations, it lacks specific implementation details. The Level-2-Prompt result provides an in-depth discussion on API integrations, backward compatibility, potential data synchronization issues, and security measures such as encryption protocols. This level of technical depth ensures that the chatbot upgrade is planned with a strong foundation.
Compliance and scalability are also better addressed in the Level-2-Prompt result. While the Level-1-Prompt result mentions scalability in a general sense, the Level-2-Prompt result thoroughly discusses GDPR compliance, data protection laws, and steps for ongoing regulatory adherence. It also provides a roadmap for regular compliance reviews, aligning with legal and ethical standards.
The Level-2-Prompt result is the stronger choice because it provides a more detailed, structured, and actionable requirement analysis. It defines what needs to be done and explains how to implement each feature effectively. With its focus on technical integration, security, user experience, and compliance, the Level-2-Prompt result offers a more comprehensive plan, making it the best option for enhancing the chatbot’s educational functionalities. 

## 5.	Few Shots Technique

Few-Shot is a machine learning and prompt engineering method where a model is given a small number of examples—typically two to five—so that it has an idea of the task before the response is generated. It works very well with large language models, as this provides context without requiring much retraining or fine-tuning. The model can infer patterns and apply them to new, unseen inputs by including a few relevant examples in the prompt.

Few-shot prompting accomplishes this by providing the model with a few example input-output pairs to show the intended behavior. The model, having learned from these examples, is then given a new input that is of a similar pattern, and it is expected to generate an acceptable response. For instance, if an example provides some English-Spanish word pairs like "Apple -> Manzana" and "Dog -> Perro" in a translation problem, the model can learn the pattern and then translate a new word like "House -> Casa" properly.

This technique is particularly beneficial as it reduces the requirement for large amounts of labeled data or fine-tuned models but still improves precision. It allows models to generalize better than zero-shot learning, where no examples are provided, but not as much as traditional supervised learning, which requires extensive numbers of marked data. Few-shot prompting is applicable in extensive domains of education software, chatbots, and AI services where flexibility and quick learning are required.

## First Experimentation:-

MESSAGE = "I want to add an educational chatbot that helps students understand advanced concepts in a much easier way to my Discord-based bot."

FEW_SHOT = """You are a software requirements analyst. Your task is to analyze and define the requirements for adding an educational chatbot to a Discord-based bot. 
If the request is to enhance an existing chatbot with educational features, follow this format:
1. Objective: Clearly define what the chatbot should achieve.
2. Core Functionalities: List the key features required for an educational chatbot.
3. User Interaction: Describe how students will interact with the chatbot.
4. Integration Requirements: Explain how to integrate with Discord and any external APIs.
5. Challenges & Considerations: Identify potential issues and solutions.

Example:
User request: "Add a tutoring feature to my Discord bot."
Response:
1. Objective: Enable the bot to provide tutoring on various subjects.
2. Core Functionalities: Subject-specific explanations, quizzes, interactive Q&A.
3. User Interaction: Students can ask questions and get detailed answers with examples.
4. Integration Requirements: Use Discord bot commands, embed AI models for responses.
5. Challenges & Considerations: Ensure accuracy, prevent misinformation, support multiple learning styles.

Now, analyze the following request and generate the requirements:
"""
PROMPT = FEW_SHOT + '\n' + MESSAGE
temperature=1.0, 
                         num_ctx=100, 
                         num_predict=100

In the above snippets, the few shot technique has been employed by adding one example to the prompt. However, the number of tokens is 100 since the length of the prompt is less than 100. 

Output:
 
## Second Experimentation:

We tried to enhance the prompt by giving two examples this time.

FEW_SHOT = """

You are a software requirements analyst. Your task is to analyze and define the requirements for adding an educational chatbot to a Discord-based bot. 
If the request is to enhance an existing chatbot with educational features, follow this format:
1. Objective: Clearly define what the chatbot should achieve.
2. Core Functionalities: List the key features required for an educational chatbot.
3. User Interaction: Describe how students will interact with the chatbot.
4. Integration Requirements: Explain how to integrate with Discord and any external APIs.
5. Challenges & Considerations: Identify potential issues and solutions.

Example 1:
User request: "Add a tutoring feature to my Discord bot."
Response:
1. Objective: Enable the bot to provide tutoring on various subjects.
2. Core Functionalities: Subject-specific explanations, quizzes, interactive Q&A.
3. User Interaction: Students can ask questions and get detailed answers with examples.
4. Integration Requirements: Use Discord bot commands, embed AI models for responses.
5. Challenges & Considerations: Ensure accuracy, prevent misinformation, support multiple learning styles.

Example 2:
User request: "Make my Discord bot help students learn through interactive flashcards."
Response:
1. Objective: Improve student retention using flashcard-based learning.
2. Core Functionalities: Flashcard generation, spaced repetition system, voice-based quizzes.
3. User Interaction: Students can create, review, and test themselves using the chatbot.
4. Integration Requirements: Connect with a database to store flashcards, use AI to auto-generate them.
5. Challenges & Considerations: Maintain a balanced difficulty level, avoid redundancy.

Now, analyze the following request and generate the requirements:
"""

Output:
 

## Third Experimentation:

The prompt has nothing to change. Only the parameters are worked on.

temperature=0.2, 
num_ctx=150, 
num_predict=200

Since the required answer is technical, the temperature is set to a lower value for more factual based answer. We wanted the answer to be more clear and elaborate. Hence, the num_predict value is set to 200.

Output:
 

Since we are a team of three, our experiment gave us a sharp insight into how Few-Shot Prompting, Example Variation, and Hyperparameter Tuning influence the response quality. From using a single example (Response 1), we noted that the chatbot's response did not have much depth and lacked essential features like concept mapping and progress monitoring. However, two-example prompting (Responses 2 and 3) led to better-structured responses that touched on important points such as adaptive learning, feedback mechanisms, and integration strategies. This was proof that two-shot prompting is far superior to one-shot prompting as it raises coherence and response completeness.
We also experimented with hyperparameter tuning through specifically altering temperature, context length ('num_ctx'), and prediction tokens ('num_pred'). At temperature set at 1.0, 'num_ctx' at 100, and 'num_pred' at 100, Response 2 performed best, striking a balance between structure and detail and being clear and concise. However, lowering the temperature to 0.3 and 'num_ctx' to 150 and 'num_pred' to 200 (Response 3) produced a more factual but more rigid response. Although the increased context and predictive length helped in preserving details, it was not helpful in enhancing structuring considerably. The lowered temperature made the chatbot response less flexible and conversational, slightly lowering engagement.

Overall, Response 2 worked best, having achieved an optimal balance between depth, expressiveness, and structure clarity. Two-shot prompting helped with learning patterns, and temperature set at 1.0 allowed for a more natural, not to mention interesting, response. Context length of 100 was effective, which kept responses on point and did not allow expansion where it was unnecessary. What we learned from this experiment was that few-shot prompting with at least two examples results in more complete and coherent responses, and setting temperature at approximately 1.0 ensures more engagement. Further increases in context length beyond 100-150 were of limited value, rendering it helpful only for applications involving longer recall instead of better structuring.

In the future, we might improve our strategy by trying variations in instructions or formatting enhancements in responses to enhance readability and clarity further. It may also be worth trying different methods of presenting examples as part of the prompt to determine whether that also boosts the quality of responses.


## 6.	Chain of Thought

Chain of Thought (CoT) is an artificial intelligence and machine learning prompting method that aids in reasoning and problem-solving by inducing the model to break down complicated tasks into mid-level steps. Instead of giving a direct answer, the model is asked to reason stepwise, mimicking human thinking. This method is particularly useful in tasks requiring logical reasoning, solving math problems, or multi-step decision-making.

In Chain of Thought prompting, the model is given examples that not only show the right solution but also outline the thinking process which builds up to that. That way, the model learns generating explanations before a final solution, improving accuracy as well as interpretability. For instance, while doing a word problem in mathematics, a usual request would just ask for the solution, whereas a Chain of Thought request would provide a line-by-line detail of every step from the very beginning to derive the final answer.

For instance, if one needs to do the following: "Alice possesses 3 apples and purchases an additional 5. How many apples does Alice now have?"

It could be a typical prompt that would result in the model answering immediately: "Alice has 8 apples."

However, when prompted using Chain of Thought prompting, the model would produce: "Alice initially has 3 apples. She buys 5 more apples. Adding them together, 3 + 5 = 8. Thus, Alice has 8 apples."

This method is particularly helpful for learning chatbots, like the one you're building for Discord, since it not only enables students to get the correct answer but also learn the reasoning behind it. Applying Chain of Thought prompting can improve how your chatbot educates complex concepts in math, science, and logic-based subjects.

## First Experimentation:

CHAIN_OF_THOUGHT = I am running a few minutes late; my previous meeting is running over.
f"""
You are a software requirements analyst. Your task is to analyze and define the requirements for adding an educational chatbot to an existing Discord-based bot.

To generate a structured and well-thought-out response, follow this reasoning process step by step:

1 ''Identify the Primary Objective''  
   - What is the main goal of adding the educational chatbot?
   - How should it help students understand complex concepts more easily?

2 ''Determine Core Functionalities''  
   - What are the essential features required for the chatbot?
   - Should it provide concept explanations, quizzes, and interactive learning?
   - How can AI or NLP improve student engagement?

3 ''Define User Interaction Flow''  
   - How will students interact with the chatbot?
   - Should it support ''commands'' (e.g., '/explain topic') or ''natural language'' input?
   - How will feedback and learning adaptation be handled?

4 ''Integration Requirements''  
   - What technologies, APIs, or AI models should be integrated?
   - How should it connect with the existing Discord bot framework?
   - Should it pull resources from external knowledge bases or educational APIs?

5 ''Identify Challenges & Considerations''  
   - What are potential issues in terms of ''accuracy, engagement, scalability, and data privacy''?
   - How can the chatbot be ''improved over time'' based on student feedback?

---
### ''Example Thought Process''
''User Request:'' "I want to add an educational chatbot to my Discord bot that helps students understand advanced concepts easily."

 ''Step 1 - Objective:''  
   - The chatbot should simplify difficult concepts, provide structured learning support, and engage students in active learning.

 ''Step 2 - Core Functionalities:''  
   - Concept explanations with real-world analogies  
   - AI-powered Q&A support   
   - Adaptive learning paths based on student progress  
   - Quizzes and interactive assessments  

 ''Step 3 - User Interaction Flow:''  
   - Students can ask questions using '!explain <topic>' or interact through conversation.  
   - The bot provides ''multi-step explanations'' to help students build understanding.  
   - Feedback from students improves future responses.  

 ''Step 4 - Integration Requirements:''  
   - Use Discord bot commands for structured queries.  
   - Implement GPT-based NLP for natural responses.  
   - Connect to external APIs (Khan Academy, Wikipedia) for additional resources.  

 ''Step 5 - Challenges & Considerations:''  
   - Ensure ''accuracy'' of explanations to prevent misinformation.  
   - Design for ''engagement'' to keep students interested.  
   - Scale efficiently to handle multiple students at once.  

---
### ''Now, analyze the following request and generate the requirement analysis:''
"I want to add an educational chatbot that helps students understand advanced concepts in a much easier way to my Discord-based bot."
"""

We employed the Chain of Thought Prompt technique in our code by giving a step-by-step process to give the result. Since the input has more words, the number of tokens is set to 1000, and for the answer to be very elaborate, the num_predict value is set to 300.

Output:
 
Second Experimentation:
Temperature set to 1.2
 
Third Experimentation:
Temperature set to 0.5
 

## Comparison of responses:

As seen from our experiment, we can observe the influence of temperature values on responses in a Chain of Thought (CoT) prompting technique while investigating the necessities in deploying an educational chatbot in a Discord bot. Since we used the same prompt for all three responses, the differences in output were influenced directly by how the temperature differed.

The first response, which was produced at temperature 1.0, provided the best balance between creativity, coherence, and structure. It maintained the well-ordered structure, ensuring the chatbot requirements were laid out well while allowing flexibility in the response. This level was most appropriate for requirement analysis, as it allowed detailed yet concise reasoning while ensuring the response was engaging and versatile.

The second response, generated at temperature 1.2, resulted in a more creative but also slightly chaotic answer. While it included more details and dwelled on particular functionalities, some of the information was not crucial or was repetitive for a structured requirement analysis. This temperature setting seems more suitable for brainstorming or designing new ideas, where the different possibilities need to be explored rather than following a clear structure.

The third response, with the temperature at 0.5, was the most structured and factual. It provided a briefer and more implementation-focused response, ensuring that all specifications were laid out clearly and explicitly. But with the lowered temperature, the response was less adaptable and creative and was therefore less engaging than the first two. Although this setting would be perfect for strict technical documentation, it is less than perfect for flexible and dynamic requirement gathering. 

Based on these observations, we concluded that the most appropriate setting for generating structured requirement analyses is temperature 1.0. This setting ensures responses that are detailed, well-structured, and adaptive, making it the most appropriate to outline the functionality, user interaction, and integration requirements of our teaching chatbot. If we were attempting to do brainstorming or idea expansion, we might use a higher temperature of 1.2. Alternatively, if we wanted short, precise implementation steps, we might try lowering the temperature to 0.5.

## 7.	Generate Knowledge Technique

Generate Knowledge Prompting is a prompt engineering method whereby a model is first prompted to create applicable background knowledge prior to answering a question or solving a problem. This method strengthens reasoning, precision, and comprehension, especially where a literal response might lack sufficient context. Instead of producing a response instantly, the model is subjected to a two-step process: one, it recollects or generates fundamental information on the subject, and second, employs the same information in generating a well-versed answer. For example, when a question is asked about why the sky appears blue, instead of responding "because of Rayleigh scattering," the model would begin by explaining what Rayleigh scattering is—shorter wavelengths like blue light scatter more than longer wavelengths like red—before applying that understanding to provide an answer. This way of thinking enhances it, makes it more accurate in its responses, and gives better explanations, so it is extremely well suited for educational use. Utilizing Generate Knowledge Prompting on your Discord study chatbot can help students comprehend complex concepts more effectively by encouraging systematic thinking and step-by-step learning.

## Experimentation 1:

MESSAGE = ("Before performing the requirement analysis, first generate foundational knowledge on how AI-powered "
    "educational chatbots improve student learning, focusing on:\n"
    "- Cognitive and pedagogical principles behind effective tutoring.\n"
    "- How simplifying complex topics using toy examples improves retention.\n"
    "- The role of personalization in adaptive learning systems.\n"
    "- How AI models can be optimized to improve explanation clarity and engagement.\n"
    "- Key challenges in AI-driven education and how to address them.\n\n"
    "After generating this knowledge, proceed with the requirement analysis to enhance an existing Discord chatbot "
    "built using the Owlmind framework into an educational chatbot. The chatbot should simplify advanced topics for "
    "students using toy examples. Focus on educational improvements and provide:\n"
    "1. Additional educational features required, informed by the generated knowledge.\n"
    "2. Learning methodologies the chatbot should adopt based on effective AI tutoring strategies.\n"
    "3. Ways to personalize learning for different student levels, leveraging AI-driven adaptability.\n"
    "4. AI model improvements to enhance explanations and engagement.\n"
    "5. Example interactions demonstrating improved learning experience.\n\n"
    "First, generate the relevant knowledge step-by-step, then use that knowledge to structure the final requirement analysis. "
    "Format the response with clear sections and bullet points for readability.")

## Experimentation 2: 
Temperature set to 0.5

Output:
 
## Experimentation 3:
Temperature is set to 1.4

Output:
 

## Analysis:
According to our experiment comparing the answers produced using the "Generate Knowledge (GK) prompting strategy," we observed the distinct impacts of the various "temperature settings" on the quality, organization, and applicability of the answers. Each temperature setting produced a distinctive response style that had different degrees of applicability of the demands of the chatbot analyzed and organized.

The answer produced under "temperature 0.5" was most "organized, specific, and fact-based.". It provided clear and concise explanations so that every point of requirement analysis had been addressed in a coherent way. The response was "highly practical" and the best to utilize for "direct implementation" as it focused on providing information without unnecessary elaboration. However, while being very good in terms of clarity and precision, it was somewhat "less engaging" than the higher temperature responses because it avoided exploratory reasoning or innovative analogy.

The response at "temperature 0.7" possessed the "best balance" of "clarity, depth, and creativity". It was well-structured in terms of requirement analysis and made use of "engaging explanations, apt examples, and relevant connections" among AI-based learning approaches. The response was "informative and flexible" and thus a suitable choice for "both requirement planning and chatbot design improvements". In contrast to the response under lower temperature, it contained greater "contextual reasoning and insightful explanations" but was more readable and still structured and pragmatic.

The "temperature 1.4 response" was "most innovative and interrogative," featuring rich information, richer analogies, and "interactive learning strategies" that were likely to enhance AI-based education. While this response was "highly innovative", it was "more wordy and slightly less structured", which may make it less ideally suited to direct implementation but highly useful for "brainstorming new AI-driven educational features". This setting was best suited to "idea generation and exploring new ways of augmenting the abilities of the chatbot", as opposed to exactly defining the requirements for implementation.

Depending on our requirements, the perfect response is based on our analysis. If we are "focusing on structured requirement analysis and direct implementation", then "temperature 0.5 response is the best choice". But if we also have to explore "engaging and innovative methods to improve AI-based learning", then "temperature 0.7 provides the best trade-off" between structure and innovation. The "temperature 1.4 response works best for brainstorming", where we need "broad, creative ideas on improving AI-powered tutoring".

Because our focus is "requirement analysis for an educational chatbot," we should "appreciate the structured clarity of the 0.5 response," but "include some creative elements from the 0.7 response" to make it more interesting. We can also use the "1.4 response for creating novel feature ideas" if needed in the future.

## 8.	Prompt Chaining Technique

Prompt Chaining is a prompt engineering method in which two or more prompts are linked together in a sequence to guide an AI model through a complex task in incremental steps. Instead of formulating a final response in a single prompt, the task is broken down into intermediate steps, with each prompt building upon the output of its predecessor. This method improves reasoning, precision, and coherence and is therefore best used in problem-solving with multiple steps, content generation, and decision-making. Prompt chaining is being most widely used in educational chatbots, workflow automation, and guided AI interactions where a step-by-step approach must be used to obtain improved outputs.

Code:

##
## PROMPT CHAINING FOR REQUIREMENT ANALYSIS
##

from _pipeline import create_payload, model_req

#### (1) Step 1 - Generate Key Requirement Areas
INITIAL_PROMPT = (
    "Identify the five most important aspects to consider when developing an educational chatbot for Discord. "
    "Focus on how it can simplify advanced topics for students using toy examples."
)

payload_step1 = create_payload(target="open-webui",
                               model="phi4:latest", 
                               prompt=INITIAL_PROMPT, 
                               temperature=0.7, 
                               num_ctx=300, 
                               num_predict=300)

response_time1, response1 = model_req(payload=payload_step1)
print("Step 1 Response:\n", response1)
if response_time1: print(f'Time taken: {response_time1}s')

#### (2) Step 2 - Expand on Each Requirement
EXPANSION_PROMPT = (
    f"Based on these key aspects: {response1}, provide a detailed breakdown of each, including: \n"
    "1. Specific functionalities required.\n"
    "2. AI learning methodologies that should be integrated.\n"
    "3. Ways to personalize learning for different student levels.\n"
    "4. AI model improvements to enhance explanations and engagement.\n"
    "5. Example interactions demonstrating improved learning experiences.\n"
    "Structure the response in a well-organized format."
)

payload_step2 = create_payload(target="open-webui",
                               model="phi4:latest", 
                               prompt=EXPANSION_PROMPT, 
                               temperature=0.7, 
                               num_ctx=600, 
                               num_predict=900)

response_time2, response2 = model_req(payload=payload_step2)
print("Step 2 Response:\n", response2)
if response_time2: print(f'Time taken: {response_time2}s')

#### (3) Step 3 - Final Requirement Analysis
FINAL_PROMPT = (
    f"Using the expanded details provided: {response2}, generate a complete requirement analysis for an educational chatbot. "
    "The chatbot should be designed for Discord and simplify advanced topics using toy examples. "
    "Ensure the response is structured into clear sections with bullet points for readability."
)

payload_step3 = create_payload(target="open-webui",
                               model="phi4:latest", 
                               prompt=FINAL_PROMPT, 
                               temperature=0.7, 
                               num_ctx=1000, 
                               num_predict=1200)

response_time3, response3 = model_req(payload=payload_step3)
print("Final Requirement Analysis:\n", response3)
if response_time3: print(f"Time taken: {response_time3}s")


Output:
 
## 9.	Retrieval Augmented Generation

Code:

##
## SINGLE-PROMPT RAG FOR REQUIREMENT ANALYSIS
##

from _pipeline import create_payload, model_req

#### (1) Single Prompt - Retrieval + Generation Combined
RAG_PROMPT = (
    "Retrieve relevant insights from trusted educational AI resources on designing AI-powered educational chatbots for Discord. "
    "Ensure that the retrieved knowledge includes:\n"
    "1. Best practices in AI-driven tutoring and adaptive learning.\n"
    "2. Techniques for simplifying complex topics using toy examples.\n"
    "3. Personalization strategies to adjust content for different student levels.\n"
    "4. AI-driven engagement strategies to keep students interested in learning.\n"
    "5. Challenges faced in AI-based education and ways to mitigate them.\n\n"
    
    "Using the retrieved knowledge, generate a structured **requirement analysis** for enhancing a Discord-based chatbot into an educational assistant. "
    "Ensure the response includes:\n"
    "- **Objective:** Define the chatbot’s role in simplifying advanced topics.\n"
    "- **Core Functionalities:** Outline key features needed for effective learning.\n"
    "- **User Interaction Model:** Explain how students will interact with the chatbot.\n"
    "- **AI Model Enhancements:** Suggest ways to improve explanation quality.\n"
    "- **Integration Requirements:** Detail necessary APIs, AI models, and tools.\n"
    "- **Challenges & Considerations:** Identify potential obstacles and solutions.\n\n"
    
    "Ensure that the response is structured, fact-based, and clearly formatted for easy readability."
)

#### (2) Configure the Model request, simulating Workflow Orchestration
payload = create_payload(target="open-webui",
                         model="phi4:latest", 
                         prompt=RAG_PROMPT, 
                         temperature=0.7, 
                         num_ctx=1000, 
                         num_predict=1200)

### YOU DON’T NEED TO CONFIGURE ANYTHING ELSE FROM THIS POINT
# Send out to the model
response_time, response = model_req(payload=payload)
print(response)
if response_time: print(f'Time taken: {response_time}s")

Output:
 


## 10.	Automatic Reasoning

Automatic reasoning is a branch of artificial intelligence (AI) and computer science that is concerned with the ability to make computers reason logically and come to conclusions without any human interaction. It refers to how algorithms and formal logic are used to derive conclusions, establish proofs of theorems, analyze data, or make decisions based on inputs. Automatic reasoning has great implications in mathematics, formal verification, natural language processing, and expert systems.

Automatic reasoning encompasses several types, including deductive reasoning (the process of obtaining conclusions from existing facts or rules), inductive reasoning (reaching general conclusions from specific observations), and abductive reasoning (inferring the most likely explanation of a specified set of facts). Methods such as rule-based reasoning, constraint solving, and machine learning-based reasoning are used extensively to enhance the accuracy and efficiency of computer-based decision-making.

For AI chatbots, including educational chatbots, automatic reasoning can provide logical explanations, verify answers, and guide users through systematic problem-solving. Students can have step-by-step solutions, logical explanations, and enhanced learning experiences by integrating automatic reasoning into a chatbot.

Code:

AUTO_REASONING_PROMPT = (
    "Retrieve the most relevant knowledge from educational AI research and chatbot design principles to understand "
    "how an AI-powered Discord chatbot can simplify complex topics for students using toy examples.\n\n"

    "Step 1 - Retrieve Knowledge:\n"
    "Gather factual insights on:\n"
    "- Effective tutoring strategies in AI-driven education.\n"
    "- How AI can personalize learning for students of varying levels.\n"
    "- The best ways to use toy examples to simplify advanced concepts.\n"
    "- Challenges in AI-based education and potential solutions.\n\n"

    "Step 2 - Logical Deduction & Automatic Reasoning:\n"
    "Analyze the retrieved information and reason through how these principles should be applied to a Discord-based educational chatbot. "
    "Use a systematic, logical approach to refine requirements, ensuring that all features are necessary, scalable, and impactful.\n\n"

    "Step 3 - Structured Requirement Analysis Generation:\n"
    "Based on the reasoned insights, generate a structured requirement analysis for upgrading a Discord chatbot with educational capabilities. "
    "Ensure that the response includes:\n"
    "- Objective: Define the chatbot’s role and purpose.\n"
    "- Core Functionalities: Essential features needed for educational engagement.\n"
    "- User Interaction Model: How students will interact with the chatbot effectively.\n"
    "- AI Model Enhancements: Improvements in explanations, reasoning, and user engagement.\n"
    "- Integration Requirements: APIs, external knowledge sources, and AI tools needed.\n"
    "- Challenges & Solutions: Identify potential obstacles and their resolutions.\n\n"

    "Ensure that the reasoning is step-by-step, fact-driven, and logically sound before generating the final requirement analysis."
)
Output:
 

Comparison of all the techniques:
For our use case—building an educational chatbot for Discord to simplify challenging topics for students—the best approach needs to enhance student engagement, provide systematic step-by-step descriptions, enable adaptive learning, and present a clear and logical requirement analysis for building the chatbot. Based on the experiment results and comparisons, the best approach is the integration of Prompt Chaining, Few-Shot Prompting, and Generate Knowledge Prompting.

Prompt Chaining plays a vital role as it helps the chatbot break down complicated topics into minor, step-wise pieces so that students are led through the process of learning rather than being told one direct answer. Prompt Chaining increases engagement, and the chatbot turns more interactive in areas like math, science, and programming. For example, in describing how to solve a quadratic equation, the chatbot can start with defining the term, then apply the formula, and finally solve an example problem interactively. This manner, students learn concepts in a step-by-step logical sequence rather than memorizing the solutions.

Few-Shot Prompting significantly improves response quality by ensuring that the chatbot follows a systematic method in its explanation. Having a minimum of two examples in the question allows the chatbot to generate more accurate and fuller replies, consistent in explanation. By careful training of the chatbot with well-structured examples, such as Newton's Third Law being described in breakdown or an electric circuit described in step-by-step format, the chatbot learns to give similar good-quality replies to other questions. This enhances clarity, easy to understand and follow the answers.

Generate Knowledge It further enhances response quality by asking the chatbot to retrieve appropriate background knowledge prior to answering a question. Rather than giving brief, shallow answers, the chatbot first retrieves relevant information and then builds a rich answer. For example, if the question of why the sky is blue is asked, rather than providing a one-word answer such as "due to Rayleigh scattering," the chatbot will describe the phenomenon of Rayleigh scattering first and then relate it to the phenomenon. This way, answers are not just correct in terms of fact but also provide a better understanding, enhancing the student's level of understanding.

Other approaches, such as Zero-Shot Prompting, Self-Consistency, and Retrieval-Augmented Generation (RAG), do not work as well for our application. Zero-shot prompting yields inconsistent and incomplete responses, and self-consistency prioritizes checking logical consistency over enhancing engagement. RAG excels at fact-based retrieval, but our chatbot must do more than just retrieve information—it must engage, explain, and lead students in an interactive fashion. While hyperparameter tuning, such as temperature adjustments, can better the response style, they don't significantly better the chatbot's performance at teaching ideas.

By incorporating Prompt Chaining, Few-Shot Prompting, and Generate Knowledge Prompting, our chatbot will be interactive, structured, and responsive to learners' needs. Prompt chaining will give step-by-step, interactive instructions, few-shot prompting will bring better coherence to responses, and generate knowledge prompting will introduce depth and detail into explanations. This mixture will not just turn our chatbot into an information outlet but also into a good digital tutor, one that can suit different learning patterns and make it easy for students to grasp difficult ideas. 

GITHUB REPO: https://github.com/VamsiNamballa/COT6930-SyntaxSultans-Assignment-2


## Final Thoughts:-
This research contributes to AI-driven software engineering by demonstrating how advanced prompting techniques can be applied to automate the development of intelligent learning chatbots. Through enhanced requirement analysis methodologies, we aim to make AI-driven learning tools more effective and provide students with an easier-to-use study aid.
