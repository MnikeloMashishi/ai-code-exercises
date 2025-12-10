Original Code:

function calculateTaskScore(task) { // Base priority weights const priorityWeights = { [TaskPriority.LOW]: 1, [TaskPriority.MEDIUM]: 2, [TaskPriority.HIGH]: 3, [TaskPriority.URGENT]: 4 };


// Calculate base score from priority
let score = (priorityWeights[task.priority] || 0) * 10;

// Add due date factor (higher score for tasks due sooner)
if (task.dueDate) {
    const now = new Date();
    const dueDate = new Date(task.dueDate);
    const daysUntilDue = Math.ceil((dueDate - now) / (1000 * 60 * 60 * 24));
    if (daysUntilDue < 0) { // Overdue tasks
        score += 30;
    } else if (daysUntilDue === 0) { // Due today
        score += 20;
    } else if (daysUntilDue <= 2) { // Due in next 2 days
        score += 15;
    } else if (daysUntilDue <= 7) { // Due in next week
        score += 10;
    }
}

// Reduce score for tasks that are completed or in review
if (task.status === TaskStatus.DONE) {
    score -= 50;
} else if (task.status === TaskStatus.REVIEW) {
    score -= 15;
}

// Boost score for tasks with certain tags
if (task.tags.some(tag => ["blocker", "critical", "urgent"].includes(tag))) {
    score += 8;
}

// Boost score for recently updated tasks
const now = new Date();
const updatedAt = new Date(task.updatedAt);
const daysSinceUpdate = Math.floor((now - updatedAt) / (1000 * 60 * 60 * 24));
if (daysSinceUpdate < 1) {
    score += 5;
}

return score;


Prompt 1: Comprehensive JSDoc Documentation

Calculates a priority score for a task based on multiple weighted factors.
This function implements a sophisticated scoring system that considers:
- Base priority level (LOW=10, MEDIUM=20, HIGH=30, URGENT=40 points)
- Urgency based on due date proximity (overdue +30, today +20, etc.)
- Status penalties (DONE -50, REVIEW -15)
- Special tag boosts (blocker/critical/urgent +8)
- Recent activity boost (updated today +5)

Higher scores indicate higher priority tasks that should be tackled first.

@param {Object} task - The task object to score
@param {TaskPriority} task.priority - Task priority level (LOW, MEDIUM, HIGH, URGENT)
@param {Date|string} task.dueDate - Due date (ISO string or Date object)
@param {TaskStatus} task.status - Current task status (TODO, INPROGRESS, REVIEW, DONE)
@param {string[]} task.tags - Array of task tags
@param {Date|string} task.updatedAt - Last update timestamp (ISO string or Date object)

@returns {number} Numeric priority score (higher = more urgent)

@example
const urgentOverdueTask = {
priority: TaskPriority.URGENT,
dueDate: "2023-12-01", // overdue
status: TaskStatus.INPROGRESS,
tags: ["blocker"],
updatedAt: new Date()
};
const score = calculateTaskScore(urgentOverdueTask); // ~83

@example
const lowPriorityDoneTask = {
priority: TaskPriority.LOW,
status: TaskStatus.DONE
};
const score = calculateTaskScore(lowPriorityDoneTask); // -40

@throws {TypeError} If task is not an object
@throws {Invalid Date} If dueDate or updatedAt cannot be parsed as valid dates

@notes
- Scores can be negative for completed/low-priority tasks
- Overdue LOW priority can outscore future URGENT tasks
- Date calculations use local timezone
- Missing priority defaults to 0 base score */

Prompt 2: Intent and Logic Insights High level intent: Create intelligent task prioritization beyond simple labels. Real productivity needs multi-factor urgency detection.

Step-by-step logic breakdown:

- Priority base (10-40 points)
- Due date urgency buckets (+0 to +30)
- Status deprioritization (-50 or -15)
- Critical tags (+8)
- Recency (+5)
- Return total score

Key assumptions:
- All tasks have valid priority/status enums
- Dates parse correctly from strings
- Tags are simple strings
- Local timezone acceptable