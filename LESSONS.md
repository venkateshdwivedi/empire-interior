# Lessons from earlier builds (Bhumi → Mangesh → Harsiddhi → Kitchen InteriO)

## Keep exactly as is (proven on a real phone)
- Header: `.top{position:sticky}`. Do NOT switch it to position:fixed.
- Call bar: position:fixed bottom + the visualViewport script that keeps it on the
  visible bottom edge. Do NOT remove that script.
- Do NOT add ScrollTrigger.config({ignoreMobileResize:true}).
These were "improved" once on Mangesh and broke on a real phone; reverting to the Bhumi
code fixed it. Browser-pane tests passed both times, so only a real phone shows this.
- Changing only the colour variables inside the header/bar CSS is fine (done on Harsiddhi
  and Kitchen InteriO).
- One exception found on Kitchen InteriO: the header's `background:rgba(...,.97)` lets a
  dark section show through as it scrolls under. Set the header background to a solid
  colour. That is still a colour-only change.

## Finding the photos (do BOTH sources)
- Use only photos uploaded by the business's own Google profile. In the Maps photo viewer,
  an owner upload shows a "View <business name>'s profile" link (a /maps/contrib/ link).
  A photo credited to a customer's name: skip it, even if that customer posted most photos.
- **The place page's photo grid caps at 10 items — but the business's own contributor
  profile loads a DIFFERENT 10.** Open `https://maps.google.com/maps/contrib/<id>` (the id
  is in that "View …'s profile" link) and then its Photos tab. On Kitchen InteriO this
  turned 8 owner photos into 15. Always do both, then dedupe by md5 — the two sets overlap.
- Everything on the contributor profile is by definition an owner upload. On the place
  page, check attribution per item: one "owner" video there belonged to another business.
- Download at native resolution. The viewer URL carries `!7i<width>!8i<height>`, and the
  thumbnail URL ends `=w203-h359-k-no`; swap that suffix for `=w<W>-h<H>-k-no`.
- Say how many of the total you saw ("15 unique owner images of 94 listed").

## Judging the photos
- Flag possible 3D renders (flat perfect lighting, CG plants, nothing real through windows,
  no dust or wires). Label them "Design render, not a photograph" on the page itself, not
  just in DIRECTION.md.
- **Check every render for a stock-library watermark** (123RF, Shutterstock, iStock, Adobe).
  Two of Kitchen InteriO's uploads were bought stock, not their work. Those never go on the
  site at all — list them as a client question and say the listing should drop them.
- Mid-install photos (protective film, tools, bags, builders' dust) are useful: caption them
  honestly. A loose wire left in frame reads as real; keep it and say so.
- Crop out phone watermarks (e.g. "Galaxy S26") and identifiable people (workers, family);
  list the crop as a client question.
- Furniture in a photo may be bought, not made by them (sofas, lamps, art): caption only what
  they made, and ask.
- A render can still earn a place if it is honest about its job — Kitchen InteriO's turquoise
  kitchen render sits next to process step 3, "this is the drawing you approve".
- Export as .webp in img/ with explicit width/height. Portraits 900x1125, strip 700x875,
  landscape 1200x800. Crop to aspect with a chosen anchor, don't centre-crop blindly.
- Make img/og-image.jpg (1200x630) from the most legible landscape owner photo.

## Reviews & facts
- Quote short, exact lines from Google reviews; first name + initial. Keep their spelling.
- **The limited view shows about 5 reviews and "See more reviews (N)" does nothing without
  a sign-in.** Read what you can, record them all in DIRECTION.md, and say on the page how
  many of the total are readable.
- Thin listings happen (1 review, no hours, no website). Show it honestly:
  "5.0 from 1 Google review so far", "Hours not listed yet. Please call before visiting."
  Never pad with invented reviews or a fake hours line.
- **The listing name is often the brand plus keyword stuffing** ("Kitchen interiO, MODULAR
  KITCHEN, WARDROBE."). The shopfront photo usually settles the real name — zoom into the
  signboard. Put the brand in `name`, the exact listing string in `alternateName`, and put
  "which name to use" in the gaps list.
- The listing's Devanagari and the signboard's Devanagari often disagree. Record both, use
  the sign's, ask.
- **The owner's or designer's name usually appears only in reviews, never on the listing.**
  Record it, but keep it off the page until the client confirms it.
- Anything not on the listing goes under "Labelled gaps": WhatsApp, Instagram, website,
  owner name, years in business, brands, warranty, prices, free site visit, showroom vs
  office, areas served, job durations.
- Don't put the Google rating into schema aggregateRating. Hours DO go in
  `openingHoursSpecification` when the listing publishes them; omit if it doesn't.

## Colours and finishes
- Take the five site colours and the 3D finishes from the client's own photos.
- **Sample by region median, not a point average.** A 5x5 average lands on a highlight or a
  shadow and returns nonsense (a white worktop sampled as #131313). Crop a rectangle of the
  material and take the median of each channel.
- Set the swatch hexes by eye from those medians and record the measured value next to them
  in DIRECTION.md.
- Look for a pairing the client repeats. Kitchen InteriO put mocha gloss bases under white
  gloss lofts in four photos, so the finish picker repaints only the base shutters and the
  step copy says why. More specific and more honest than repainting everything.
- A dark section works well (Kitchen InteriO's build section is the mocha shutter colour),
  but then the "on" step marker, the rail fill and the focus ring all need a light accent,
  not the red one. Check contrast on every one of them.
- If no owner photo shows the main product, don't fake one: use a labelled "photo to come"
  gap in that row and let the 3D build carry it.

## Layout fixes already learned
- A hero photo pushes the quote form a full screen down on phones: hide it under 900px
  and show it further down the page instead (a .narrow-only copy in a strip).
- Focus outline must stay visible on dark sections too.
- 3D marble veins stay faint (alpha ≤ .4) or they look like cracks.
- At 320px the brand name must not wrap; shrink it. A longer brand needs two steps
  (≤460px and ≤360px), not one.
- h1: use text-wrap:balance so no single word sits alone on a line. Aim for three lines at
  1366 — size the clamp so it does, rather than letting it run to four.
- A caption sitting over the 3D canvas fails contrast against the light floor. Give it a
  dark chip (`background:rgba(ink,.82); padding:3px 8px`), and shorten it on narrow screens.
- A repeating mask band reads as flutes at 5px on / 4px off; at 7px/6px it reads as dashes.
- Short screens while the build section is held on screen during scroll:
  desktop ≤880px tall → hide the build sub-line;
  phone ≤700px tall → hide the build section label, shrink the build h2 AND the stage
  height, and shrink the step paragraph. Shrinking the h2 alone is not enough — at
  320x640 step 05 still clipped under the call bar by 10px until the stage came down too.

## 3D stage (Three.js)
- Anything hanging from the ceiling needs its rod to reach the wall top, plus a small
  ceiling rose. There is no ceiling mesh, so a short rod leaves the lamp floating.
- Ramp the camera radius with progress (`r = radius * (1 + .12 * p)`) or whatever is added
  last fills the frame and hides the rest of the room.
- The last step should be a thing the client actually makes, not a generic flourish. Model
  it as transform first, then an opacity ramp on an emissive plane plus a PointLight.
- Keep the whole build on the one ScrollTrigger progress value. Never add a second trigger.

## Borrowed from Eat Move Rest (already in index.html, keep it)
- The page told as one project: small section labels ("Call · Site visit", "Making",
  "Fitting", "Handover", "Find us"). Add "Years later" only if a review supports it.
  No durations unless the client gives them.
- A thin progress rail beside the 3D stage that fills (scaleY) from the same ScrollTrigger
  progress value as the build. It is part of the one animation, not a second one.
- Flat colour blocks per section, taken from this client's own materials. No colour fades.
- One team card only if the client gives a real name and photo. At most one handwritten aside.

Do NOT borrow: scrolling marquees, breathing circle, drag carousel, loading screen.

## Must look different from earlier sites
- Bhumi: Fraunces + Instrument Sans; cream #F4EEE2, teal #123F3A, saffron #B5461B;
  plywood-edge motif; headline "Kitchens built to your walls, not a catalogue."
- Mangesh: Bricolage Grotesque + Figtree; marble #F1F0EC, taupe #4E443E, petrol #1D5870,
  amber #F3C975; LED-strip motif; headline "Bare walls in. A finished home out."
- Harsiddhi: Young Serif + Hanken Grotesk (+ Tiro Devanagari Hindi); chalk #EDF0EA,
  sage #CFDAD2, walnut #2B1D16, rose #8C3A45, navy #233041; chevron-seam motif
  (two peaks where sections meet); headline "Measured once. Fitted room by room."
- Kitchen InteriO: Zilla Slab + Karla (+ Mukta Devanagari); sand #EFE9DD, ink #1F1C19,
  mocha #6B5D50, rib #8E5C34, sign-red #7A1F23; fluted-rib seam motif (vertical ribs
  interlocking where sections meet); headline "Your kitchen, finished on the date they
  promised."; signature move = the 3D kitchen ends by switching its own counter light on.

New site needs its own display + body fonts, five new hex values, its own static motif,
its own headline, its own signature move, and a finish set taken from its own photos.
Also pick a new section-colour plan — don't reuse "light hero / dark build / dark reviews"
in the same order if the last site did.

## Previous clients' details (search for these before saying done)
Harsiddhi, Harsddhi, हरसिद्धि, 63773, 6377344815, Katraj, Rajas, 411046, Swaropsingh
Kitchen InteriO, interiO, intériO, किचन इंटेरीओ, किचन इंटेरियो, 89289, 8928904904,
Kothrud, Bhusari, Paud Road, Ishana, Shinde Nagar, 411038, Raj Gunjal, Paarshva,
Govind Patil, Deepa Gandre, Vikas Pawar, GQ5R

Keep the one "Bhumi" in the call-bar code comment — it records why that script must not be
rewritten.

## Dev-server ports used so far
Harsiddhi 5175 · Kitchen InteriO 5177 · **next build: 5178**
Set both `name` and `port` in `.claude/launch.json`, and the port in `runtimeArgs`.

## Checks before saying done
1. 1366×800, 375×812 and 320×640.
2. Scroll the whole page; tab through it; read the console.
3. Submit the form in preview mode (empty once, then filled).
4. No sideways scroll at any width — assert it:
   `document.documentElement.scrollWidth === innerWidth` and no element whose
   `getBoundingClientRect().right > innerWidth + 1`.
5. At the end of the held build section, step 05 and its text sit above the call bar —
   assert it: `li5.getBoundingClientRect().bottom <= bar.getBoundingClientRect().top`.
6. Script the contrast check, don't eyeball it: walk every text selector, compute relative
   luminance of the computed colour against the nearest non-transparent background, and
   apply 4.5 (or 3.0 for ≥24px, or ≥18.66px bold).
7. Search for the previous clients' details (list above).
8. Then test on a real phone over Wi-Fi. Still the only check that catches the header and
   call-bar regressions.

## Working notes for the browser pane
- Scrub a pinned section by setting scrollY from the trigger's own numbers —
  `const st = ScrollTrigger.getAll()[0]; scrollTo(0, st.start + (st.end-st.start)*0.98)` —
  instead of wheel-scrolling. Far fewer round trips and you land exactly where you meant.
- After a CSS edit that changes the stage height, ScrollTrigger re-measures on load. Call
  `ScrollTrigger.refresh()` and wait before trusting a progress reading.
- `javascript_tool` is a REPL: a top-level `return` makes the whole call return undefined.
  End with a bare expression.
- Google Maps panels need `innerText` off `[role="main"]`; `get_page_text` returns nothing.
