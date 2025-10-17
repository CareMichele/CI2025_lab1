# Multi-Dimensional Knapsack Problem

Ideas and approaches were discussed during the week with:
- Davide Carletto (s339425)
- Federico Carollo (s339645)

## Solution Strategy
The implemented solution uses a **Simulated Annealing** approach with the following components:

### Initialization
- Start with empty knapsacks (all items unassigned)
- Initial temperature T = 10.0 with cooling factor = 0.99

### Tweak Function
Simple perturbation strategy:
- Randomly select an item
- If item is unassigned: add it to a random knapsack
- If item is assigned: remove it from current knapsack

### Acceptance Criterion
Standard Simulated Annealing acceptance:
- Always accept improvements (delta > 0)
- Accept worse solutions with probability exp(delta/T)
- Temperature decreases over time, reducing acceptance of worse solutions

### Fitness Function
Objective function with penalties:
- **Base value**: Sum of values of all assigned items
- **Constraint penalty**: penalty for capacity violations (×10)
- **Duplicate penalty**: penalty if item appears in multiple knapsacks

### Validation
- `checkSameObject()`: Ensures no item appears in multiple knapsacks
- Constraint violations handled through penalty-based fitness

