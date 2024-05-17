# CS6700: Reinforcement Learning
PA3 EE21S048 NS24Z111
April 20, 2024
Assignment 3

Team Members:
* Matcha Naga Gayathri (EE21S048)
* Ragu B (NS24Z111)

## OPTIONS:
Implementation Details:
* Primitive options are special cases of options that last exactly one step.
* Primitive options are South, North, East, West, Pick, and Drop.
* The rest of the options defined are multi-step, i.e., temporally extended.
* Temporally extended options are Opt_R, Opt_G, Opt_Y, Opt_B.
* These options correspond to [0,1,2,3,4,5,6,7,8,9] respectively.
* Deterministic policies for the set of temporally extended options (Opt_R, Opt_G,
Opt_Y, and Opt_B)

## SMDP Q-Learning:
* SMDP (Semi-Markov Decision Process) Q-Learning extends traditional
Q-Learning to handle options, which are temporally extended actions. Options
allow the agent to select a course of action that may take multiple time steps to
complete.
* In SMDP Q-Learning, the Q-values represent the expected return when starting in
a particular state and taking a specific action or option. Updates to Q-values
occur after the completion of each action or option, considering the cumulative
rewards obtained during its execution.

## Intra-Option Q-Learning:
* Intra-option Q-Learning focuses on learning within options. Instead of treating
options as atomic actions, it decomposes them into primitive actions and learns
policies within each option.
* In Intra-Option Q-Learning, the agent maintains separate Q-values for each
primitive action within an option. These Q-values are updated during the
execution of the option, allowing the agent to learn the value of selecting each
primitive action within the context of the option. 

## INFERENCE:
* It's evident that, overall, alternate options tend to underperform, particularly in SMDP
Q-Learning. This is likely because these options aren't optimized for reaching high-reward
states or key objectives like locating, picking up, and dropping off passengers.
* Intra-option Q-Learning demonstrates better performance even with these alternative options,
nearing convergence with the optimal solution. This improvement is attributed to continuous
updates within options during the execution of other options, facilitating faster convergence.
* Additionally, the deterministic nature of policies for alternate options contributes, as their
state-action pairs are repetitive, leading to frequent updates in the Q-table, aligning with the
principles outlined in Theorem 1 of Intra-Option Learning about Temporally Abstract Actions.
* Theorem 1 (Convergence of intra-option Q-learning) For any set of deterministic Markov
options, one-step intra-option Q-learning converges w.p.1 to the optimal Q-values, for every
option regardless of what options are executed during learning provided every primitive action
gets executed in every state infinitely often.
* Both SMDP Q-Learning and Intra-option Q-Learning perform similarly in terms of reward curves
and Q-tables. However, the Intra-Option method exhibits superior performance in terms of
Q-values and convergence to the optimal policy, as illustrated by the case of state 0.
