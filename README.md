# A song that never leaves the city

**Bose × Kota The Friend — Long Beach**

An example city landing page for the *A song that never leaves the city* campaign, built to be linked from the pitch deck.

## The concept

Kota travels city to city writing a song for each place. The songs are never streamed — they exist only in the city they were written for, and only through Bose speakers. This page is how someone who wasn't at the show still hears the song: scan a QR code in Long Beach, land here, and press play **on the speaker itself**.

Every city gets its own version of this page. Long Beach is the example.

## The interaction

The whole point is that the sound appears to come out of the speaker, not the browser.

- The play affordance sits exactly on the SoundLink Micro's real ▶⏸ glyph, so pressing play means pressing play on the speaker. The entire speaker is clickable, and it's keyboard accessible as a single button.
- When it plays, warm light blooms **inside the grille** — masked to the speaker's own alpha silhouette, so the light never spills outside the product.
- A halo swells in the air around the cabinet, pressure rings push outward, and the speaker breathes about 1% on the beat.

All of it is driven by real amplitude off the audio via the Web Audio API (bass-weighted), so the visuals move with the actual track rather than looping a canned animation.

**Fallback:** browsers block sample access when the page is opened as a bare `file://` document. The page detects that within a second of playback and switches to a synthesised envelope, so it looks the same whether it's hosted or opened locally.

## Running it

Needs to be served over HTTP for the live audio analysis to work:

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173

Opening `index.html` directly also works — it just uses the synthesised fallback for the visuals.

## Structure

```
index.html                     single self-contained page (styles + script inline)
assets/
  speaker.png                  SoundLink Micro 2nd Gen, Sandstone — alpha-cut from the source AVIF
  bose-logo-white.png          Bose wordmark, knocked out to white with transparency
  longbeach.mp3                the track
```

## Notes on the build

- **Palette** is dark so the speaker can visibly glow. The accent yellow `#FCDC58` is sampled directly from the campaign cover art.
- **The Kota The Friend wordmark is set as live type**, not an embedded image — crisper at any size and it scales cleanly.
- **The song title is taken from the filename.** The MP3 carries no ID3 title (it's a screen capture), so if the real title differs it's a one-line change in `index.html`.
- The play-glyph hotspot is positioned at 47.6% × 36.7% of the speaker image, found by scanning the product photo for the control icons.

## Still open

Questions deliberately deferred until the real city pages get built:

- Full song or a locked preview — does the page reinforce scarcity by giving only a taste?
- Geo-gating — should Long Beach only really play *in* Long Beach?
- How each city's identity expresses itself while the Bose speaker stays the constant
- Whether show dates / RSVP attach to the page

## Credits

Bose product imagery and wordmark are property of Bose Corporation. Music by Kota The Friend. Prototype for partnership pitch purposes.
