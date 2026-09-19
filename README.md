# Walima — Ahmad Shakeeb &amp; Dr. Laalain Fatima

A standalone, Walima-only invitation site. Single static file, no build step,
no dependencies, no backend. Open `index.html` in a browser and it works.

This is a **separate project** from the full three-event invitation. It has its
own repository and its own deployment, so the two are never entangled — a change
here does not touch the other site, and vice versa.

---

## The event

|          |                                                        |
|----------|--------------------------------------------------------|
| Event    | Walima Reception                                        |
| Day      | Sunday                                                  |
| Date     | 25 October 2026                                         |
| Time     | 5:30 PM onwards                                         |
| Venue    | Aura Grande Event Complex                               |
| Address  | 2 Service Road E, Golra NPF, E-11/4, Islamabad          |
| Hosts    | Mr. &amp; Mrs Zahid Mahmood and family members          |

RSVPs are sent to WhatsApp **+92 333 5101170**.

The countdown targets **25 October 2026, 5:30 PM PKT**.

---

## What it does

- Ornate gate intro — twin gold-lattice doors that swing open from a wax seal
- Background music, starting on the tap, with a floating toggle
- Bismillah header, animated gold mandala, drawn Mughal arch
- Live countdown to the Walima
- A single event card with **Location** and **Add to Calendar** buttons
- RSVP form that composes a WhatsApp message — no backend needed
- Falling rose petals and gold dust on canvas, scroll reveals, card tilt

---

## Personalised links

Add a guest's name to the link and the page greets them and pre-fills the RSVP.
The page then **wipes the query string from the address bar**, so the guest
never sees the code.

```
https://your-site.com/?to=Ahsan%20Bhai
```

Spaces must be written as `%20`. The name is remembered in `sessionStorage`, so
a refresh keeps it.

There is no `event=` parameter here — this site is the Walima only. (The
three-event site has that switch; this one does not need it.)

---

## Optional files

Drop these into `assets/` — each is optional and the site degrades cleanly
without it:

- `music.mp3` — replaces the online background track
- `walima.jpg` — the printed Walima card. When present, a **View Card** button
  appears and opens the image full screen. When absent the button removes
  itself.

---

## Editing content

Everything lives in `index.html`.

- **Date, time, venue** — in the `<article class="ev">` block
- **WhatsApp number** — `var PHONE = '923335101170';` near the bottom of the script
- **Countdown target** — `var target = new Date('2026-10-25T17:30:00+05:00')`
- **Colours** — the `:root` block at the top of the `<style>`
- **Map link** — the `Location` button uses a Google Maps *search* query, which
  resolves to the right venue. Swap in an exact `maps.app.goo.gl/...` pin if you
  prefer.

---

## Deploying

Static hosting, nothing to build.

**Vercel**

```bash
npx vercel --prod
```

Or drag the folder onto [vercel.com/new](https://vercel.com/new). `vercel.json`
is already set up.

**Netlify** — drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop).

---

## Local preview

```bash
npx --yes serve -l 4322 .
```

Then open `http://localhost:4322`.
