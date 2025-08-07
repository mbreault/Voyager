# Voyager Architecture Overview

Voyager's architecture is designed to enable an autonomous agent to continuously learn and interact within the Minecraft environment. It comprises several key modules that work together to achieve its goals of exploration, skill acquisition, and discovery.

## Core Components:

1.  **Agent Core (`voyager/agents/`)**: This is the brain of Voyager. It includes sub-modules for:
    *   **Curriculum Generation (`curriculum.py`):** Dynamically creates tasks for the agent to pursue, aiming to maximize exploration and learning.
    *   **Skill Management (`skill.py`):** Handles the storage, retrieval, and refinement of learned skills. Skills are typically represented as executable code (JavaScript for Minecraft interaction).
    *   **Action Generation (`action.py`):** Determines the next actions for the agent to take based on the current task and learned skills. It interacts with the LLM to generate or select appropriate code.
    *   **Critic (`critic.py`):** Evaluates the success of actions and provides feedback for learning and refinement. This often involves self-verification and analysis of environmental feedback.

2.  **Skill Library (`skill_library/`)**: A persistent repository of all the skills Voyager has learned. Each skill is typically a piece of code that accomplishes a specific task in Minecraft. This library grows over time as the agent acquires new abilities.

3.  **Iterative Prompting Mechanism (`voyager/prompts/`)**: Voyager interacts with a Large Language Model (LLM, e.g., GPT-4) through a sophisticated prompting system. This involves:
    *   **Task Decomposition:** Breaking down complex goals into simpler sub-tasks.
    *   **Code Generation:** Prompting the LLM to write or modify JavaScript code for skills.
    *   **Feedback Integration:** Incorporating environmental feedback, execution errors, and self-critiques into prompts to refine and improve generated code and plans.
    The `voyager/prompts/` directory contains various templates used for these interactions.

4.  **Environment Interaction Layer (`voyager/env/` and `voyager/control_primitives/`)**:
    *   **Minecraft Environment Bridge (`voyager/env/bridge.py`, `voyager/env/mineflayer/`):** Manages the connection and communication with the Minecraft game. It uses Mineflayer, a JavaScript library, to control the Minecraft character programmatically.
    *   **Control Primitives (`voyager/control_primitives/`):** A set of fundamental, low-level JavaScript functions that provide basic actions within Minecraft (e.g., `mineBlock.js`, `craftItem.js`, `placeItem.js`). These primitives are the building blocks for more complex skills.

5.  **Main Orchestrator (`voyager/voyager.py`)**: This is the entry point and central coordinator for the Voyager agent. It initializes all components and manages the main learning loop or task execution process.

## Data Flow and Learning Loop:

1.  The **Automatic Curriculum** proposes a new task or goal.
2.  The **Agent** (using its `action.py` and `skill.py` components) attempts to achieve this task. This may involve:
    *   Retrieving an existing skill from the **Skill Library**.
    *   If no suitable skill exists, using the **Iterative Prompting Mechanism** to ask the LLM to generate code for a new skill, utilizing available **Control Primitives**.
3.  The generated or retrieved skill (JavaScript code) is executed in the Minecraft environment via the **Environment Interaction Layer**.
4.  The **Critic** observes the outcome and provides feedback.
5.  If the skill is new or was modified, it's added or updated in the **Skill Library**.
6.  The process repeats, allowing Voyager to continuously learn and expand its capabilities.

This modular architecture allows Voyager to be adaptable and to continuously improve its performance in the complex and open-ended world of Minecraft.
