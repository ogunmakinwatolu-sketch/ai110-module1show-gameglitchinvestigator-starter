# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it? 
Answer: The game looked okay and ran pretty well, it didn't look out of place.

- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
Answer: Normal looks harder than 'Hard' based on the range. The range for normal is higher than the range for hard.
Secondly, the range request for each level is fixed on the main page (info page) and only changes on the side panel.
Thirdly, the hints are inaccurate, it suggests to go higher or lower even though this means I exceed the range requested. 

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
Answer: I used Claude for this project

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
Answer: One suggestion Claude gave was on how to fix the intentional type mismatch where the number prints as wrong (regardless of being correct or not) because the secret number becomes a string at every even attampt. I fixed the rootcause by removong the conditonlal cast so the secret number is always an integer.

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
Answer: It didn't give me any misleading or incorrect suggestion.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
Answer: I used test cases and ran the app many times to see the changes.

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
Answer: I ran python -m pytest tests/test_game_logic.py -v and one test, test_too_high_hint_says_go_lower, confirmed that the hints were swapped, the game was telling me to guess higher when I actually needed to go lower. Once we fixed it, all 7 tests passed.

- Did AI help you design or understand any tests? How?
Answer: Yes it did. Claude designed the tests based on the two bugs we found. For the swapped hints, it checked the actual message text (not just the outcome) to make sure "Too High" says "LOWER" and vice versa. For the type mismatch, it tested check_guess with multiple int pairs to confirm no TypeError gets raised and the direction is always correct.
---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
