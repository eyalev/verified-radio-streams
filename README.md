# Verified radio streams

**7,707 internet radio streams from 188 countries.** Every one was
opened and returned audio before it was written here, and every row carries the
date that happened.

```
stations/index.json   the country list, counts, and where each file is
stations/<CC>.json    one country, self-describing
stations/all.json     all of it, one file (3.3 MB)
m3u/<CC>.m3u          the same country as a playlist
m3u/all.m3u           everything, grouped by country
```

Listen to any of it at **[globalradio.app](https://globalradio.app)**, which is built from this
same data.

## What "verified" means here, exactly

Most radio lists are a link and a hope. Links rot, and a dead station is
indistinguishable from a live one until you press play. So every stream in this
repo had to survive three filters, none of which is taste:

| filter | why |
|---|---|
| **https only** | an `http://` stream is blocked as mixed content on any https page — silence, with no error a listener can see |
| **no HLS** | a bare `<audio>` element cannot play `.m3u8` |
| **it has to answer** | the stream was opened with a `Range` request and had to return audio bytes. Radio Browser's own `hidebroken` flag is not enough; stations it called healthy did not answer |

Every station carries `"verified": "YYYY-MM-DD"` — the day its stream last
answered. That is per-row on purpose. A single "last updated" badge at the top
of a repo tells you when a *file* was written, not whether the station on line
4,000 still exists.

Streams verified between **2026-08-23** and **2026-08-24**.

A station that fails one run is **never deleted**. A broadcaster restarting, a
CDN blip, a geo-block and a genuinely dead URL are indistinguishable from one
request, and deleting on the strength of a single failure would quietly shrink
the dataset toward whatever this machine's network could reach that day.

## The one field that is usually missing, on purpose

`format` is `music`, `talk` or `mixed` — or absent. It is absent
3,255 times out of 7,707, and that is a feature.

Crowd tags are not evidence. Of the top 200 stations in one country, four
claimed `talk` and one of those four was a football-and-music station. So the
harvester infers `music` from musical genre tags and **never infers `talk`**.
Being wrong about music costs a listener a little; being wrong about talk costs
them an hour of pop when they wanted speech.

**An absent `format` means unknown, not neutral.** If you filter on it, exclude
the unlabelled rather than letting them through — passing them off as "talk"
breaks the only promise that filter makes.

```
music 4,452   unlabelled 3,255
```

`talk` and `mixed` are legal values a human may set and **no machine here has
ever written one** — currently 0 of the first and 0 of the
second, so every station in this repo is either `music` or unknown. Do not read the absence of `talk` as evidence that a country
has no talk radio; read it as nobody having checked.

## Schema

Each entry in `stations`:

| field | | |
|---|---|---|
| `id` | string | stable slug, unique within its country |
| `name` | string | as the broadcaster writes it, in its own script |
| `stream` | string | the audio URL — always `https`, never HLS |
| `url` | string? | the station's homepage, dropped entirely if unparseable |
| `codec` | string | mp3 5,275 · aac 2,353 · ogg 71 · unknown 8 |
| `bitrate` | number | kbps, `0` when the server does not say |
| `format` | string? | in practice only ever `music`; **usually absent, see above** |
| `genre` | string[] | normalised crowd tags, may be empty |
| `langs` | string[]? | language names |
| `langCodes` | string[]? | ISO 639-1 |
| `state` | string? | region or city, when known |
| `votes` | number | Radio Browser votes — a rough popularity signal |
| `clicks` | number | Radio Browser plays in the last 24h |
| `verified` | string | `YYYY-MM-DD`, the day the stream last answered |

`?` marks a field that is absent when unknown. **Nothing here is filled in with
a plausible default.** A missing name costs you nothing; an invented one asserts
something false.

## Biggest countries

| | country | stations | json | m3u |
|---|---|--:|---|---|
| 🇮🇩 | [Indonesia](https://globalradio.app/indonesia/) | 165 | [`ID.json`](stations/ID.json) | [`ID.m3u`](m3u/ID.m3u) |
| 🇦🇷 | [Argentina](https://globalradio.app/argentina/) | 164 | [`AR.json`](stations/AR.json) | [`AR.m3u`](m3u/AR.m3u) |
| 🇫🇷 | [France](https://globalradio.app/france/) | 162 | [`FR.json`](stations/FR.json) | [`FR.m3u`](m3u/FR.m3u) |
| 🇳🇱 | [Netherlands](https://globalradio.app/netherlands/) | 160 | [`NL.json`](stations/NL.json) | [`NL.m3u`](m3u/NL.m3u) |
| 🇧🇷 | [Brazil](https://globalradio.app/brazil/) | 159 | [`BR.json`](stations/BR.json) | [`BR.m3u`](m3u/BR.m3u) |
| 🇷🇴 | [Romania](https://globalradio.app/romania/) | 159 | [`RO.json`](stations/RO.json) | [`RO.m3u`](m3u/RO.m3u) |
| 🇨🇴 | [Colombia](https://globalradio.app/colombia/) | 156 | [`CO.json`](stations/CO.json) | [`CO.m3u`](m3u/CO.m3u) |
| 🇬🇧 | [United Kingdom](https://globalradio.app/united-kingdom/) | 156 | [`GB.json`](stations/GB.json) | [`GB.m3u`](m3u/GB.m3u) |
| 🇨🇦 | [Canada](https://globalradio.app/canada/) | 152 | [`CA.json`](stations/CA.json) | [`CA.m3u`](m3u/CA.m3u) |
| 🇦🇺 | [Australia](https://globalradio.app/australia/) | 150 | [`AU.json`](stations/AU.json) | [`AU.m3u`](m3u/AU.m3u) |
| 🇦🇹 | [Austria](https://globalradio.app/austria/) | 150 | [`AT.json`](stations/AT.json) | [`AT.m3u`](m3u/AT.m3u) |
| 🇧🇪 | [Belgium](https://globalradio.app/belgium/) | 150 | [`BE.json`](stations/BE.json) | [`BE.m3u`](m3u/BE.m3u) |

Full list in [`stations/index.json`](stations/index.json).

## Use it

```bash
# one country
curl -sL https://raw.githubusercontent.com/eyalev/verified-radio-streams/main/stations/PT.json

# a playlist, straight into a player
mpv https://raw.githubusercontent.com/eyalev/verified-radio-streams/main/m3u/PT.m3u
vlc https://raw.githubusercontent.com/eyalev/verified-radio-streams/main/m3u/all.m3u
```

```js
const RAW = 'https://raw.githubusercontent.com/eyalev/verified-radio-streams/main';

// which countries have the most stations?
const { countries } = await fetch(`${RAW}/stations/index.json`).then((r) => r.json());
console.log(countries.slice(0, 5).map((c) => `${c.flag} ${c.country} ${c.stationCount}`));

// one country
const pt = await fetch(`${RAW}/stations/PT.json`).then((r) => r.json());

// unlabelled stations are EXCLUDED from a format filter, never passed through
const music = pt.stations.filter((s) => s.format === 'music');

// anything verified in the last 30 days
const cutoff = new Date(Date.now() - 30 * 864e5).toISOString().slice(0, 10);
const fresh = pt.stations.filter((s) => s.verified >= cutoff);
```

## What is not in here

- **Stations that did not answer.** They are dropped at harvest time and the
  list is not currently written down. Publishing the failures — a negative
  cache with dates — is the obvious next thing this repo should carry, and it
  does not exist yet, so it is not claimed above.
- **HLS and http streams.** Excluded by the filters, not missing by accident.
  If you are building something that can play `.m3u8`, Radio Browser has
  them and this repo never will.
- **Every station in the world.** Each country is capped, keeping the
  strongest by votes and clicks. This is a dataset of streams that work, not a
  census.
- **3 entries withheld** for the reasons listed in [`EXCLUDED.md`](EXCLUDED.md).

## Where it comes from

Station discovery is [**Radio Browser**](https://www.radio-browser.info), a
community directory whose collected data its author placed in the **public
domain**. Verification, filtering, normalisation and the schema above are this
project's.

The data in this repo is released under [CC0 1.0](LICENSE) — public domain, no
attribution required. Attribution to Radio Browser is nonetheless the right
thing to do, because the directory only exists because people kept adding to it.

**Stream URLs are not ours and are not licensed by us.** They point at
third-party broadcasters who may geo-block, rate-limit, move or withdraw them
at any time. Verified means it answered on the date recorded — nothing more, and
in particular not a right to rebroadcast it. See [`NOTICE`](NOTICE).

## Corrections

A wrong or missing station is almost always wrong in
[Radio Browser](https://www.radio-browser.info) first, and fixing it there fixes
it for every project downstream, not just this one. For a problem with *this*
repo's shape — the schema, the filters, a station that is here but should not
be — open an issue.

---

Built by [globalradio.app](https://globalradio.app) · regenerated from the site's own data, so
the two can never disagree about which streams answered.
