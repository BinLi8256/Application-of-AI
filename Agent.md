### 1. LLM vs. AI Agent

#### 1.1 Introduction
People often use the terms LLM and AI Agent interchangeably, but they are not the same thing. 

An **LLM** is the reasoning and languag-generation component. An **AI Gent** is a complete system that uses an LLM together with tools, memory, and planning mechanisms to achieve a goal.

A useful relationship is:
``
AI Agent = LLM + Tools + Memory + Planning + Action Loop
``

#### 1.2 What is an LLM?
A Large Language Model (LLM) is a machine learning model trained to predict the next token(word or subword) in a sequence. It can understand natual language, produce human-like responses, perform many reasoning tasks, contain knowledge learned during training, does not inherently remember previous sessions.

It cannot inherently interact with the outside world and cannot perform actions itself despite it can generate instructions. For example, a pure LLM cannot actually check the current weather. A pure LLM can explain Python code but cannot execute it.

#### 1.3 What is an AI Agent?

An AI Agent is a system designed to accomplish goals by repeatedly:
  - thinking
  - taking aactions
  - observing results
  - adjusting its plan
Unlike an LLM, an agent operates in a feedback loop.

#### 1.4 Core Components of an Agent
  - LLM (The Brain)
    The LLM provides reasoning, planning, decision making, and language understanding. Without the LLM, the agent would not know what to do
  - Tools
    Tools provide capabilities that the LLM itself lacks. For example, web search, calculator, email API, etc.
  - Memory
    Memory allows the agent to retain information. Without memory, every conversation starts from scratch. With memory, the agent can personalize decisions.
  - Planning
    Planning decomposes large goals into smaller tasks.
  - Action Loop
    This is what distinguishes agents from simple chatbots. The loop of LLM is Input -> LLM -> Output. The loop of Agent is
    ``
    Input -> think -> act -> observe -> think -> act -> observe -> ... -> think -> act -> observe -> Output
    ``

### 2. ReAct: Reason + Act

**ReAct** is one of the most influential AI agent frameworks. The core idea is simple: Instead of only reasoing (**chain-of-thought) or only acting (**tool-use**), let the model alternate between **Reasoning** and **Acting**.

#### 2.1 Why ReAct Was Introduced
Before ReAct, there are mainly two approaches:
  - Chain-of-Thought (Reasoning Only)
    The model reasons step-by-step. However, it has no verification, no access to current information and may hallucinate.
  - Tool Use (Action Only)
    it does not plan nor reason about what information is needed.

ReAct combines both. The though-action-observation loop continues until the model has enough information.

### Pseudo Code

````
while not solved:
  thought = LLM(
  question,
  previous_observations
  )

  action = choose_tool(thought)

  observation = execute(action)

  add_to_context(
    thought,
    action,
    observation
  )

return fianl_answer
````




