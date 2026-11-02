# Teen Taali

A short swap-and-match game for store staff. It is **mandatory**: staff play it before the LMS opens.
It takes about a minute: a round is 45 seconds of play, plus a 13 second demo on the first visit.
The clock stops while a deck line is showing, so a real round takes 50 to 65 seconds from the first tile to the end card
(about 75 seconds on the first visit, with the demo). Plan for about a minute and a quarter.
There is no Later button and no close button.

The floor is 6 by 6 tiles. Five of the tiles are the deck's ushering chain, in order: **Greet** (a waving hand, mint),
**Ask** (a question bubble, violet), **Listen** (an ear, amber), **Guide** (footsteps, coral) and **Hand over**
(two people and a pass arrow, blue). Rohan is already "ready" at the door, so the chain starts at Greet.
Each tile has its own colour and its own shape, so the game works for colour-blind players too.

The player swaps two neighbouring tiles to make three or more in a row. The row clears, Archie claps, the tiles above fall
and new ones drop in. Falling tiles can make new rows: that is "Taali ×2", "Taali ×3".
A swap that makes nothing slides back with a little wobble. There is no penalty.

Above the floor is the walk-in strip: the shopper in the glowing doorway (her bubble shows what she came for), the five
steps in the middle, and Rohan on the right. The next step glows, with "Next: Listen" under it. A match of the glowing
step ticks it, and the strip reacts: Rohan nods and opens his palm (Greet), asks one of the deck's openers (Ask),
leans in while she shows what she is looking for (Listen), turns and walks with her (Guide), and at Hand over they reach
the section. The floor pauses and Archie shows the deck line. Then the next shopper walks in.
Only one person talks at a time: if Listen ticks while Rohan's opener is still up, she answers once his question has been
up long enough to read (1.4 to 2 seconds, by its length), the deck's "Ask. Pause. Listen.".
Matches of other steps just score. Out-of-order matches are never punished: the learning is the repeated order.

Three trap tiles drop in now and then: **Phone out**, **Shouting offers** and **Pitch first** (Iris).
They never match, cannot be moved, and fall like any tile. A match right next to a trap clears it.
Each trap shows its name in a small red tag as it drops in, and again as it pops.
While a trap is on the floor, Rohan is distracted in the strip: his pocket glows, a megaphone floats by, Iris pops up and waves.

It teaches ushering from the Level 1 deck: the five steps in order, the hand-over lines, and three don'ts.
No glasses content. No sign-in. English only.

## What the player sees

1. **First time on this device only:** a 13 second demo plays by itself. A ghost hand drags a tile to line up three
   Greets ("Swap to make three"), points at the glowing Ask in the chain and steps aside so the "Next: Ask" pill can be read
   ("The glow is next"), then makes three Asks right next to Iris, whose "Pitch first" tag shows before she pops
   ("Clear traps beside them") with her line. Then a big "Your turn" button.
   The demo cannot be skipped the first time.
2. The round: 45 seconds on the clock. The timer turns amber for the last 10 seconds.
3. After a hand-over, and the first time each kind of trap is cleared, a panel at the bottom shows the deck line while
   the floor and the clock wait. At a hand-over it opens as soon as the floor is still; the walk to the section plays on
   above it. The line moves on by itself (about 4.5 words a second). After 0.8 seconds the player can
   move it on sooner: a tap on the panel or its arrow (or Enter) shows the next part; a tap on the floor closes the line.
   A tap in the first 0.8 seconds only makes the arrow bob.
   Lines that come from the same cascade share one panel and one pause: the hand-over line first, then the trap line as
   the next part. A trap cleared again later in the round only shows a small crossed-out picture in Rohan's bubble.
4. When the clock reaches 0:00 the current cascade finishes (and any last line shows), then the end card:
   score, stars, Archie's line, shoppers handed over, traps cleared, time, one thing to remember, **Enter LMS** and
   **Play again**. The two buttons sit over the floor, so they only wake up 1.4 seconds after they appear,
   and a quick run of taps does not press them: a tap meant for the floor never ends the round or starts a new one.
5. Enter LMS closes the gate and the LMS opens.

Help when stuck: after 5 seconds without a move, two tiles of a possible swap glow amber, lean toward each other and
wiggle (a swap that makes the glowing step, if there is one). It repeats every 3 seconds until the player moves. If there is no move left at all, Archie reshuffles the floor ("New floor plan."). A new floor never starts
with a match already made.

On later visits the demo is skipped. The (?) icon at the top plays it again whenever the floor is still and no line is
showing; the player then goes back to the same floor, same shopper and the same time left (the clock waits during the demo).
It is not offered on the end card, so a curious tap never throws a finished round away.

Each round is a little different: a new floor, the shoppers in a new order (Anjali, Kunal, Dadi, Meera, Pranav and
Mr Sethi) with shuffled missions (laptop, TV, phone, fridge, headphones), and the traps in a new order and timing.
A laptop shopper always comes in the first two; a later laptop shopper sometimes finds the specialist busy.

## Files

| File | What it is |
| --- | --- |
| `teen-taali.html` | The game. One file with everything inside: styles, script, art and sound (about 200 KB). |
| `demo.html` | A plain sample LMS page with the mandatory gate in front of it. Open it in a browser to try it. |
| `README.md` | This file. |
| `shots/` | Screenshots, one per beat: the demo's glow step, Rohan's opener, a trap landing with its name, Iris popping, the idle hint, a hand-over line on the faded floor, the end card, the gate on desktop. |

Upload `teen-taali.html` to a place your LMS can serve a web page. The same server as the LMS is best.

## Try the demo

Open `demo.html`. The gate covers the page at once. Play a round and tap Enter LMS: the gate fades away.
Reload the page: it goes straight in, because the round is done for today.

**Reset demo** (bottom right, marked "Demo only") clears today's pass and the game's saved flags,
so the gate and the first-time demo show again. It is only for testing. Do not copy it into the LMS.

It works best from a web server. It also works as a local file in Chrome.

## Add the gate to your LMS

The idea: when the page loads, cover it with the game. When the game says `enter`, remove the cover.

1. Wrap your LMS page in one element, for example `<div id="lms-root">`.
2. When the user still has to play, render the page with `<html class="tt-gated">` and the gate below, right after `<body>`.
   (Rendering the class on the server means the LMS never flashes before the gate.)
3. When the user does not have to play, leave all of this out. The game is then not loaded at all.

```html
<style>
  html.tt-gated, html.tt-gated body { overflow: hidden; height: 100%; }
  html.tt-gated body { position: fixed; left: 0; right: 0; top: 0; }
  html.tt-gated #lms-root { filter: blur(6px); pointer-events: none; }
  #tt-gate { position: fixed; inset: 0; z-index: 2147483000; display: flex; align-items: center;
             justify-content: center; background: rgba(16, 12, 52, .58); transition: opacity .4s; }
  #tt-gate.leaving { opacity: 0; }
  #tt-frame { width: 320px; height: 400px; border: 0; border-radius: 16px; background: #5B4BDB; }
  @media (max-width: 600px), (max-height: 440px) {
    #tt-frame { width: 100%; height: 100%; border-radius: 0; }   /* phones: full screen */
  }
</style>

<div id="tt-gate" role="dialog" aria-modal="true" aria-label="Play the floor game to enter the LMS">
  <iframe id="tt-frame" src="teen-taali.html" title="Teen Taali game" allow="autoplay"></iframe>
</div>

<!-- at the end of <body> -->
<script>
(function () {
  var gate = document.getElementById('tt-gate');
  var frame = document.getElementById('tt-frame');
  var lms = document.getElementById('lms-root');
  var html = document.documentElement;
  if (!gate) return;

  html.classList.add('tt-gated');
  lms.setAttribute('inert', '');      // nothing behind the gate can be clicked or tabbed to
  frame.focus();                      // so the keyboard works at once

  function noEsc(e) { if (e.key === 'Escape') e.preventDefault(); }
  document.addEventListener('keydown', noEsc, true);

  window.addEventListener('message', function (e) {
    if (e.source !== frame.contentWindow) return;          // only messages from the game
    var d = e.data;
    if (!d || d.type !== 'teen-taali') return;
    if (d.event === 'complete') {
      // Send it to your server here: d.score (0 to 100), d.stars (1 to 3), d.handed, d.traps, d.cleared, d.seconds, d.round.
      // The same round is sent again with d.repeat === true just before 'enter': keep one record per round.
    }
    if (d.event === 'enter') {
      document.removeEventListener('keydown', noEsc, true);
      lms.removeAttribute('inert');
      html.classList.remove('tt-gated');
      gate.classList.add('leaving');
      setTimeout(function () { gate.remove(); }, 400);     // also stops the game and its sound
    }
  });
})();
</script>
```

`demo.html` does the same and adds a few extras you can copy:
a line of text above and under the game on desktop, a focus loop that keeps the keyboard inside the gate (it tells the game which edge Tab wrapped from, with
`{type: 'teen-taali-focus', edge: 'start' | 'end'}`, so focus lands on the game's last or first control),
the "once a day" memory in the browser, a small "Floor game done today" note on the LMS page, and the demo-only reset.

If the game is on a different web address than the LMS, also check `e.origin` against the game's address.

## How often to show it

The LMS decides. Pick one:

- **Every login.** Show the gate every time the user logs in.
- **Once a day.** Show the gate if the user has no `complete` recorded today. This is what `demo.html` does, to show the idea.
- **Once ever.** Show the gate until the user's first `complete` is recorded.

**Our advice for this version: at most once a day, or a few times a week.** Unlike a quiz, the floor is new every round,
so it does not wear out the same way; but the deck lines repeat, and a mandatory game every login will feel like a chore.

Decide it on the LMS server if you can. `demo.html` keeps the date in the browser (local storage) only to show the idea.
To try each one: `demo.html?gate=login`, `demo.html?gate=day`, `demo.html?gate=ever`.

## Sizes

- Smallest: 300 x 360 px.
- Best: 320 x 400 px, or larger in the same shape (4:5). It scales up cleanly.
- Other shapes work too. The spare space is filled with the game's violet.
- Phones: full screen. `demo.html` switches to full screen below 600 px wide (or 440 px tall).

**Tile sizes.** The floor is 6 x 6 cells of 47 px on the 320 x 400 design, and the whole cell (tile plus the gap around it)
is the place to touch, so a swipe that starts in a gap still picks the right tile. Measured on screen:

| Window | One floor cell | Smallest button |
| --- | --- | --- |
| 300 x 360 (smallest) | 42.3 px | 48.6 px |
| 320 x 400 | 47 px | 54 px |
| 390 x 844 (a phone) | 57.3 px | 65.8 px |
| 1280 x 800 (desktop) | 94 px | 108 px |

Every button (sound, help, the panel's arrow, Your turn, Enter LMS, Play again) stays at 48 px or more even at 300 x 360.
The floor cells are 42 px there: enough for a fingertip, because a swipe only needs to start inside the cell.

## URL options

Add these to the game's address, for example `teen-taali.html?pass=60`.

| Option | What it does |
| --- | --- |
| `?pass=60` | Below 60% the end card offers only "Play again", with an encouraging line. Without it, any score can enter. Use with care: a high bar can keep staff out of work. |
| `?demo=always` | Always play the how-to-play demo first. |
| `?demo=never` | Never play the demo. |
| `?close=1` | Shows a close X that sends `close`. Only for a later, optional (not mandatory) use. Do not use it in the gate. The X gets its own corner slot and the title makes way. |
| `?shuffle=0` | For testing only: the same opening floor, shopper order, missions and trap order every round. The tiles that drop in also depend on how long each step waited, so the same moves played at slightly different moments can drop different tiles. |

`demo.html` passes `?pass` and `?demo` on to the game, for testing: `demo.html?pass=60&demo=always`.

## Events (postMessage)

The game sends these messages to the page that holds it (`window.parent`):

| Message | When |
| --- | --- |
| `{type: 'teen-taali', event: 'complete', score, stars, handed, traps, cleared, seconds, points, round}` | The round ended. `score` is 0 to 100. `stars` is 1 to 3. `handed` is how many shoppers were handed over. `traps` is how many traps dropped in, `cleared` how many were cleared. `seconds` is the playing time. `points` is the match score (bigger for rows of 4 and 5 and for cascades; not part of `score`). `round` counts the rounds played since the game opened (1, 2, ...). |
| `{type: 'teen-taali', event: 'complete', ..., repeat: true}` | Sent again just before `enter`, for the same round (same `round` number). |
| `{type: 'teen-taali', event: 'enter'}` | The player tapped Enter LMS. Remove the gate. It always comes after `complete`. |
| `{type: 'teen-taali', event: 'close'}` | Only with `?close=1`. The gate ignores it. |

So `complete` can arrive twice for one round, and once more for each "Play again". If you save it on your server,
keep one record per `round` (or ignore messages with `repeat: true`).

How the score works: 70 points come from shoppers (4 handed over = all 70, fewer pro rata) and 30 from traps
(every trap that dropped in was cleared = all 30, pro rata; a round with no traps also gets 30, as long as at least one
shopper was handed over: a round with no match at all drops no traps, and should not earn 30%). A trap still on the floor
at 0:00 counts as missed. 3 stars from 85%, 2 stars from 60%.
Archie's line: three stars "Archie clapped three times. That is his maximum.", two "Two claps from Archie. He is saving the third.",
one "One clap. Archie is warming up.", and "Archie is still holding the door." when nobody was handed over.
The "To remember" line: a trap left on the floor (or one that took 6 seconds or more to clear) gives that trap's line;
otherwise the step that waited longest gives its deck line ("Acknowledge shoppers promptly.", "Ask one broad question and
listen to the whole answer.", "Listen first. Understand the need.", "Walk with the shopper and use an open-palm gesture.",
"Complete the handover."); a quick, clean round gets "Don't just point. Make the connection."
The messages carry no personal data. Check `e.source === iframe.contentWindow` so you only act on messages from the game.

## Score and SCORM

This version has no SCORM. To keep scores in the LMS, listen for `complete` and save it on your server.
The game also keeps the player's best score and "demo seen" in the browser's local storage.
It still works if storage is blocked; it just cannot remember that the demo was seen.

## How strict is the gate? (please read)

The gate runs in the browser. It stops normal use: there is no button, link or key that gets past it.
But someone who knows how can get past it, for example with the browser's developer tools
(remove the cover, or send a fake `enter` message).
Clearing browser storage does not help them: it only makes them play again.

For real enforcement, record the `complete` event on the LMS server, with the user and the time,
and let the server decide whether to show the gate. Even then, a determined user could fake the message.
Treat the game as a training step, not an exam.

Also:
- Esc does nothing while the gate is up (inside the game, Esc only puts a picked-up tile down). Inside the gate the
  browser's Back button leaves the page as usual (the game adds no history entry there); the gate shows again on the next
  visit until a round is done. Opened on its own as a pop-up (not in a frame), the game holds the first Back press so it
  is not closed by accident.
- If the game file cannot load, the gate stays up. Keep a quick way to switch the gate off on the server.

## Offline and fonts

The game works without internet once the page is open. It asks Google Fonts for the Poppins and Figtree fonts.
The request does not hold the game up: if it fails or hangs (a slow or filtered store network), the game starts at once with
the device's own font and switches to Poppins if it arrives. Nothing else is loaded from outside.
All sounds are made in the browser (no audio files), including Archie's clap. Sound is off at the start; the speaker button turns it on.
`demo.html` loads nothing from outside.

## Browser support

- Desktop: current Chrome, Edge, Firefox and Safari.
- Phones: Chrome on Android, Safari on iPhone.
- Internet Explorer is not supported.
- `inert` (which blocks the page behind the gate) needs Chrome 102, Safari 15.5 or Firefox 112 or newer.
  On older browsers the cover still blocks clicks.

How to swap: drag or swipe a tile toward a neighbour (a quarter of a tile is enough), or tap a tile and then the
neighbour. Keyboard: Tab reaches the floor (one Tab stop for the whole floor), the arrow keys move between tiles,
Enter or Space picks a tile up, then an arrow key (or Enter on a neighbour) swaps it; Esc only puts it down.
While a deck line is showing, Enter or Space moves it on. Focus stays inside the gate.
During the demo the floor is out of the Tab order, and Enter starts the round as soon as "Your turn" shows.
Keyboard players get the same Back protection as touch players when the game is opened on its own.
Every tile is read out by screen readers (its row, column and step, or "a trap"), and so are the steps ticked, the lines and the end card.
Reduced-motion settings are respected: tiles move quickly without bounces, nothing shakes, and there are no confetti dots.

## Change the texts

Open `teen-taali.html` in a text editor.
All the words are in **the CONTENT block at the top of the script**:
the five step names, the trap names, the deck's openers, what a shopper says at Listen, the section signs, the hand-over
lines, the trap lines, Archie's lines, the end-card lines, the "To remember" lines and the demo captions.

- Change only the text inside the quotes. Keep the commas and brackets.
- Keep it short: demo captions up to 5 words. A long deck line can be split into two parts (like the busy-specialist line).
- No exclamation marks.
- The deck lines are the deck's exact words. Change them only if the deck changes.
- A line that is a DON'T (now only "Call out offers from a distance.") is listed in `dontTraps`, so it always shows
  with the red "Don't" chip. Keep that, or the line reads as an instruction to do it.

The shoppers and their missions are in `SHOPPERS` and `MISSIONS` just under CONTENT. The round length, the drop bias and
the trap timing are in `TUNE`; the score split is in `SCORE`.

Save, then open `demo.html` to check.

## Tuning (how hard it is)

New tiles lean toward the glowing step, so nobody stays stuck:
- a base share of 36% of new tiles are the glowing step's type (with five types, 20% would be no lean);
- once that step has waited 2 seconds of play, the share climbs over 3 seconds to 80%;
- if the glowing step has had no possible match at all for 6 seconds, at least 70% of new tiles are that type.

A slow player waits longer per step, so the second rule helps them more than a quick player. The lean stops at 80%
rather than every new tile, so a refill is seldom one type from top to bottom: more steps come from the player's own swap
and fewer from a cascade that does the step for them.
At a hand-over the deck line opens as soon as the floor is still (at least 0.6 seconds after the tick, `handWait`), so the
clock does not run on while the floor is locked for the walk.
Traps: the first drops in about 8 seconds into the round, then one every 8 to 11 seconds, at most 2 on the floor and 4 in
a round, never in the first refill and none after 36 seconds of play (so the last one can still be cleared). That makes 3 a
round, sometimes 4.

Measured with a test bot that plays real rounds through the game's test hooks, on the game clock:

| Player | How it plays | Shoppers handed over (mean, median, spread) | Score | Traps cleared |
| --- | --- | --- | --- | --- |
| Casual first-timer | one move every 2.5 s; looks for the glowing step only 40% of the time, otherwise any match | 2.8, median 3 (of 40 rounds: 2 in 14, 3 in 20, 4 in 6) | 78% mean; mostly 2 stars (31 of 40), 6 with 3 | 94% |
| Sharp player | one move every 1.5 s; always the glowing step first | 5.2, median 5 (of 40 rounds: 4 in 8, 5 in 18, 6 in 11, 7 in 3) | 99.6% mean; 3 stars | 98% |
| Ignores the glow | one move every 2.5 s; any match, never looks at the chain | 2.2, median 2 (of 40 rounds: 1 in 2, 2 in 29, 3 in 9) | 67% mean; 2 stars, never 3 | 95% |

So the stars follow how the player plays: 1 star means hardly matching, 2 means matching without following the order,
3 means following the glow. The bots made about the number of moves you would expect once the floor's own time is
counted (19 and 29 moves in 45 seconds). Repeated runs of 40 to 60 rounds vary by about 0.15 shoppers (the casual bot
measured 2.7 to 2.8 over 140 rounds). The bias numbers are in `TUNE` if the client
wants it harder or easier: lowering `bias` moves both players down by about the same amount; the wait rule mostly helps
the slower player. Since a round with 4 shoppers already earns the full 70 points, a sharp player's 5th and 6th shopper
show on the end card but do not raise the score.

## Originality

Teen Taali is our own swap-and-match game. Nothing is taken from any other game: no candy or sweets, no names, words or
sounds from other games, no special pieces (no striped, wrapped or colour-bomb style tiles, no row or column blasters,
nothing that clears a whole colour), no jelly or chocolate, no level map and no lives. The only obstacle tiles are our
three ushering traps, drawn for this game.
A row of 4 or 5 only earns more points and a bigger clap. The game's own twists are the ushering chain in the walk-in
strip, the three trap tiles cleared by a match beside them, and Archie's claps. All art is the Welcome Floor cast drawn
for these games; all sounds are made in the browser.
