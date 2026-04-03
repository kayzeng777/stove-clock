# Project brief

A responsive embeddable clock widget built from photos of my apartment stove.
Instead of fonts, every digit (0-9), colon, and empty state is a real photo
of the stove's actual clock display. The clock shows live time in 12-hour
format with no AM/PM label. Output is a single self-contained HTML file
that can be embedded anywhere via <iframe>.

The goal is a collage feeling — real photos stitched together to show
live time, as if the stove itself is on the page.

# Assets

All images are in the /image/ folder.

Background: image/stove.png
Digits: image/number0.png through image/number9.png
Colon: image/colon.png
Empty: image/empty.png

All images will be converted to base64 and inlined into the HTML
so the final file is fully self-contained.

# Layout

- Figma design link: https://www.figma.com/design/sWNPlGEPlrFJcKnpqd34d5/apartment_clock?node-id=8-18&t=9uT32fjfaJQpoRri-4
- Layer names in Figma: digit-1, digit-2, colon, digit-3, digit-4
- Read digit positions and sizes from Figma, convert to % relative to container
- Container locked to stove.png aspect ratio
- Use <img> tag for background (not CSS background-image)
- All positioning in % relative to container, no px for layout
- Digits sit on top of background using position: absolute

# Time logic

- 12-hour format, no AM/PM
- Hours: 1–12 (10am and 10pm both show as 10:00)
- Minutes: always 2 digits (e.g. 09, 30)
- Single-digit hour (1–9): digit-1 shows empty.png, digit-2 shows the hour
- Double-digit hour (10–12): digit-1 shows 1, digit-2 shows 0/1/2
- Update every second via setInterval

# Rules

- Single HTML file, no frameworks, no npm, no build step
- Vanilla JS only, no libraries
- No canvas, no SVG drawing, just <img> src swapping
- No text or font rendering for the clock display
- Never split into multiple files
- Never add a dependency without asking first
- Keep JS under 100 lines
- If there are multiple ways to solve something, tell me the options first
- Prefer the simplest solution always
