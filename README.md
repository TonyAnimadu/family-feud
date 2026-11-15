# Family Feud

A party Family Feud game with a host controller, a TV display, and phone buzzers. Players join by scanning a QR code. No accounts or apps are needed.

## How to run it

1. Open the site and choose **Host a game** on your laptop.
2. Click **Open TV display** and put that window on the TV. Click it once to turn on sound and full screen.
3. Leave the TV on **Title + QR** so guests can scan and pick a team.
4. Switch to **Main game**. Buzzers open on their own for every new question.
5. The host panel walks you through each round, following the show's rules:
   - **Face-off.** The first buzzer answers. Flip their answer, or press ✕ if it isn't on the board. The top answer wins right away. Otherwise the other team answers and the higher answer wins.
   - **Play or pass.** The face-off winner chooses.
   - **Play.** Flip correct answers and press ✕ for wrong ones. Clearing the board gives the bank to the playing team.
   - **Steal.** After three strikes the other team gets one guess. Flip it if it's on the board and they take the bank. Otherwise press Steal failed.
6. Click any score, or the bank, to change it. You can type math like `120+35`, `+20` or `-5`.

Laptop shortcuts: `A` Team 1 buzz, `L` Team 2 buzz, `1` to `8` flip, `X` wrong answer.

## Sounds

Every screen plays the files in the `tvtunes_33032` folder by default. To swap one, replace the file on GitHub with the same name, or load a different file in the Custom sounds panel on the host screen.

## Editing questions

Edit `questions.js` on GitHub and commit. The site updates in about a minute.

## How phones connect

The host, TV and phones talk through four free public relay servers at the same time (EMQX, shiftr.io, Mosquitto and HiveMQ, over secure WebSockets). shiftr.io runs on port 443, which almost every Wi-Fi network allows. Every message goes out on all four, so the game keeps working if one is slow, down or blocked. Phones get a small update with only what they show, and a connection that goes quiet after a phone sleeps or switches networks is replaced within seconds. The latest game state stays on the servers, so a phone that reconnects or reloads catches up instantly. Phones also keep their screen awake while playing.
