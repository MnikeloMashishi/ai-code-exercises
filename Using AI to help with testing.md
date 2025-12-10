# Using AI to Help with Testing

I chose the JavaScript TaskManager code and focused on understanding how to test the calculateTaskScore function.

## Part 1: Understanding What to Test
What calculateTaskScore Should Do:
- Combine priority, due date, and how long ago the task was updated
- Return a score showing how important a task is

## Behaviors & Edge Cases
Key behaviors:
- Higher priority => higher score
- Closer due date => higher score
- Older update date => higher score

Edge cases I thought of:
- No due date
- Very old tasks
- Invalid priority
- Future dates

AI helped me think of:
- Overdue tasks
- Tasks with missing properties
- Priorities outside expected range
- Very new vs very old tasks

Tests I Should Write
- Basic scoring
- No due date
- Overdue tasks
- Old vs recent updates
- Invalid priority

## Part 2: Improving a Test
My first test

Only checked if the result was a number — not very useful.

## Improved test
Checks actual behavior:

expect(highScore).toBeGreaterThan(lowScore);

Much clearer and actually tests logic.

## Due date test I wrote
Checks that tasks due sooner get higher scores. This helped me understand how due dates affect scoring.

## Part 3: TDD Practice
New Feature: User Assignment Boost

I wrote a failing test first, then updated the function with a small change that adds +12 if the task is assigned to the current user.

## Bug Fix
Wrote a test around “days since update,” then fixed the logic. TDD helped me confirm the fix worked.

## Part 4: Integration Test
I tested the full workflow:
- Sort tasks
- Get the top important ones
- Make sure the order is correct

This confirmed the whole system works together.

## What I Learned
About Testing:
- Good tests check behavior, not types
- Edge cases matter
- Clear tests > lots of tests
- Tests make your code easier to trust

About Using AI
- AI helped me think, not just code
- It pointed out edge cases I didn’t consider
- Talking through the test logic improved my understanding

About TDD
- Writing tests first clarifies what the function should do
- Small steps are best
- Refactoring is safer when tests back you up

Main Takeaway

AI helps me think about testing, but writing the tests myself is what actually teaches me.