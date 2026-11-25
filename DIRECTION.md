# DIRECTION — Empire Interior Design Studio (mockup)

A rebuild of the Kitchen InteriO template for **Empire Interior Design Studio**, a Pune
interior-design studio. This is a mockup: facts are from the Google listing only, and every
unverified detail is in the gaps list for the client to confirm. The structure, 3D build,
finish picker, quote form, progress rail, section labels and mobile call bar are kept. The
header and call-bar code are kept verbatim (colour variables only), per LESSONS.md.

Empire is **not** a kitchen fitter — it is a full-flat interior designer. The hero, the
palette, the 3D subject, the finishes and the "what we make" rows are all re-cut to what the
business actually shows: living-room feature walls, lit niches, cove lighting, wardrobes, and
their stand-out piece — a dining table that folds down out of the wall.

---

## 1. Three reference URLs (one borrowed clause each)

1. **https://www.livspace.com** — borrow only the *room-by-room storytelling*: each space shown
   as one large photo with a small room label, rather than a gallery wall.
2. **https://www.homelane.com** — borrow only the *single repeated primary action* (one clear
   "get a design consultation" call that follows you down the page).
3. **https://beautifulhomes.asianpaints.com** — borrow only the *warm, evening-lit editorial
   tone* of Indian-flat photography (cove light and lamps on, not flat daylight).

Nothing else is taken from them — not their type, colour, grid or motion.

## 2. What it feels like (one sentence)

> It feels like stepping into a Pune 2BHK at 7 p.m. on handover day — the cove lights are
> already warm, a table has folded down from the wall for dinner, and every niche is lit.

(No "premium / modern / clean / sleek" — and nothing here would describe a generic company.)

## 3. Type and colour

**Display:** **Marcellus** (Google Fonts, 400) — an architectural, inscriptional serif; warm
and understated-luxe, right for a design studio. *Not* Inter/Roboto/Arial/Helvetica/Open
Sans/Montserrat/Poppins/Playfair/system-ui, and different from the four earlier display faces
(Fraunces, Bricolage Grotesque, Young Serif, Zilla Slab).

**Body:** **Mulish** (400/600/700) — a humanist sans, warm and legible small. Different from
the earlier bodies (Instrument Sans, Figtree, Hanken Grotesk, Karla).

**Devanagari:** **Hind** (400), for एम्पायर इंटीरियर डिजाइन स्टूडियो. Different from Mukta
(Kitchen InteriO) and Tiro Devanagari Hindi (Harsiddhi).

**Five hex values** — set by eye from region-median samples of the owner photos (their photos
are shot under warm incandescent light, so raw medians skew orange; the measured value is
recorded next to each, the site value is the daylight-true reading):

| Token | Site value | Role | Measured median (warm-lit) |
|---|---|---|---|
| limestone | `#EFE4CC` | warm gold-parchment page background | p9 cream wall `#F0D6AD` |
| espresso | `#21190F` | ink text + the darkest (3D build) section | hero panel/floor shadow `#150A07`–`#4B2F28` |
| walnut | `#4E3826` | deep warm-brown "Find us" block + frames | p0 `#8C6E50`, p9 `#9D6A3F` |
| brass | `#C0893B` | gold accent, cove glow, accent-on-dark | cove-light glow ≈ `#E8B869` |
| peacock | `#235E62` | cool jewel accent + the reviews block | hero teal sofa `#5F8194` (warm-cast) |

Distinct from the four earlier palettes: limestone carries a gold undertone vs Kitchen
InteriO's grey-cream sand `#EFE9DD`; peacock `#235E62` is greener/lighter than Bhumi's teal
`#123F3A` and Mangesh's petrol `#1D5870`; the brass + walnut + espresso trio is new.

**Section-colour plan** (a new order — not Kitchen InteriO's light/dark-mocha/light/dark-ink/
paper/dark-mocha): hero **limestone** → 3D build **espresso** (darkest, so the glow pops) →
what-we-make **limestone** → reviews **peacock** (a coloured review block) → process
**limestone-deep `#E7DABB`** → find-us **walnut** → footer **espresso**. No single dark colour
is reused across build/reviews/visit. On every dark section the "on" marker, rail fill and
focus ring use **brass**, never a red.

**3D finishes** — taken from Empire's own feature-wall panels (the finish picker repaints the
fluted feature wall, not kitchen shutters):

| Finish | Swatch | From |
|---|---|---|
| Walnut flute | `#5A3A22` | door frames, TV-wall borders (p0, p4, p9) |
| White flute | `#E9E6DF` | the hero feature wall |
| Grey flute | `#8E8C88` | p0 grey reeded TV wall |
| Marble | `#E6E1D6` + faint veins | p3 / p5 laminate walls |

## 4. One signature move

The one animated moment is the existing scroll-driven 3D build, re-subjected to a **living-room
feature wall** going into an empty flat (base console → fluted feature wall → floating TV + lit
niches → false ceiling, curtains + cove reveal). Its climax — the signature a visitor would
describe — is Empire's own party trick: **on the last step the wall-mounted table folds down
out of the feature wall (a rotation) while the cove light, the niche lights and a floor-wash
come up together — the room turns from a daytime shell into an evening-lit room, set for
dinner.** Transform + opacity only; one ScrollTrigger progress value drives the whole thing and
the progress rail; `prefers-reduced-motion` lands it on the finished, lit state.

This differs from Kitchen InteriO's signature (its 3D kitchen switched its own counter light
on): Empire's is a *fold-down transform* of a real, repeated Empire product, not just a light.

**Static motif (differs from plywood-edge / LED-strip / chevron-seam / fluted-rib):** the
**warm cove reveal** — a brass hairline at each section seam with a soft glow rising
*continuously* into the block above (a gradient wash, not a strip of dots), the reveal Empire
runs between ceiling and wall. Section labels carry a small **arched-niche marker** (a brass
half-oval), echoing their backlit niches and oval nameplates.

---

## 5. The facts found (Google listing, built-in browser)

- **Listing name (exact):** `Empire Interior Design Studio`
- **Devanagari (listing):** `एम्पायर इंटीरियर डिजाइन स्टूडियो`
- **Category:** Interior designer
- **Rating:** 5.0 from **20** Google reviews
- **Phone:** 098609 96046 → `+91 98609 96046` → `tel:+919860996046`
- **"Website":** the only link on the listing is WhatsApp — `wa.me/919860996046` (same number)
- **Hours:** Monday–Saturday **10 AM–8 PM**; **Sunday closed.** (Goes in schema
  `openingHoursSpecification`; Sunday omitted.)
- **Address:** **none published.** This is a service-area business — no street address, no
  shopfront photo. The map pin sits loosely near the Mula River / Sapras Rd area of Pune
  (~18.5531, 73.8645, but that is a low-zoom centroid, probably not a real office). → gap.
- **Designer named in reviews:** **Mr. Shubham Gaikwad** (called an architect / interior
  designer; "the Empire team"). Per LESSONS, kept **off the page** until the client confirms.
- **Review tags (Google):** *2bhk flat interior, enjoyable experience, creativity, expertise,
  flat, space* (each ×2).
- **Brand mark:** a dark circular crest reading "EMPIRE" (the Google profile avatar). No
  shopfront or signboard exists to compare, so the real wordmark is unconfirmed. → gap.
- **Location clue:** a reviewer's project was at *Kohinoor Sapphire, Tathawade* (PCMC/Wakad
  corridor) — suggests Empire serves Pune & Pimpri-Chinchwad, but areas served are unstated.

**Reviews readable: 3 of 20** (the other 17 need a Google sign-in). Quoted exactly:

1. **Abhijeet Pahapalkar** — Local Guide · 78 reviews · 301 photos — a year ago:
   *"Mr. Shubham Gaikwad is a very talented and Innovative architect/interior designer… He
   works with a very experienced and expert team and brings new ideas. He doesn't force his
   ideas on his client but collaborates with them as per their budget."* (names the designer —
   paraphrase on the page without the name until confirmed.)
2. **Omkar Dharwadkar** — Local Guide · 25 reviews — a year ago:
   *"Thank You for Creative Interior Work… excellent designer never ever seen before… Thanks
   again to empire team"* — owner replied.
3. **Prasad Abhang** — a year ago:
   *"Empire Interior Design Studio did an amazing job on my home. They listened to my needs,
   offered great suggestions, and created a beautiful, cohesive space. The entire experience
   was smooth and enjoyable. I highly recommend their expertise!"* — owner replied.

Owner reply voice (exact): *"Thanks for your wonderful review, we're glad you [had] a great
experience and look forward to working with you again 😊"*.

---

## 6. Photos table

Seen: **11 of 55** owner uploads (business contributor profile
`maps.google.com/maps/contrib/103915797785392157583` = all owner; plus the place-page hero,
owner, "Jan 2025"). The place page caps its grid at ~10 and the contributor grid is
virtualised; 11 is a representative spread across their room types. **No stock-library
watermarks** seen on any. **No obvious 3D renders** — all read as real photographs (real
ceilings, reflections, curtains, minor site mess). Export plan: `.webp` in `img/`, explicit
width/height, cropped to aspect with a chosen anchor.

| File (planned) | Source | Shows | Flag |
|---|---|---|---|
| `feature-teal.webp` (hero) | place page, owner, Jan 2025 | Living room: white fluted TV feature wall, walnut border, warm cove light, **teal L-sofa**, swirl rug, chandelier | real; the signature look |
| `feature-grey.webp` | owner #0 | Living room: grey reeded TV wall, round marble medallion, cove light, grey tufted sofa | real |
| `table-open.webp` | owner #5 | **Fold-down wall dining table, open** — cream cabinet, walnut frame, gear-face clock, kitchen glimpse behind | real; signature product |
| `table-folded.webp` | owner #1 | Same table **folded flat** to the wall (space saved) | real; pairs with above |
| `niche-console.webp` | owner #9 | TV unit with lit open niches + floating console, beige curtains, marble floor | real |
| `living-niche.webp` | owner #6 | Living/dining: lit shelf niches, false-ceiling cove, curtains | real |
| `wardrobe.webp` | owner #2 | Bedroom sliding wardrobe (cream + walnut), false ceiling | real |
| `wall-art.webp` | owner #8 | Two framed marble panels + brass wall sconces | real |
| `empty-handover.webp` | owner #7 | Empty living room at handover: curtains, cove, art, marble floor | real; good "process" shot |
| `foyer-door.webp` | owner #4 | Entrance: dark walnut safety door with **scalloped art-deco grille**, backlit oval nameplate | real — **but shows a client's family name ("विड्ये परिवार") + flat no. 407.** Crop the nameplate out, or drop. → gap |
| `og-image.jpg` (1200×630) | from `feature-teal` or `feature-grey` | the most legible landscape, for social | — |

---

## 7. Labelled gaps (ask the client)

1. **Which name/logo to display.** Listing says "Empire Interior Design Studio"; the only mark
   is a circular "EMPIRE" crest avatar — no signboard to confirm. Get the official wordmark/
   logo and the exact legal name.
2. **No address.** Is there a studio/office a client can visit, or is it site-visit-only? Full
   address + a map pin, or confirm "we come to you". The current map centroid is unreliable.
3. **Areas served.** Reviews point to Tathawade/PCMC + Pune. Confirm the real service area for
   the form's "area / society" field and the copy.
4. **Designer's name.** Reviews name "Shubham Gaikwad". OK to put him (and a photo/title) on
   the site? Held off until confirmed.
5. **Foyer photo consent/crop.** The entrance photo shows a client's family surname and flat
   number. Crop the nameplate, or get an unidentifiable shot, or drop it.
6. **WhatsApp.** Confirm `+91 98609 96046` is on WhatsApp (the listing's own "website" points
   there, so almost certainly yes).
7. **Kitchens?** They show a *glimpse* of kitchens behind the dining table but post no kitchen
   as a project. Do they do modular kitchens, or design-only + partner fit-out? Affects the
   "what we make" rows.
8. **Services & specifics.** Do they do civil/false-ceiling/electrical, or joinery only? Any
   warranty, typical timelines, free first consultation, Instagram/website? None are on the
   listing.
9. **Lead email.** `apps-script.gs` needs the client's email so enquiries reach them.

## 8. Build notes (after OK)

- Rework the Three.js scene from *kitchen* to *living-room feature wall*; keep one
  ScrollTrigger, the rail, the picker, and LESSONS' 3D rules (camera-radius ramp, step-05
  clearance above the call bar, faint veins ≤.4, rod-to-ceiling for the pendant, the last step
  is a real Empire product = the fold-down table as a transform then the glow ramp).
- Replace every Kitchen InteriO string: name, Devanagari, phone (8928904904→9860996046),
  address block → service-area copy, hours (every day → Mon–Sat, Sun closed), the four reviews,
  JSON-LD schema, WhatsApp text/number, footer, form options (kitchen shapes → room set), the
  wardrobe gap note, `apps-script.gs` subject/notify, and the og-image.
- `.claude/launch.json`: name `empire-interior`, port `5178` (and in runtimeArgs).
- Then run the LESSONS checks (sideways scroll, step-05 clearance, scripted contrast, leftover
  search) at 1366×800 / 375 / 320×640, and report what was actually seen.
