# Exno.7-Develop a prompt-based application tailored to their personal needs, fostering creativity and practical problem-solving skills while leveraging the capabilities of large language models.

# Date:19-09-2025
# Register no.212223080041
# Aim: To develop a prompt-based application using ChatGPT - To demonstrate how to create a prompt-based application to organize daily tasks, showing the progression from simple to more advanced prompt designs and their corresponding outputs.




#AI Tools Required:

Explanation:
Prompt: "Design a personal productivity assistant that can help manage daily tasks, schedule reminders, suggest wellness tips, and answer general queries. The assistant should interact using natural language and be adaptable to the user’s changing preferences over time." Procedure:

Define the core requirements of a personal productivity assistant.
Identify and construct appropriate prompts for each task using an LLM (e.g., ChatGPT).
Simulate natural user interaction through a simple interface or command-line system.
Collect feedback or inputs from users and adapt responses accordingly.
(Optional) Integrate basic memory to simulate preference adaptation. EXPECTED OUTPUT: - (attached the drive link) Output (Example Response by LLM): Personal Productivity Assistant Features:
Daily Task Manager: o Accept tasks via natural language (e.g., "Remind me to call mom at 6 PM"). o Organize tasks by priority and deadline. o Provide daily summaries and pending items.
Smart Scheduler: o Schedule events and set reminders using contextual understanding. o Notify user of overlapping appointments or free time slots.
Wellness Tips Generator: o Suggest daily wellness advice (hydration, exercise, screen-time breaks). o Adapt suggestions based on past user preferences and responses.
Features Implemented
Daily Task Manager – add, list, and mark tasks complete.

Smart Scheduler / Reminders – stores due-times and checks what is due soon.

Wellness Tips – random, easy tips; adapts slightly based on your stored preferences.

General Q&A (mocked) – simple keyword-based answers to simulate LLM help.

Python Code
import datetime import time import random from collections import defaultdict

---------- Mock "LLM" Response ----------
def mock_llm_response(prompt: str) -> str: """Simulate a language model reply.""" if "weather" in prompt.lower(): return "Today's weather looks pleasant with mild temperatures." elif "quote" in prompt.lower(): return random.choice([ "“The best way to get started is to quit talking and begin doing.” – Walt Disney", "“Don’t watch the clock; do what it does. Keep going.” – Sam Levenson" ]) else: return "I'm your assistant and can help with tasks, reminders, or wellness tips!"

---------- Core Assistant ----------
class PersonalAssistant: def init(self): self.tasks = {} # task_id -> (task, deadline, done) self.next_id = 1 self.user_prefs = defaultdict(int) # simple memory for wellness likes

def add_task(self, description, deadline=None):
    self.tasks[self.next_id] = [description, deadline, False]
    print(f"Task #{self.next_id} added.")
    self.next_id += 1

def list_tasks(self):
    if not self.tasks:
        print("No tasks yet.")
        return
    print("\nYour Tasks:")
    for tid, (desc, deadline, done) in self.tasks.items():
        status = "✓" if done else "✗"
        dline = f" (due {deadline})" if deadline else ""
        print(f"[{status}] {tid}: {desc}{dline}")

def mark_done(self, tid):
    if tid in self.tasks:
        self.tasks[tid][2] = True
        print(f"Task #{tid} marked complete.")
    else:
        print("Invalid task ID.")

def check_reminders(self):
    now = datetime.datetime.now()
    for tid, (desc, deadline, done) in self.tasks.items():
        if deadline and not done:
            if now >= deadline - datetime.timedelta(minutes=1):
                print(f"Reminder: Task #{tid} '{desc}' is due at {deadline}!")

def wellness_tip(self):
    tips = [
        "Drink a glass of water.",
        "Take a 5-minute stretch break.",
        "Practice deep breathing for one minute.",
        "Walk for 10 minutes if possible."
    ]
    # basic preference adaptation
    preferred = max(self.user_prefs, key=self.user_prefs.get, default=None)
    if preferred:
        tips.append(f"Repeat your favorite: {preferred}")
    tip = random.choice(tips)
    self.user_prefs[tip] += 1
    print("Wellness Tip:", tip)

def general_query(self, question):
    print(mock_llm_response(question))
---------- Simple CLI ----------
def main(): assistant = PersonalAssistant() print("=== Personal Productivity Assistant ===") print("Commands: add, list, done, tip, ask, check, quit")

while True:
    cmd = input("\n> ").strip().lower()

    if cmd == "add":
        desc = input("Task description: ")
        dline = input("Deadline (YYYY-MM-DD HH:MM or blank): ")
        deadline = None
        if dline:
            try:
                deadline = datetime.datetime.strptime(dline, "%Y-%m-%d %H:%M")
            except ValueError:
                print("Invalid format, skipping deadline.")
        assistant.add_task(desc, deadline)

    elif cmd == "list":
        assistant.list_tasks()

    elif cmd == "done":
        tid = int(input("Task ID to mark complete: "))
        assistant.mark_done(tid)

    elif cmd == "tip":
        assistant.wellness_tip()

    elif cmd == "ask":
        q = input("Ask a question: ")
        assistant.general_query(q)

    elif cmd == "check":
        assistant.check_reminders()

    elif cmd == "quit":
        print("Goodbye!")
        break
    else:
        print("Unknown command. Try again.")
if name == "main": main() How It Demonstrates the Procedure

Define requirements – tasks, scheduler, wellness, Q&A.

Prompt construction – the mock mock_llm_response simulates an LLM answering natural questions.

Natural interaction – CLI accepts commands in everyday language.

Feedback & adaptation – tracks which wellness tips you pick most and surfaces them more often.

Optional memory – preferences stored in self.user_prefs during the session.

## Running & Extending
Run in a terminal: python assistant_app.py

Use commands like:

add → “Remind me to call mom” with a deadline.

tip → get wellness advice.

ask → “Give me a motivational quote.”

To connect to real LLMs, replace mock_llm_response() with an actual API call (e.g., OpenAI’s openai.ChatCompletion.create()).

Result:
The lab exercise resulted in the creation of a prototype concept for a personal assistant powered by large language models. Students were able to:  Understand how to tailor LLM prompts to real-life applications.  Foster creativity by designing features suited to their personal or academic lives.  Learn prompt engineering techniques for optimal interaction with AI tools.  Experience the versatility and utility of generative AI in solving everyday problems.


# Result: 
The lab exercise resulted in the creation of a prototype concept for a personal assistant powered by large language models. Students were able to:
 Understand how to tailor LLM prompts to real-life applications.
 Foster creativity by designing features suited to their personal or academic lives.
 Learn prompt engineering techniques for optimal interaction with AI tools.
 Experience the versatility and utility of generative AI in solving everyday problems.
