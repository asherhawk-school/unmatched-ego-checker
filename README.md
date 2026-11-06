# Unmatched Ego Checker

An online bragging battle. Type sentences about yourself; the scanner rates each one in **ego points**. Win ranked 2-minute matches to climb the leaderboard. Pass 100,000 points and you *almost* have an unmatched ego, besides the egoist Dempsey.

**Play:** https://asherhawk-school.github.io/unmatched-ego-checker/

## How it works

- **Accounts:** sign up with a username and password. Names are unique and can't be changed. Each device can create one account. Signing in somewhere new signs you out everywhere else.
- **Ranked matches:** press *Find ranked match* to be paired with another signed-in player. You can't be matched against yourself.
- **Slow Elo:** ratings start at 1,000 and move up to 20 points a match for your first 10 games, then up to 12.
- **Profiles:** click any player's name (leaderboard, match feed, or your rival mid-match) to see their rating, record, win rate, best score, status and recent matches.
- **Secret scoring:** the word list is stored as hashes, so it can't be read from the page.
- **No shortcuts:** punctuation and caps earn nothing extra, one sentence every 2 seconds, no pasting, no repeated sentences, and every brag word only counts once per match.
- **Roasts:** aim an insult at your rival ("you", "your", or their name) and they lose points.
- **Anti-cheat:** a rival's score can only grow by what one sentence can earn, impossible records are hidden, banned players are blocked, matches where nobody brags don't count, and only 3 matches per rival per day affect rating.
- **Practice solo** works without an account and doesn't change your rating.

## Tech

One static `index.html`. Multiplayer and accounts run over the free public HiveMQ MQTT broker (`wss://broker.hivemq.com:8884/mqtt`) using [MQTT.js](https://github.com/mqttjs/MQTT.js). Passwords are never sent or stored in plain text: they're hashed in the browser with PBKDF2-SHA256 (150,000 rounds, random salt).

Because the broker is public and there's no game server, this is not bank-grade security: a skilled attacker could still tamper with data. It's built to stop casual cheating and to make hacks easy to clean up.

Tip: add `?p=2` to the URL to use a second, separate login in the same browser (handy for testing).
