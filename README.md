# Unmatched Ego Checker

An online bragging battle. Type sentences about yourself; the scanner turns each one into **ego points**. Win ranked 2-minute matches to climb the leaderboard. Pass 100,000 points and you *almost* have an unmatched ego, besides the egoist Dempsey.

**Play:** https://asherhawk-school.github.io/unmatched-ego-checker/

## How it works

- **Ranked matches:** press *Find ranked match* and you're paired with another player in the queue. Ratings start at 1,000 and use Elo (K = 32).
- **No repeats:** a sentence that you or your rival already said is rejected, and each brag word only scores once per match.
- **Roasts:** aim an insult at your rival ("you", "your", or their name) and they lose points. Each insult works once per match; "!" makes it hit harder (max 15,000 per roast).
- **Leaderboard and match feed** are shared by everyone who plays.
- **Practice solo** works offline and doesn't change your rating.

## Tech

One static `index.html`. Multiplayer runs over the free public HiveMQ MQTT broker (`wss://broker.hivemq.com:8884/mqtt`) using [MQTT.js](https://github.com/mqttjs/MQTT.js). No accounts or server to run.

Because the broker is public and free, scores aren't tamper-proof, and the broker may occasionally wipe stored leaderboard data. Your own rating and record are also saved in your browser.

Tip: add `?p=2` to the URL to play as a second profile in the same browser (handy for testing).
