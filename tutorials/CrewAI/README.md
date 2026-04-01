# Learn CrewAI in 60 Minutes
## Structured Multi Agent AI Systems with Planning, Execution, and Critique

---

# 1. Goal

This tutorial provides everything needed to become familiar with CrewAI in 60 minutes.  This folder also contains the setup for running AutoGen tutorials within a containerized environment.

CrewAI is a framework for building **collaborative multiagent AI systems** where agents with specialized roles plan, execute, critique, and refine tasks iteratively.

By the end, you will move from:

Single LLM prompts → Structured autonomous AI systems

---

# 2. What This Tutorial Provides

## Hands on Experience

- Working Docker container
- Reproducible notebook (`tutorial_crewai.ipynb`)
- End to end runnable example
- Multiagent planning loop

## Conceptual Understanding

You will understand:

- What CrewAI is
- What problem it solves
- Native API structure
- When to use multiagent systems
- Alternatives and trade-offs

## Practical Application

You can:

- Build a Planner -> Worker -> Critic loop
- Execute notebook code through agents
- Implement retry logic
- Track explicit state

## Reproducibility

- Notebook runs end to end
- Dependencies are managed via the container environment

---

# 3. Structure

## Quick Start
- From the root of the repository, change your directory to the CrewAI tutorial
  folder:
  ```bash
  > cd tutorials/CrewAI
  ```

- Once the location has been changed to the repo run the command to build the
  image to run dockers:
  ```bash
  > ./docker_build.sh
  ```

- Once the docker has been built you can then go ahead and run the container and
  launch jupyter notebook using the created image using the command:
  ```bash
  > ./docker_jupyter.sh
  ```

- Once the `./docker_jupyter.sh` script is running, follow this sequence to
  explore the tutorials:
  1. **`tutorial_crewai.ipynb`**: Start here to master the fundamental commands and more about creating agents, defining tasks, running a crew, how to give an agent tools and how an agent calls Python functions.
  2. **`Autogen.example.ipynb`**: Proceed to this notebook to explore more
     complex, multi-agent scenarios and advanced problem-solving techniques.

- For more informations on the Docker build system refer to [Project template
  readme](https://github.com/gpsaggese/umd_classes/blob/master/class_project/project_template/README.md)


# 5. What is CrewAI?

CrewAI is a Python framework for building structured multi agent AI systems.

Instead of:
 
```bash
prompt -> response
```

CrewAI enables:

```bash
Planner -> Worker -> Critic -> Update -> Repeat
```
It supports role specialization, task delegation, tool usage, explicit coordination, iterative refinement

# 6. What Problem Does It Solve?

Single LLM calls lack iterative correction, error recovery, explicit state, structured decomposition, and deterministic ochestration.

CrewAI introduces modular agents, explicit tasks, structured workflows, and observable state transitions.

# 7. Native API Overview
Core abstractions: 
Agent: 

```bash
Agent(
    role="Planner",
    goal="Plan next notebook step",
    backstory="Expert AI planner"
)
```

Task:

```bash
Task(
    description="Execute notebook cell",
    agent=worker
)
```

Crew:

```bash
Crew(
    agents=[planner, worker, critic],
    tasks=[task]
)
```

# 8. State Management

State includes: Objective, Execution history, Notebook outputs, Error traces, Completion flag

Explicit state ensures: Reproducibility, Debuggability, Deterministic behavior, Observability

Avoid hidden memory.