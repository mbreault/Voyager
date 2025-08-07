# Agents Module (`voyager/agents/`)

The `voyager/agents/` directory houses the core decision-making and learning components of Voyager. These modules work in concert to enable the agent to understand its goals, generate plans, execute actions, and learn from its experiences.

## Key Components:

*   **`action.py` (Action Generation):**
    *   **Purpose:** Responsible for determining the specific actions the agent should take to achieve its current sub-goal.
    *   **Functionality:** This module likely interacts heavily with the LLM. Given a task or sub-goal, it queries the LLM to generate or select appropriate JavaScript code (a skill) to execute in the Minecraft environment. It might also decide which existing skill from the skill library is best suited for the current situation.

*   **`critic.py` (Critic):**
    *   **Purpose:** Evaluates the outcomes of the agent's actions and provides feedback for learning and improvement.
    *   **Functionality:** The critic assesses whether an action was successful in achieving its intended purpose. This can involve:
        *   Checking for expected changes in the environment.
        *   Analyzing error messages if a skill execution fails.
        *   Performing self-verification to confirm task completion.
    *   The feedback from the critic is crucial for the iterative prompting mechanism, helping to refine skills and improve future action selection.

*   **`curriculum.py` (Automatic Curriculum):**
    *   **Purpose:** Drives the agent's exploration and learning by proposing a sequence of tasks or goals.
    *   **Functionality:** Instead of relying on a fixed set of predefined tasks, the automatic curriculum dynamically generates new challenges for Voyager. The aim is to maximize exploration of the Minecraft world and encourage the acquisition of a diverse range of skills. This component ensures that Voyager is continually pushing its boundaries and learning new things in an open-ended manner.

*   **`skill.py` (Skill Management):**
    *   **Purpose:** Manages the agent's library of learned skills.
    *   **Functionality:** This module is responsible for:
        *   **Storing new skills:** When the LLM generates a new piece of executable code (a skill) that successfully accomplishes a task, this module saves it to the `skill_library/`.
        *   **Retrieving existing skills:** When faced with a task, this module helps find relevant skills from the library that can be reused or adapted.
        *   **Refining skills:** It may also be involved in updating or improving existing skills based on feedback from the critic or new experiences.

These agent components form a closed loop: the curriculum proposes a task, action generation decides how to tackle it (potentially creating a new skill), the skill is executed, the critic evaluates the result, and the skill management module updates the agent's knowledge base. This iterative process is fundamental to Voyager's lifelong learning capabilities.
