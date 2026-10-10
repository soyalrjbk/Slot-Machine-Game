# 🎰 Slot Machine

A browser slot machine built for Week 5 of the 2019 Resilient Coders bootcamp curriculum. You start with a $500 balance and choose a $5 or $50 bet. Three fruit reels spin with each bet, and if all three match, you win 10× your bet. Your balance updates after each spin, and the game won't let you bet more than you have.

<img width="700" height="400" alt="Slot Machine" src="https://github.com/user-attachments/assets/f54f321d-71de-45a2-a7ca-0c2eaf59bd40" />

## How It's Made:

**Tech used:**

<p align="left">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
</p>

The page has three empty `reel` divs inside a Flexbox container, a balance display, and two bet buttons. Each reel uses CSS Grid (`place-items: center`) so the emoji symbol sits in the middle at 80px.

All of the game logic lives in one `spin(bet)` function, which both buttons call with their bet amount (`spin(5)` and `spin(50)`):

- **Balance check** – if the bet is larger than the current balance, it shows "Not Enough Balance!" and stops.
- **Spinning the reels** – the bet is subtracted, then each reel picks a random symbol from an array of five fruits (🍍 🍒 🍌 🍉 🍋) using `Math.floor(Math.random() * symbols.length)` and displays it with `innerText`.
- **Checking for a win** – if all three reels match, the player wins 10× their bet and sees "Congratulations, Winner!"; otherwise, "You Lose!"
- **Updating the display** – the new balance is written back to the page with a template literal.

## Optimizations

- Store the reel results in an array and use `every()` to check for a match, so adding a fourth reel or more symbols doesn't mean rewriting the logic.
- Disable the bet buttons when the balance is too low, and add a "Reset" button to start over at $500.
- Add a short spinning animation (CSS keyframes or cycling symbols with `setInterval`) before the reels land, so it feels more like a real slot machine.
- Add `display: grid` to `body`. Right now `place-items: center` has no effect without it, so the game isn't actually centered on the page.
- Balance the payouts. With 5 symbols, the odds of three matching are 1 in 25, so a 10× payout means players lose money over time. Adding smaller prizes, like two matching reels, would make the game more fun.

## Lessons Learned:

This project taught me how to structure a program around one reusable function that takes a parameter, so two buttons could share the same logic just by passing different bet amounts. I practiced generating random values from an array, comparing several values with logical operators, and keeping a running state (the balance) in sync with what's shown on the page. Handling the "not enough balance" case also got me thinking about validating user actions before running the main logic.
