## What is Formal Verification?
Formal verification is the process of verifying the correctness of a system by using **mathematical logic**
 with respect to a certain specification or property. This method uses geometric state space or mathematical formula
 to validate the system's correctness.

## Why do we need formal verification?
We need formal verification, because in traditional testing, like unit testing or fuzzy logic, we only can
test the system under some predefined scenarios. On the other hand, formal verification makes sure the system is robust enough
to perform correctly in every possible use case since it is verified under a mathematical formulation.

## How does Formal Verification work?
Every formal verification process relies on these core triads:
 1. **Sytem Model ($\mathcal{M}$)**: A mathematical representation of the system. It could be a finite state machine
 representation of traffic light phases, an abstract syntax tree of the source code, or weights of a neural network.
 2. **Specification or Rules ($\phi$)**: The rigious rule that system must obey. For example,
 $\phi$ = "It is never true that the North-South light is Green while the East-West light is Green."
 3. **Verification Engine**: The algorithm that takes $\mathcal{M}$ and $\phi$ and mathematically
 proves whether $\mathcal{M} \models \phi$ (the model satisfies the property). If it fails, the engine usually provides a counterexample-a step-by-step
 trace showing exactly how the system breaks the rule.
 
