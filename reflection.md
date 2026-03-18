# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

Bug 1: When the secret was 33, I entered 45 as a guess one would expect to be told to guess lower, but instead it output “Go HIGHER!”, which is the wrong direction.

Bug 2: After making a few guesses, I switched from Normal mode to Easy. One would expect that witching difficulty should start a completely new game with a new secret number, cleared history, reset attempts, and a consistent score. However, after switching to Easy, the UI showed the Easy range and reset score display, but the old secret number and previous guess history were still displayed. 

Bug 3: Having switched to easy, I was curious what would happen if the correct answer was entered. Since it was my very first guess in Easy, I expected that the score would be 0 because that is what the debug panel was displaying. However, after winning a message was displayed showing the final score was 50, which did not match the score being displayed.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

I used ChatGPT and GitHub Copilot to help analyze bugs, refactor the code, and generate test cases. One example of a correct AI suggestion was identifying the bug in the check_guess function. The AI explained that when the guess was greater than the secret number, the program incorrectly told the user to “Go HIGHER” instead of “Go LOWER.” It also pointed out that the secret number was sometimes being converted into a string, which could lead to incorrect comparisons. I verified the validity of this fix by testing the game using the Developer Debug Info panel and observing that higher guesses gave the wrong direction. After fixing the logic and ensuring both values were treated as integers, the hints worked correctly.

One misleading AI suggestion was that the scoring system needed to be rewritten. Although the score behaved in a confusing way, I found that it was consistent with the existing update_score logic. I verified this by testing the game and reviewing the function, and decided not to change it since it was not part of the main bugs I was fixing.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I decided whether a bug was fixed by running the Streamlit app to test the behavior directly and monitored the values using the Developer Debug Info panel. At each step, I compared the secret number, guesses, attempts, and score to make sure the game logic matched the expected behavior. For example, after fixing the hint logic, I verified that guesses higher than the secret correctly prompted “Go LOWER,” and guesses lower than the secret prompted “Go HIGHER.”

One test I ran was a pytest test for the check_guess function. The test checked that a guess higher than the secret returns "Too High", a guess lower returns "Too Low", and a correct guess returns "Win". Running pytest showed that the test passed, confirming that the comparison logic was working correctly.

AI helped me design the pytest test helping me understand what behaviors should be verified, such as checking both the outcome and the message returned by the function. I then ran the tests and confirmed they matched the expected behavior.
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
