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
export USE_SLACK_LANGUAGE=true
export SLACK_APP_LOG_LEVEL=INFO

python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python main.py
```
