# 🇨🇺 Radio from Cuba

**10 stations**, every one opened and confirmed to return audio on **2026-08-23**.

## How to listen

| | |
|---|---|
| **In your browser** | **[globalradio.app/cuba](https://globalradio.app/cuba/)** — press play, no install, keeps playing while you browse |
| **In a player** | `mpv https://raw.githubusercontent.com/eyalev/verified-radio-streams/main/m3u/CU.m3u` — or open that URL in VLC |
| **In your own code** | [`stations/CU.json`](../../../stations/CU.json) |

## Start here

The most-voted stations in Cuba, each with a page of its own:

- **[Exa FM](stations/exa-fm.md)** — pop, pop-music, pop-rock · 48 kbps AAC · 1,931 votes
- **[Cubania Radio](stations/cubania-radio.md)** — genre not labelled · 128 kbps MP3 · 623 votes
- **[Canal Radio Cruces Cienfuegos](stations/canal-radio-cruces-cienfuegos.md)** — genre not labelled · 128 kbps MP3 · 616 votes
- **[Rádio Costa (Archipiélago Uno)](stations/radio-costa-archipielago-uno.md)** — genre not labelled · 128 kbps MP3 · 174 votes

## On FM and AM

3 of these stations state a broadcast frequency in their own name — the only
place this dataset gets one, so the other 7 are unrecorded rather than
internet-only.

| Station | On air | Listen |
|---|---|---|
| Radio Progreso 90.3 FM | **90.3 FM** | [▶︎ listen](https://securestreams7.autopo.st/?uri=https://icecast.teveo.cu/XjfW7qWN) |
| Radio Habana Cuba 102.5 FM | **102.5 FM** | [▶︎ listen](https://securestreams7.autopo.st/?uri=https://icecast.teveo.cu/McW3fLhs) |
| Radio Rebelde 1180 AM | **1180 AM** | [▶︎ listen](https://securestreams7.autopo.st/?uri=https://icecast.teveo.cu/kHKL7tWd) |

## All 10 stations

Ordered by votes on [Radio Browser](https://www.radio-browser.info), which is a
crowd signal and not a ranking this project stands behind.

**▶︎ listen** opens the audio stream itself — it plays in most browsers and in
any media player. To press play on a page instead, with the station list beside
it, open **[globalradio.app/cuba](https://globalradio.app/cuba/)**. A station
name is a link only when it has a page in this repo.

| Station | Genre | Quality | Listen | |
|---|---|---|---|---|
| [Exa FM](stations/exa-fm.md) | pop, pop-music, pop-rock | 48 kbps AAC | [▶︎ listen](https://playerservices.streamtheworld.com/api/livestream-redirect/XHPSFMAAC.aac) | [site](https://www.exafm.com/veracruz/) |
| [Cubania Radio](stations/cubania-radio.md) | — | 128 kbps MP3 | [▶︎ listen](https://streamingv2.shoutcast.com/cubania?type=.mp3) | [site](https://radiosdecuba.com/cubania/) |
| [Canal Radio Cruces Cienfuegos](stations/canal-radio-cruces-cienfuegos.md) | — | 128 kbps MP3 | [▶︎ listen](https://stream.laut.fm/canalradio) | [site](https://canalradio.caster.fm/) |
| [Rádio Costa (Archipiélago Uno)](stations/radio-costa-archipielago-uno.md) | — | 128 kbps MP3 | [▶︎ listen](https://radio.archipielago.uno/radiocosta) | [site](https://radio.archipielago.uno/) |
| Abdulbasit Abdulsamad | — | 192 kbps MP3 | [▶︎ listen](https://radio.mp3islam.com/listen/abdulbasit/radio.mp3) | [site](https://mp3islam.com/) |
| Radio Campesina Cubana | salsa | 128 kbps MP3 | [▶︎ listen](https://radiocampesinacubana.stream.laut.fm/radiocampesinacubana?t302=2026-08-21_15-54-32&uuid=f27d83f9-8947-4c58-ac38-cabdd2fae52f) | [site](https://radioscuba.com/312-radio-campesina-cubana.html) |
| Radio Rebelde 1180 AM | — | MP3 | [▶︎ listen](https://securestreams7.autopo.st/?uri=https://icecast.teveo.cu/kHKL7tWd) | [site](https://radiorebelde.cu/) |
| Radio Habana Cuba 102.5 FM | — | 64 kbps MP3 | [▶︎ listen](https://securestreams7.autopo.st/?uri=https://icecast.teveo.cu/McW3fLhs) | [site](https://radiohc.cu/) |
| Radio Progreso 90.3 FM | — | 64 kbps MP3 | [▶︎ listen](https://securestreams7.autopo.st/?uri=https://icecast.teveo.cu/XjfW7qWN) | [site](https://www.radioprogreso.icrt.cu/) |
| Radio María de la Caridad | — | 80 kbps MP3 | [▶︎ listen](https://usa6.fastcast4u.com/proxy/aserranog/stream) | [site](https://soloist.ai/radiomariadelacaridad) |

## What the columns do and do not say

- **Genre** is crowd-submitted and often absent — 8 of 10 stations
  here have none. Absent means nobody labelled it, not that it plays nothing.
- **Quality** is what the server reported when the stream was opened. `—`
  means it reported nothing.
- **Listen** is the raw audio URL. It belongs to the broadcaster, not to this
  project, and may be geo-blocked where you are.
- **site** is the station's own website, as its operators gave it to Radio
  Browser. Some are stale; none of them were checked by this project — only the
  streams were.

Every station also carries the date its stream last answered — see
[`stations/CU.json`](../../../stations/CU.json) or any station page above.

---

[← Americas](../README.md) · [All countries](../../README.md) · [Repo home](../../../README.md) · [globalradio.app](https://globalradio.app)
