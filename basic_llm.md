# Basic LLM Flow

This README explains the basic flow of how a Large Language Model (LLM) processes a user's prompt and generates an answer.

---

## 1. Big Picture

A Large Language Model does not understand text the same way humans do.

At a basic level, it works like this:

```text
User prompt
→ tokenize text into tokens
→ convert tokens into embedding vectors
→ add positional information
→ process through transformer layers
→ calculate probability of the next token
→ select/generate next token
→ append generated token to context
→ repeat next-token prediction
→ final response
```

Super simple version:

```text
Text
→ tokens
→ token vectors
→ transformer understands context
→ predicts next token
→ repeats
→ answer
```

---

## 2. User Prompt

The process starts when the user gives a prompt.

Example:

```text
Explain what an AI agent is.
```

This prompt is raw text.

The model cannot directly process human text as words. First, the text must be converted into a machine-readable format.

---

## 3. Tokenization

### What is tokenization?

**Tokenization** means breaking text into smaller pieces called **tokens**.

A token can be:

- a full word
- part of a word
- punctuation
- a symbol
- a space-connected word piece

Example:

```text
"Explain what an AI agent is."
→ ["Explain", " what", " an", " AI", " agent", " is", "."]
```

Another example:

```text
"unbelievable"
→ ["un", "believ", "able"]
```

Tokens are important because LLMs process text as tokens, not as full sentences.

Beginner takeaway:

> Tokenization turns human text into smaller units that the model can process.

---

## 4. Token Embeddings

After tokenization, each token is converted into a vector.

A **vector** is a list of numbers.

Example:

```text
"AI"     → [0.12, -0.45, 0.88, ...]
"agent"  → [0.33, 0.09, -0.21, ...]
```

So the full sentence becomes a sequence of token vectors:

```text
[token vector 1, token vector 2, token vector 3, ...]
```

Important distinction:

```text
LLM processing:
each token → one embedding vector

Vector search:
whole sentence/document → one embedding vector
```

Beginner takeaway:

> In an LLM, each token becomes a numerical vector before going into the model.

---

## 5. Positional Information

LLMs also need to know the order of tokens.

Why?

Because word order changes meaning.

Example:

```text
Dog bites man.
```

is different from:

```text
Man bites dog.
```

The words are similar, but the order changes the meaning.

So the model adds positional information:

```text
token embedding + position information
```

Beginner takeaway:

> Positional information helps the model understand word order.

---

## 6. Transformer Layers

The token vectors are processed through many **transformer layers**.

The transformer is the core architecture behind most modern LLMs.

Inside transformer layers, one of the most important mechanisms is **attention**.

---

## 7. Attention Mechanism

### What is attention?

**Attention** helps the model decide which tokens are important to each other.

Example:

```text
The cat sat on the mat because it was tired.
```

The model uses attention to understand that:

```text
"it" probably refers to "the cat"
```

Attention helps the model understand:

- grammar
- context
- relationships between words
- meaning
- references
- instruction following

Beginner takeaway:

> Attention helps the model connect related words and understand context.

---

## 8. Predicting the Next Token

After processing the prompt, the LLM predicts the next token.

It creates a probability distribution over possible next tokens.

Example prompt:

```text
The capital of France is
```

Possible next tokens:

```text
Paris   → 92%
London  → 3%
Berlin  → 2%
Rome    → 1%
Other   → 2%
```

The model then selects one token.

Example output:

```text
Paris
```

Beginner takeaway:

> LLMs generate text by predicting the most likely next token.

---

## 9. Repeating the Process

The model does not generate the whole answer at once.

It generates one token, then another, then another.

Example:

```text
Prompt: The capital of France is
Generated token 1: Paris
Generated token 2: .
```

The generated token is added back into the context.

Then the model predicts the next token again.

Flow:

```text
Prompt
→ predict token 1
→ add token 1 to context
→ predict token 2
→ add token 2 to context
→ repeat
→ final answer
```

Beginner takeaway:

> LLM output is generated step by step, one token at a time.

---

## 10. Final Response

After enough tokens are generated, the model stops.

It may stop because:

- it reaches an end token
- it reaches a maximum output length
- it completes the answer
- the system tells it to stop

Final answer example:

```text
An AI agent is an AI system that can understand a goal, plan steps, use tools, and take actions to help complete a task.
```

---

## 11. Correct Basic LLM Flow

Use this version:

```text
receive user's prompt
→ break text into tokens
→ turn each token into an embedding vector
→ add positional information
→ pass through transformer layers
→ use learned statistical patterns to predict the next token
→ output one token
→ append that token to the context
→ repeat until the answer is complete
```

---

## 12. What Does “Statistical Prediction” Mean?

LLMs are trained on huge amounts of text.

During training, they learn patterns such as:

```text
which words often appear together
how grammar works
how questions are answered
how code is structured
how explanations are written
how reasoning patterns usually look
```

When generating an answer, the model uses these learned patterns to predict likely next tokens.

Important note:

> The model is not simply copying from memory. It is using learned patterns to generate likely text.

---

## 13. Does a Basic LLM Search the Internet?

No.

A basic LLM does not automatically search the internet, open files, or access databases.

Basic LLM flow:

```text
prompt → model → generated answer
```

If the system has search or tools, then it becomes a larger AI system.

---

## 14. LLM vs RAG vs Agentic AI

### Basic LLM

```text
User prompt
→ LLM
→ generated answer
```

The model answers from its trained knowledge and current context.

### RAG System

RAG means **Retrieval-Augmented Generation**.

```text
User prompt
→ search relevant documents
→ add documents to context
→ LLM generates answer
```

RAG is useful when the answer should be based on specific documents or updated information.

### Agentic AI System

Agentic AI can plan and use tools.

```text
User prompt
→ agent plans steps
→ uses tools/search/API/database
→ checks results
→ responds or acts
```

Example:

```text
User: Schedule a meeting with Alex.

Agent:
1. Checks calendar
2. Finds Alex's contact
3. Suggests time
4. Creates calendar event after approval
```

---

## 15. Context Window

A **context window** is the maximum number of tokens the model can process at one time.

It includes:

- system instructions
- conversation history
- current user prompt
- retrieved documents
- tool outputs
- generated response

Simple explanation:

```text
Context window = what the model can see right now
```

When the context window is full, the system may:

- remove older messages
- summarize old content
- retrieve only relevant information
- compress context
- keep only recent conversation

Beginner takeaway:

> Context window works like short-term working memory, not permanent long-term memory.

---

## 16. Common Misunderstanding

Incorrect flow:

```text
User prompt
→ break into chunks
→ embed whole prompt to one vector
→ transformer
→ output
```

Better flow:

```text
User prompt
→ tokenize into tokens
→ each token becomes an embedding vector
→ transformer layers process token vectors
→ model predicts next token
→ repeat
```

The difference is important.

In vector search, a whole sentence or document may become one vector.

In LLM generation, each token becomes a vector and is processed in sequence.

---

## 17. Simple Analogy

Imagine the LLM is writing one word at a time.

It reads the sentence so far:

```text
The capital of France is
```

Then it asks:

```text
What word is most likely next?
```

It chooses:

```text
Paris
```

Then it reads:

```text
The capital of France is Paris
```

Then it predicts:

```text
.
```

This continues until the answer is complete.

---

## 18. Why This Matters Before Learning AI Agents

Understanding the basic LLM flow helps you understand more advanced topics:

| Topic | Why LLM flow matters |
|---|---|
| Prompting | The prompt affects the next-token prediction |
| Context engineering | Better context helps the model predict better answers |
| RAG | Retrieved documents are added into the context |
| Hallucination | The model may predict likely text that is not factual |
| Safety | Guardrails control what the model should or should not output |
| Agentic AI | The LLM becomes part of a larger system that can use tools |
| Speech AI | ASR converts speech to text before the LLM; TTS converts output text to speech |

---

## 19. One-Sentence Summary

> A Large Language Model receives text, breaks it into tokens, converts tokens into vectors, processes them through transformer layers, predicts the next token using learned statistical patterns, and repeats this process until it produces a final answer.

---

## 20. Quick Cheat Sheet

```text
Token = small piece of text
Embedding = numerical vector representation of a token
Transformer = model architecture that processes token relationships
Attention = mechanism that helps the model focus on relevant tokens
Next-token prediction = how LLMs generate text
Context window = maximum tokens the model can see at one time
RAG = search documents first, then generate answer
Agentic AI = AI that can plan, use tools, and take actions
```
