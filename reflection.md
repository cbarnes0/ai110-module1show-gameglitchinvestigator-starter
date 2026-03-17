# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

  First running through the game I failed on trying to guess the number. I believe this is because the hint that it gives you does the opposite of what it should (Ex. Secret: 24, Guess: 10, Response: "Go Lower"). After completing a run and trying to use the new game button, the game wouldn't reset. It would change the number in the debugging but not reset the game. After refreshing the page I found that the new game button only works in the middle of a game, not after completing one. You would expect the new game button to always reset to a new game, especially after completing one. I noticed that the ranges and attempts seemed off as well with 1-20 for easy, 1-100 for normal, and 1-50 for hard with similarly in consistent attempt counts relative to the difficulty. The attempts left is also incorrect, displaying 1 more than the attempt that you are on. I think this may be because in the atteemps of the dev debug info you start at 1 instead of 0. 

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

On this project I only used Claude Code.

A simple example where Claude suggested the correct result was swapping the text to be correct for "Go higher" or "Go lower" for the results. I was able to identify the issue, point it out to Claude and easily fix it and immediately test the app to see the correct hint now being returned.

I noticed an issue when continuing to play around with the app that I was interested in trying to fix. I had to dig a bit deeper because all of the initial bugs I found, Claude Code easily helped me to be able to fix them. I noticed that when I should have run out of attempts, it always said I had one more attempt left, instead of being zero. In trying to fix this, Claude kept trying to move the submit buttons or results to different parts of the page. It completely disrupted the flow of the page and didn't make sense. After playing around a bit I was able to find a seperate solution. Claude's solutions "worked" but the way it made it work was kind of silly and changed the visual flow of the web page too much. We ended up using a plcae holder to correctly update without changing where on the page things were. 

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

To truly decide if a bug was fixed, I had to be able to verify it by using the application. That's typically my process for debugging. 

One example of a test I had to do quite a few times was going in and playing games to completion. The was particularly useful when fixing the difficulties and the hints given.

AI was incredibly helpful for fixing and creating tests. The tests were returning false when they should have been true and Claude Code was able to easily resolve for the issue for the tests to work when they were supposed to.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.

Streamlit reruns the script top to bottom on every interaction. This means without the right protections, a new secret will get created each time you interact.

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

Every time you interact with something on the page or load it, Streamlit runs the whole python file, almost as if you completely refreshed the page.

- What change did you make that finally gave the game a stable secret number?

Using Claude, a solution was found to check if the secret was already created using st.session_state. We also ended up using something similar with using the st.empty() placeholder to read the correct value for attempts left. 

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.

I am usually not as good about doing regular commits, this was a great reminder to do more. It was always really nice to pace breaking down the bugs and then working with AI. I'll defintely use similar pacing in the future.

- What is one thing you would do differently next time you work with AI on a coding task?

Next time I work on an AI coding task I think I'll start off even slower, really soak everything in. However, I would also move much faster once everything was identified using AI fully to my advantage.


- In one or two sentences, describe how this project changed the way you think about AI generated code.

AI generated code is incredibly useful, especially when you understand how to fix it and prompt correctly. However, it can be confusing and convoluted given some tricky situations and may try and find "the easy way out". 
