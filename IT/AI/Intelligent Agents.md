## Agent and Environment
- An **agent** is anything that can be viewed as perceiving its **environment** through **sensors** and Sensor acting upon that environment through **actuators**.
- PEAS (Performance, Environment, Actuators, Sensors)
![[agent.png]]
## Performance measures
- As a general rule, it is better to design performance
in the environment, rather than according to how one thinks the agent should behave.

## Properties of task environments
- Fully observable vs partially observable
- Single-agent vs multiagent
	- Chess: competitve multiagent
- Deterministic vs nondeterministic (stochastic)
	- If the next state of the environment is completely determined by the current state and the action executed by the agent(s), then we say the environment is deterministic; otherwise, it is nondeterministic
- Episodic vs sequential
	- In sequential environments, the current decision could affect all future decisions
- Static vs Dynamic
	- Environment can change while an agent is deliberating - Dynamic
- Discrete vs continuous
- Known vs unknown
	- Not strictly a property of the environment

### Simple reflex agents
Simple reflex agents respond directly to percepts,
### Model-based reflex agents
Model-based reflex agents maintain internal state to track aspects of the world that are not evident in the current percept
### Goal-based agents
Goal-based agents act to achieve their goals
### Utility-based agents
Utility-based agents try to maximize their own expected “happiness.”
### Learning agents 
All agents can improve their performance through learning

