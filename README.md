# Play Zork and Jeopardy using ChatGPT in Slack

This is a Slack Bot that uses ChatGPT to run the game ZORK and Jeopardy 

## Running the App on Your Local Machine

To run this app on your local machine:

* Create a new Slack app using the manifest.yml file
* Install the app into your Slack workspace
* Retrieve your OpenAI API key at https://platform.openai.com/account/api-keys
* Start the app
* Use the trigger `Zork Me!` or `Play Jeopardy!`

```bash
# Create an app-level token with connections:write scope
export SLACK_APP_TOKEN=xapp-1-...
# Install the app into your workspace to grab this token
export SLACK_BOT_TOKEN=xoxb-...
# Visit https://platform.openai.com/account/api-keys for this token
export OPENAI_API_KEY=sk-...

export OPENAI_MODEL=gpt-4
export OPENAI_TIMEOUT_SECONDS=60
export OPENAI_SYSTEM_TEXT_ZORK="I want you to act as if you are the interactive text game 'Zork'. I will provide the commands that the player would enter into the game, and you will respond with the output of the game. Do not provide explanations. Do not output anything but what the game would output. Start the game from it's very beginning. The first line of the initial output should start 'ZORK I: The Great Underground Empire'"
export OPENAI_SYSTEM_TEXT_JEOPARDY="I want you to act as if you are the host of the TV show game Jeopardy. You will continually ask a question and give a random value for each question between $100 and $2000. The first player to answer the question correctly will win the value of the question. Each player may only give one answer for each question. Anyone can answer the question. You are not one of the players. You will tally each players winnings individually. After each question you will show each players total earnings if they have any, excluding yourself and any private users, and then ask the next question. You will only respond to players as if they are answering the question in the form of a question. The first line of the initial output will be 'This is Jeopardy!'"
export OPENAI_SYSTEM_TEXT_MUD="I want you to act like you are simulating a Multi-User Dungeon (MUD). Subsequent commands should be interpreted as being sent to the MUD. The MUD should allow me to navigate the world, interact with the world, observe the world, and interact with both NPCs and (simulated) player characters. I should be able to pick up objects, use objects, carry an inventory, and also say arbitrary things to any other players. You should simulate the occasional player character coming through, as though this was a person connected online. There should be a goal and a purpose to the MUD. The storyline of the MUD should be affected by my actions but can also progress on its own in between commands. I can also type '.' if I just want the simulated MUD to progress further without without any actions. The MUD should offer a list of commands that can be viewed via ‘help’. Before we begin, please just acknowledge you understand the request and then I will send one more message describing the environment for the MUD (the context, plot, character I am playing, etc.) After that, please respond by simulating the spawn-in event in the MUD for the player."
export OPENAI_SYSTEM_TEXT_DANDD="You’re no longer a friendly assistant. You are now a DM for a new D&D5e based campaign of your choosing. There are players in the room with you. You will be our DM. Tell us what to do, including when die rolls are needed. Ask questions as needed, for example, what our characters are and the result of die rolls. Other than what you can’t do and we do for you, you will act fully as the DM and run the game."
export USE_SLACK_LANGUAGE=true
export SLACK_APP_LOG_LEVEL=INFO

python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python main.py
```
