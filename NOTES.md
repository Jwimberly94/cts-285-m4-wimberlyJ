# NOTES: Three Layers

Your name: TODO

Fill each TODO. Write plain, short sentences. Do not delete the headings.

## Part 1. Predict, then find [S1]

Write your prediction before you open any code. Then search. In the last column, write each file the search finds and what that file does.

| Action | Search word | My prediction (file) | Files found and what each does |
|---|---|---|---|
| Prints "Not yet. Try again." | `Not yet` | app.py. The screen text is in the interface layer. | app.py — prints the message and reads user input. dataman/logic.py — decides whether the answer is a retry or a reveal. dataman/store.py — saves each answer so the program can remember it. |
| Decides that the second miss shows the answer | `reveal` | dataman/logic.py. The business rule decides when the answer appears. | dataman/logic.py — returns the reveal outcome on the second miss. app.py — prints the revealed answer to the screen. tests/test_logic.py — checks that the second miss reveals the answer. |
| Saves one attempt | `save_attempt` | dataman/logic.py. The logic layer calls the store after each answer. | dataman/logic.py — saves each try to the store. dataman/store.py — defines save_attempt and writes the JSON data. |
| Refuses the 11th problem | `SetFull` | dataman/logic.py. The rule stops a set at 10 problems. | dataman/logic.py — raises SetFull when the set is full. app.py — catches SetFull and prints a refusal message. exercise/bank.py — has the same rule in the exercise version. |

Search command: `grep -rn "SEARCH WORD" --include=*.py .`

## Part 2. What the program remembered [S1]

After the restart, what did the program remember? The program remembered the last answer

Which file made that possible? dataman_store.json

## Part 3. The interface change [S1]

What did you change in `app.py`? 

I changed the retry message from "Not yet. Try again." to "EEE---".

Why did no test need to change? 

The tests check the program's behavior, not the exact words on the screen.

## Part 4. The rule in the real library [S2]

The same 10-problem rule exists in the real library. Write the file and the function name. dataman/logic.py, MemoryBank.add_problem

## Part 5. The red test [S2]

With the rule removed from the library, what did the screen show? The screen showed "Added. Set holds 11." because the 11th problem was allowed.

With the rule removed, which test failed? test_eleventh_problem_is_refused in tests/test_logic.py

## Part 6. The data swap [S2]

A real database would replace which file? TODO

Which file holds the rules and does not change when the database changes? TODO

## Reflection [S2]

Write 3 to 5 sentences. Pick one layer. Say what you changed in it. Say what stayed the same in the other two layers. TODO

## Beta feedback (optional)

This bonus is a beta test. Which step took longer than its time? What confused you? Write it here. Your answer helps the next class.
