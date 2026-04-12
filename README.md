# FrameFrenzy

Frame Frenzy is a brwoser game that turns a YouTube video into a sliding puzzle.

The clip keeps playing. The board is scrambled. You have to rebuild the image before the video runs out!

## How To Play

1. Paste a YouTube link.
2. Pick a grid size.
3. Hit Drop In.
4. Slide the tiles until the picture is back in the right order.

The round ends the moment the board is solved, or when the video ends.

## What Makes It Fun and Unique

- The puzzle is built from a live video, not a still image.
- The round starts with a final tap after the countdown so audio can begin reliably.
- The board keeps moving the whole time, so you are solving motion as much as shape.

Winners get a copyable/sharable they can use to challenge their friends:

🧩 Frame Frenzy 3×3
✅ 1:51 | 118 moves

🟩🟩🟩
🟩🟩🟩
🟩🟩⬛
https://framefrenzy.games/?v=E4WlUXrJgy4&g=3

## Notes

- Some YouTube videos cannot be used because their owners disable embedding.
- The round uses one final tap after the countdown so sound can start reliably across browsers.
- Touch, mouse, and keyboard controls are supported.

## Running It Locally

This is a static site. For the most reliable local test, serve the folder over HTTP:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/framefrenzy.html`.
