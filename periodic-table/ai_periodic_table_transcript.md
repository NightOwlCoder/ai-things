# AI Periodic Table - Video Transcript

**Source:** [IBM Technology - AI Periodic Table Explained: Mapping LLMs, RAG & AI Agent Frameworks](https://www.youtube.com/watch?v=ESBMgZHzfG0)

---

## Introduction

Does the world of AI feel a bit like this to you? A thousand terms all flying around. Everyone's talking about agents and RAG and embeddings and guardrails, and you're just kind of supposed to know how it all fits together.

Well, how about we put a structure to all this chaos? What if we could organize AI like chemistry organizes the elements into families and periods and predictable reactions? Well, welcome to the **AI Periodic Table**.

> **Disclaimer:** There is no official AI periodic table like there is in chemistry. This is my take on what the structure could look like. But once you understand it, you can basically decode any AI architecture, any product demo, any event pitch. You'll see which elements they're using, how they connect, and then maybe even what might be missing.

---

## The Table Structure

### Rows (Periods)
| Row | Name | Description |
|-----|------|-------------|
| **Row 1** | **Primitives** | Atomic building blocks - can't be broken down further |
| **Row 2** | **Compositions** | Combinations of primitives working together |
| **Row 3** | **Deployment** | Putting things into production |
| **Row 4** | **Emerging** | Rapidly evolving, cutting-edge patterns |

### Groups (Families)
| Group | Name | Description |
|-------|------|-------------|
| **G1** | **Reactive** | Changes produce completely different outputs |
| **G2** | **Retrieval** | About search, storage, and memory |
| **G3** | **Orchestration** | Combining multiple elements together |
| **G4** | **Validation** | Safety, testing, and verification |
| **G5** | **Models** | Stable foundational capabilities (like noble gases) |

---

## The Elements

### Row 1: Primitives

#### Pr - Prompts (G1: Reactive)
Instructions you give to an AI, like "write me an email" or "summarize this document" or "explain quantum physics."

**Why Reactive?** You change one word in your prompt - you get a completely different output.

#### Em - Embeddings (G2: Retrieval)
Numerical representations of meaning. You take some text, like "the cat sat on the mat," and turn it into a list of numbers that capture its meaning. **Similar meanings get similar numbers.**

If you've heard of vector databases or semantic search, you've bumped into embeddings.

#### Lg - Large Language Models (G5: Models)
The LLM - like ChatGPT, Claude, and IBM Granite. These are the stable foundational capabilities that everything else reacts around.

> **Note:** Row 1 only has three elements (Prompts, Embeddings, LLMs) because in some ways, **everything else in AI is built from combining these primitives**.

---

### Row 2: Compositions

#### Fc - Function Calling (G1: Reactive)
When your LLM calls a tool before giving an answer. Perhaps it invokes an API. If you ask a model "what's the weather," the model calls a weather API to give you real data.

#### Vx - Vector Databases (G2: Retrieval)
Data stores optimized for semantic search. You can store millions of embeddings and query them to find the most relevant ones. **Storage for semantic search.**

#### Rg - RAG (G3: Orchestration)
**Retrieval Augmented Generation** - one of the most powerful patterns:
1. You have a question
2. The system **retrieves** relevant context from your documents using embeddings and vector databases
3. It **augments** the prompt with that context
4. The LLM **generates** an answer based on what it retrieved

> **Note:** There's no primitive in the orchestration column because you can't orchestrate one thing. Orchestration only emerges when combining multiple pieces.

#### Gr - Guardrails (G4: Validation)
Runtime safety filters, schema validation. Making sure the AI doesn't say something it shouldn't or output garbage.

#### Mm - Multi-Modal Models (G5: Models)
LLMs that can process images and audio as well as text.

---

### Row 3: Deployment

#### Ag - Agents (G1: Reactive)
Use **think-act-observe loops**. The AI:
1. **Plans** what to do
2. **Takes action** (maybe using function calls)
3. **Observes** the result
4. **Keeps going** until it reaches a goal

**The reactive family progression:** Prompt → Function → Agent (or: Control → Action → Autonomy)

#### Ft - Fine Tuning (G2: Retrieval)
Take a base model and adapt it - train it on your specific data, domain, or use case. Like fine tuning on medical papers or your company's codebase.

**Why Retrieval?** Fine tuning is adaptation - baking memory directly into the model's weights.

**Three timescales of memory in G2:**
- Embeddings: encode meaning
- Vector databases: store for search
- Fine tuning: store in parameters

#### Fw - Framework (G3: Orchestration)
Platforms like LangChain that tie everything together to build and deploy AI systems.

#### Re - Red Teaming (G4: Validation)
Adversarial testing - trying to break the AI. Jailbreaks, prompt injection, data exfiltration.

#### Sm - Small Models (G5: Models)
Distilled, specialized models. Fast, cheap, maybe run on your phone.

---

### Row 4: Emerging

#### Ma - Multi-Agent (G1: Reactive)
Not one AI - **multiple AIs working together**. Debating, collaborating, specializing. Maybe one agent does research, one does writing, one critiques, and they coordinate to solve complex problems.

**The reactive family taken to the extreme.**

#### Sy - Synthetic Data (G2: Retrieval)
Using AI to generate training data for AI. If you can't get enough real examples, you can generate synthetic ones. As we hit limits of available data, more is being done with synthetic data.

#### [Gap] - ??? (G3: Orchestration)
*No clear emerging orchestration paradigm yet.* What goes beyond frameworks? **This is an open question.**

#### In - Interpretability (G4: Validation)
Understanding **why** a model does what it does. Peeking inside the black box, finding neurons responsible for specific behaviors. **Frontier safety work.**

#### Th - Thinking Models (G5: Models)
Models that don't answer immediately - they spend time **reasoning**. Chain of thought built directly into the architecture. "Test time compute scaling." **The smartest models today tend to be thinking models.**

---

## AI Reactions (How Elements Combine)

### Reaction 1: Production RAG Chatbot
*Building a chatbot that knows your company's documentation*

```
Em (Embeddings) → Vx (Vector DB) → Rg (RAG) → Pr (Prompt) → Lg (LLM)
                                                          ↓
                                      + Gr (Guardrails) wrapping the whole thing
```

1. **Em:** Take your documents and turn them into vectors
2. **Vx:** Store them in vector databases
3. **Rg:** When user asks a question, query the vector DB and retrieve relevant chunks
4. **Pr:** Those chunks augment the prompt
5. **Lg:** Send to LLM to generate an answer grounded in your data
6. **Gr:** Wrap in safety filters to prevent leaking sensitive information

### Reaction 2: Agentic Loop
*"Book me a flight to Tokyo next month under $800"*

```
         ┌─────────────┐
         │             │
         ↓             │
Ag (Agent) ←→ Fc (Function Calling) → [External APIs]
         │             │
         └─────────────┘
              ↓
        Fw (Framework)
```

1. **Ag:** Agent takes the goal and breaks it down (search flights, check calendar, compare prices, book)
2. **Fc:** Function calling invokes external tools (flight APIs, calendar APIs, payment systems)
3. Agent observes results and decides next action
4. **Loop:** Think → Act → Observe → Think → Act → Observe
5. **Fw:** Framework provides the plumbing for this loop

### Other Reactions
- **AI Image Generators:** Prompt → Multi-modal model → Image output
- **Code Assistants:** Fine-tuned on code → Prompt with context → LLM → Code completions

---

## Your Challenge

Next time somebody pitches you a fancy new AI feature, product, or startup idea, **map it to this table:**

1. What elements are they using?
2. What reactions are they running?
3. Are they missing a safety element?
4. Are they over-engineering the orchestration?
5. Are they using a thinking model when a small model would do the job?

**It's all right here - a way to categorize and link all of these AI terms.**

---

## Quick Reference Table

| Symbol | Name | Row | Group | Description |
|--------|------|-----|-------|-------------|
| **Pr** | Prompts | 1 | G1 | Instructions to AI |
| **Em** | Embeddings | 1 | G2 | Numerical meaning representations |
| **Lg** | LLM | 1 | G5 | Large Language Models |
| **Fc** | Function Call | 2 | G1 | Tool invocation |
| **Vx** | Vector DB | 2 | G2 | Semantic search storage |
| **Rg** | RAG | 2 | G3 | Retrieval Augmented Generation |
| **Gr** | Guardrails | 2 | G4 | Safety filters |
| **Mm** | Multi-modal | 2 | G5 | Image/audio/text models |
| **Ag** | Agent | 3 | G1 | Think-act-observe loops |
| **Ft** | Fine Tune | 3 | G2 | Model adaptation |
| **Fw** | Framework | 3 | G3 | Deployment platforms |
| **Re** | Red Team | 3 | G4 | Adversarial testing |
| **Sm** | Small | 3 | G5 | Distilled models |
| **Ma** | Multi-Agent | 4 | G1 | Multiple AIs collaborating |
| **Sy** | Synthetic | 4 | G2 | AI-generated training data |
| **In** | Interpretability | 4 | G4 | Understanding model behavior |
| **Th** | Thinking | 4 | G5 | Reasoning models |
