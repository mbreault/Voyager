# Voyager: Purpose and Goals

Voyager is an innovative open-ended embodied agent that leverages Large Language Models (LLMs) to operate within the Minecraft environment. Its primary purpose is to achieve **lifelong learning** and **autonomous discovery** without requiring human intervention.

## Key Objectives:

*   **Continuous Exploration:** Voyager is designed to persistently explore its environment, seeking out new areas, resources, and challenges within the Minecraft world.
*   **Skill Acquisition:** A core goal is for Voyager to autonomously acquire a diverse set of skills. These skills are represented as executable code, allowing the agent to perform complex behaviors.
*   **Novel Discoveries:** Beyond predefined tasks, Voyager aims to make novel discoveries, effectively learning and adapting to new situations and opportunities it encounters.
*   **Autonomous Operation:** Voyager is built to function independently, making decisions and learning from its experiences without direct human guidance.

## What Voyager Does:

Voyager interacts with the Minecraft game environment and uses an LLM (specifically GPT-4 via blackbox queries) to:

1.  **Understand and Decompose Tasks:** It can break down high-level goals into smaller, manageable steps.
2.  **Generate Code for Skills:** It writes new code snippets (skills) to accomplish these steps.
3.  **Learn from Experience:** It incorporates feedback from the environment, execution errors, and self-verification to refine its skills and improve its programs.
4.  **Build a Knowledge Base:** It maintains an ever-growing library of learned skills that can be retrieved and reused for future tasks.

In essence, Voyager demonstrates a strong capability for in-context lifelong learning, becoming increasingly proficient at playing Minecraft by obtaining more unique items, traveling greater distances, and achieving key game milestones significantly faster than previous state-of-the-art methods. It can also generalize its learned skills to new Minecraft worlds and solve novel tasks from scratch.
