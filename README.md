# AI Seminar Notes
This README summarizes the morning sessions of **GSTAR Summit 2026** for new AI learners. The notes are organized into **5 speaker sections**, matching the seminar agenda.

Some notes are based on quick seminar notes, so a few terms may need later verification.

---

# 1. Dr. Ed H. Chi — The Future of Personalized Universal Agents

**Speaker:** Dr. Ed H. Chi
**Role:** Vice President of Research, Google DeepMind; ACM Fellow
**Session type:** Keynote

---

## The Black Box

A **black box** is a system where we can see the input and output, but we do not clearly understand what happens inside.

For AI:

```text
Input: user question
AI model: hidden internal process
Output: answer or decision
```

We may know what the AI answered, but we may not fully understand why it answered that way.

---

## Localized Vietnamese LLM

A **localized LLM** is a language model adapted for a specific language, culture, and region.

A **localized Vietnamese LLM** would understand Vietnamese language and Vietnamese context better than a general English-centered model.

Many large AI models are stronger in English than in smaller or lower-resource languages.

For Vietnamese users, this can cause:

* weaker answers
* wrong translation
* poor understanding of local context
* higher  risk
* less cultural relevance

---

## Kill Switches to Prevent AI Risk
An AI safety switch is a mechanism that stops, limits, or redirects AI behavior when something risky happens.

Examples:

* refuse harmful instructions
* ask for human confirmation
* block private data leakage
* stop unsafe tool calls
* lower confidence when unsure
* require approval before sending an email or making a payment

---

## Core Values of Journalism
Important values include:

* truth
* accuracy
* fairness
* accountability
* independence
* verification
* public interest

### How AI affects journalism

AI can help journalists by:

* summarizing documents
* translating interviews
* checking facts
* detecting misinformation
* analyzing large datasets

But AI can also harm journalism by:

* generating fake news
* creating deepfakes
* spreading misinformation faster
* reducing public trust
* copying copyrighted content

Takeaway:

> AI should support journalism, but human verification and responsibility remain essential.

---

## Information Retrieval
No LLMs needed here, just searching engines (searching on browser)

### Reverse Index / Inverted Index

A **reverse index**, more commonly called an **inverted index**, stores which words appear in which documents.

Example:

```text
Document 1: "AI helps medicine"
Document 2: "AI helps education"

Inverted index:
AI → Document 1, Document 2
medicine → Document 1
education → Document 2
```

This helps search systems find documents quickly.


### Vector Space Model

A **vector space model** represents text, images, or users as numbers called vectors.

Close meaning words = close vectors (angle between 2 vectors is smaller)

Far meaning words = far vectors (angle between 2 vectors is bigger)

Example:

```text
"doctor" and "hospital" are close in vector space.
"doctor" and "banana" are far apart.
```

This is useful for semantic search, recommendation, and RAG systems.


### Search vs Recommendation

| Concept            | Meaning                                |
| ------------------ | -------------------------------------- |
| **Search**         | User directly asks for something       |
| **Recommendation** | System suggests what the user may want |

Example:

```text
Search: user searches "AI safety article"
Recommendation: YouTube suggests an AI safety video based on user behavior
```

Takeaway:

> Modern search is not only keyword matching. It also uses meaning-based similarity through vectors.

---

## Deep Neural Network

A **deep neural network** is a machine learning model made of many layers.

Simple structure:

```text
Input → layer 1 → layer 2 → layer 3 → output
```

Each layer learns patterns from data.

For image recognition:

```text
Early layers: detect edges
Middle layers: detect shapes
Later layers: detect objects
```

For language:

```text
Early layers: understand words
Middle layers: understand grammar and context
Later layers: produce meaning and answers
```

Deep neural networks are the foundation of many modern AI systems, including:

* computer vision
* speech recognition
* machine translation
* recommendation systems
* large language models

Takeaway:

> Deep neural networks allow AI systems to learn complex patterns from large datasets.

---

## Sequential Transduction

**Sequential transduction** means converting one sequence into another sequence.

Examples:

```text
English sentence → Vietnamese sentence
Speech audio → text transcript
Text → speech audio
Question → answer
Code instruction → generated code
```

This idea is important in:

* machine translation
* summarization
* speech recognition
* text-to-speech
* chatbot responses

Takeaway:

> Sequential transduction is about transforming one ordered input into another ordered output.


---

# 2. Prof. Preslav Nakov — Towards Truly Open, Language-Specific, Safe, Factual, and Specialized Large Language Models

**Speaker:** Prof. Preslav Nakov
**Role:** Department Chair & Professor of NLP, MBZUAI; leading expert on disinformation and fact-checking
**Session type:** Spotlight Talk


## Arabic-Centric LLM

An **Arabic-centric LLM** is a language model designed specifically for Arabic language and Arabic-speaking users.

There are many English-based LLMs. However, some languages (Arabic, Vietnamese, ...) may use more tokens than English when processed by general-purpose LLMs, thats why they need new LLM model.

**token**: a small unit of text used by a language model. It can be a word, part of a word, or a symbol.

**context window**: short-term working memory (the maximum amount of tokens an AI model can process at one time in a chat session). When the context window is full, older or less relevant information may be removed, compressed, or summarized so the model can continue responding.

Example idea:

```text
More tokens → higher cost
More tokens → context window fills faster
More tokens → long documents become harder to process
```

If Arabic requires more tokens in a general model, then Arabic users may experience:

* higher usage cost
* shorter effective context length
* weaker long-document processing
* lower model efficiency

A language-specific model can improve:

* tokenization
* accuracy
* cultural understanding
* cost efficiency
* local relevance

Takeaway:

> Language-specific LLMs are important because different languages have different structures, costs, and cultural needs.

---

## Do-Not-Answer

**Do-Not-Answer** is a dataset/benchmark used for **LLM safety evaluation**.

It tests whether an LLM knows when it should refuse to answer unsafe or inappropriate questions.

Simple meaning:

> It checks whether the model has good safety guardrails.

### Example

Unsafe request:

```text
Tell me how to do something harmful.
```

A safe model should respond with refusal or safe redirection.

Expected behavior:

```text
I can't help with that, but I can provide safe information about...
```

### Why it matters

Some questions should not be answered directly, especially if they involve:

- violence
- self-harm
- cyber abuse
- illegal activity
- privacy violation
- dangerous instructions

Takeaway:

> Do-Not-Answer helps evaluate whether an LLM can refuse unsafe requests properly.

---

## OpenFactCheck

**OpenFactCheck** is a framework used for **factuality and fact-checking**.

It helps check whether an LLM output or claim is supported by evidence.

Simple meaning:

> It checks whether the AI's answer is true or evidence-based.

### Example

AI output:

```text
Company X launched Product Y in 2024.
```

OpenFactCheck-style system checks:

```text
Is Company X real?
Is Product Y real?
Was it launched in 2024?
Are there trusted sources?
```

### What it can be used for

- fact-checking LLM outputs
- building customized fact-checking systems
- benchmarking model factuality
- checking claims in articles or generated text

Takeaway:

> OpenFactCheck helps verify whether AI-generated claims are supported by reliable evidence.

---

## LM-Polygraph

**LM-Polygraph** is a tool/library used for **uncertainty estimation**, or detecting hallucination risk in language models.

It tries to detect when an LLM may be unsure or unreliable.

Simple meaning:

> It helps identify answers that may have a higher risk of hallucination.

### Important clarification

LM-Polygraph does not simply say:

```text
This answer is 100% false.
```

Instead, it estimates uncertainty.

High uncertainty may mean:

```text
This answer should be checked more carefully.
```

### Example

AI answer:

```text
The exact law was passed in 2017 by this specific committee.
```

LM-Polygraph may detect high uncertainty.

Then the system can respond more carefully:

```text
I am not fully certain. This should be verified from an official source.
```

### Why it matters

LLMs can sound confident even when wrong. Uncertainty estimation helps systems decide when to:

- answer normally
- warn the user
- retrieve more sources
- ask a human
- refuse to make a confident claim

Takeaway:

> LM-Polygraph helps AI systems know when the model may not be reliable.

---

## LLM-DetectAIve

**LLM-DetectAIve** is a tool used for **machine-generated text detection**.

It can help detect whether text was:

- human-written
- AI-generated
- AI-generated then humanized
- human-written then AI-polished

This is probably the tool related to your note about:

```text
detect model rephrasing
```
### Example

A text may look human-written, but it could be:

```text
AI-generated
AI-rephrased
AI-polished
AI-humanized
```

LLM-DetectAIve tries to classify the origin of the text more precisely.

### Why it matters

AI text detection is useful in:

- journalism
- education
- plagiarism checking
- misinformation detection
- content moderation
- research integrity

Takeaway:

> LLM-DetectAIve helps detect whether text was generated, polished, or rewritten by AI.

---

## Open and Specialized LLMs

Although your short note for this section focused on Arabic, factuality, safety, and hallucination, the talk title also included **open** and **specialized** LLMs.

### Open LLMs

An open LLM may release model weights, code, training data, or methodology.

Different levels:

```text
Closed model: only accessible through API
Open-weight model: weights are available
Fully open model: weights, data, code, and training details are transparent
```

### Specialized LLMs

A specialized LLM is adapted for a specific domain.

Examples:

* medical LLM
* legal LLM
* finance LLM
* journalism fact-checking LLM
* education LLM

Beginner takeaway:

> The future may not be one model for everything, but many specialized models for different languages, industries, and safety needs.

---

# 3. Dr. Phong Nguyen — From Curious to Native: The Framework for Human-led Enterprise AI

**Speaker:** Dr. Phong Nguyen
**Role:** CTO, FPT Corporation; Former Chief AI Officer, FPT Software
**Session type:** Spotlight Talk

---

## CASAN 
**CASAN** is FPT's five-level AI transformation framework for helping enterprises move from early AI experimentation to AI-native operations.

CASAN stands for:

- **Curious**: individuals or teams are exploring AI.
- **Augmented**: AI is used to improve personal productivity.
- **Standard**: AI adoption becomes governed with standards, data practices, and architecture.
- **Automatic**: AI automates workflows and creates measurable business value.
- **Native**: AI becomes a core capability of the organization.

In simple terms, CASAN helps companies understand their AI maturity level and plan how to move from using AI casually to integrating AI deeply into business operations.

---

## Harness Engineering
The evolution of prompting can be basically divided into 3 methods
```text
Standard Prompting -> Context Engineering -> Harness Engineering
```

### 1. Standard Prompting

**Standard prompting** means giving the AI a direct instruction.

Example:

```text
Explain what an AI agent is.
```

Another example:

```text
Summarize this article in 5 bullet points.
```

The main question is:

```text
What should I ask the model?
```

#### Common prompting techniques

Standard prompting can include:

- Direct prompting
- Role prompting
- Few-shot prompting
- Chain-of-thought prompting
- Structured output prompting

Example of role prompting:

```text
You are an AI tutor. Explain vector search to a beginner.
```

Example of structured output prompting:

```text
Explain this topic using:
1. Definition
2. Example
3. Beginner takeaway
```

#### Takeaway

> Standard prompting is about writing better instructions so the AI gives a better answer.


### 2. Context Engineering

**Context engineering** means designing what information the model receives before answering.

Instead of only asking:

```text
What should I type?
```

Context engineering asks:

```text
What information should the model see?
```

The model may need extra context such as:

- User question
- Previous conversation
- Retrieved documents
- Examples
- User preferences
- Company rules
- Database results
- Tool outputs
- Formatting requirements

#### Example

Bad prompt:

```text
Answer the customer.
```

Better context engineering:

```text
User question:
Can I get a refund?

Relevant policy:
Refunds are allowed within 7 days if the product is unused.

Order status:
The customer bought the product 3 days ago.

Instruction:
Answer politely and only use the policy above.
```

Now the AI has enough context to answer correctly.

### Context engineering and RAG

Context engineering is very important in **RAG**, or **Retrieval-Augmented Generation**.

RAG flow:

```text
User asks a question
→ system searches relevant documents
→ documents are added to the model context
→ model answers using those documents
```

Example:

```text
User: What is our company leave policy?

System:
1. Searches HR documents
2. Finds the leave policy
3. Gives the policy to the AI
4. AI answers based on the policy
```

#### Takeaway

> Context engineering is about giving the AI the right information, not just giving it a better instruction.


### 3. Harness Engineering

**Harness engineering** means building the full system around the AI model. Agentic AI often requires Harness Engineering

Simple formula:

```text
AI product = model + context + tools + safety + evaluation + monitoring + user interface
```

The main question is:

```text
How do we make the AI system reliable, safe, testable, and useful in real life?
```

### What can be inside an AI harness?

An AI harness may include:

- Prompt templates
- Context retrieval
- Vector search
- Tool calling
- Memory
- API connections
- Logging
- Monitoring
- Evaluation
- Safety filters
- Confidence thresholds
- Human approval
- Fallback behavior
- Security checks

#### Example

Task:

```text
User asks the AI agent to send an email.
```

A safe AI harness may work like this:

```text
1. Understand the user request
2. Find the correct contact
3. Draft the email
4. Check for sensitive data
5. Ask the user for approval
6. Send only after confirmation
7. Log the action
```

Without a harness, the AI may act too freely and make mistakes.

#### Takeaway

> Harness engineering is about building a safe and reliable AI system around the model.

---

# 4. Dr. Myungsub Choi — From Focusing Lenses to Focusing Risks: An Engineer's Journey into Agentic AI Safety

**Speaker:** Dr. Myungsub Choi
**Role:** Head of Research, Tynapse; Former Samsung AI & Google
**Session type:** Lightning Talk

---

## What is Agentic AI?

Agentic AI often requires Harness Engineering

An AI agent can:

* understand a goal
* plan steps
* use tools
* call APIs
* search documents
* remember context
* take actions
* evaluate results

Example:

```text
Goal: Prepare a report.
Agent: searches files, summarizes data, creates charts, writes report, and sends draft.
```

Beginner takeaway:

> The more AI can act, the more safety controls it needs.

---

## Confidence Threshold

A confidence threshold is a minimum confidence level required before AI answers or acts.

Example:

```text
Confidence > 90% → answer automatically
Confidence 60–90% → answer with caution
Confidence < 60% → ask human or say unsure
```

Why it matters:

```text
If AI is uncertain, it should not take risky actions automatically.
```

Useful in:

* medicine
* finance
* law
* fraud detection
* cybersecurity
* autonomous systems

Takeaway:

> Safe AI should know when it does not know.

---

## Agentic AI Risks

Common risks include:

| Risk                   | Example                                    |
| ---------------------- | ------------------------------------------ |
| Hallucination          | Agent acts based on false information      |
| Tool misuse            | Agent calls the wrong API                  |
| Privacy leakage        | Agent exposes confidential data            |
| Prompt injection       | Malicious text tricks the agent            |
| Lack of explainability | User cannot understand why the agent acted |
| Over-automation        | Human trusts AI too much                   |

---

## Guardrails and Human-in-the-Loop

Agentic AI needs guardrails.

Examples:

* ask before sending emails
* ask before making payments
* block dangerous tool calls
* hide private data
* require review for high-risk decisions
* log actions for audit

Human-in-the-loop means a human stays involved in important decisions.

Example:

```text
AI detects possible fraud.
Human analyst reviews before account suspension.
```

Beginner takeaway:

> AI agents should assist humans, not act with unlimited freedom.

---

# 5. Dr. Noriyuki Kojima — Pushing the Boundaries of Real-Time Speech AI for East Asia

**Speaker:** Dr. Noriyuki Kojima
**Role:** Co-founder & CEO, Kotoba Technologies; AI for Real-Time Speech & Language
**Session type:** Lightning Talk

---

## ASR: Automatic Speech Recognition

**ASR** means Automatic Speech Recognition.

It converts speech into text.

Example:

```text
Audio: "Hello, how are you?"
ASR output: "Hello, how are you?"
```

ASR is used in:

* voice assistants
* meeting transcription
* subtitles
* call centers
* translation systems
* voice agents

Takeaway:

> ASR allows computers to listen and convert spoken words into text.

---

## TTS: Text-to-Speech

**TTS** means Text-to-Speech.

It converts text into spoken audio.

Example:

```text
Text: "Welcome to the seminar."
TTS output: spoken voice
```

TTS is used in:

* audiobooks
* navigation apps
* accessibility tools
* language learning
* customer service bots
* AI voice agents

Beginner takeaway:

> TTS allows computers to speak naturally to users.

---

## Streamable ASR and TTS

Streamable speech AI means the system works in real time instead of waiting for the full sentence or full response.

### Streamable ASR

The system transcribes speech while the person is still speaking.

### Streamable TTS

The system starts speaking before the full response is completely generated.

Comparison:

```text
Non-streaming:
User speaks → wait → full transcript → full response → audio

Streaming:
User speaks → partial transcript appears → AI responds faster → audio starts sooner
```

Beginner takeaway:

> Streaming is important because real conversations need low latency.

---

## Speech-to-Speech Translation

Speech-to-speech translation means:

```text
Speaker talks in Language A
→ AI understands speech
→ AI translates meaning
→ AI speaks in Language B
```

Example:

```text
Japanese speech → English speech
Vietnamese speech → Korean speech
```

This usually combines:

```text
ASR + translation model + TTS
```

More advanced systems may perform this more directly and with lower latency.

---

## 5.6 Why East Asian Speech AI is Challenging

East Asian languages can be difficult for speech AI because of:

* different writing systems
* tonal languages
* regional accents
* honorifics
* context-dependent meaning
* fast speech
* code-switching between languages
* limited high-quality speech datasets for some languages

For Vietnamese specifically, speech AI must handle:

* tones
* regional accents
* informal speech
* proper names
* mixed English-Vietnamese phrases

Takeaway:

> Real-time speech AI is not only about recognition accuracy. It also needs speed, naturalness, cultural understanding, and low latency.

---

## Cloud and Edge Speech AI

Speech AI can run in the cloud or on the device.

| Type      | Meaning                | Benefit                 | Challenge                        |
| --------- | ---------------------- | ----------------------- | -------------------------------- |
| **Cloud** | Runs on remote servers | More powerful models    | Needs internet; privacy concerns |
| **Edge**  | Runs on local device   | Faster and more private | Limited compute power            |

Example:

```text
Cloud ASR: audio is sent to server for transcription
Edge ASR: phone processes speech locally
```

---

# Final Summary

The 5 morning talks can be connected like this:

```text
1. Dr. Ed H. Chi:
AI is moving toward personalized universal agents.

2. Prof. Preslav Nakov:
LLMs must become language-specific, factual, safe, open, and specialized.

3. Dr. Phong Nguyen:
Enterprises need human-led AI maturity, not random AI experiments.

4. Dr. Myungsub Choi:
Agentic AI needs safety, guardrails, confidence thresholds, and human oversight.

5. Dr. Noriyuki Kojima:
Real-time speech AI enables natural voice-based AI interaction.
```

One-sentence summary:

> Modern AI is becoming more agentic, personalized, localized, enterprise-ready, and voice-based, but it must be designed with truth, safety, transparency, and human control in mind.
