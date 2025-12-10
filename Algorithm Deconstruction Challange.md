I chose the Task Priority Sorting Algorithm because it relates directly to the task manager project. The algorithm revolves around three main functions: 
- calculateTaskScore 
- sortTasksByImportance
- getTopPriorityTask

At first, I thought it just sorted tasks by priority labels like LOW, MEDIUM, HIGH, and URGENT. But when I looked closer I realized the system actually assigns every task a numeric score based on multiple factors. That score determines the order.

I wasn’t sure why certain values were weighted the way they were or why completed tasks received negative scores. AI prompts helped me break the logic down step by step.

Breakdown (calculateTaskScore):

1. Base Priority Value
Each priority level has a weight multiplied by 10:
- LOW => 10
- MEDIUM => 20
- HIGH => 30
- URGENT => 40

2. Due Date Bonuses
Tasks get extra points based on urgency:
- Overdue => +30
- Due today => +20
- Due in the next => 2 days → +15
- Due this week => +10

3. Status Penalties
- Certain statuses decrease the score:
- DONE → –50
- REVIEW → –15

4. Extra Bonuses
- Additional small boosts:
- Tags like blocker, critical, urgent → +8
- Updated today → +5

Overall formula:
Priority Score + Due Date Bonus – Status Penalty + Extra Bonuses = Final Score

Other Functions

sortTasksByImportance(tasks)
- Copies the array, calculates each score, and sorts tasks from highest to lowest.

getTopPriorityTasks(tasks, limit = 5)
- Returns the top N highest-scoring tasks.

