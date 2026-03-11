# Stremio AIOStreams + AIOmetadata Optimized Config

Optimized configuration for **Movies, Series, and Anime** using **AIOStreams** and **AIOmetadata**.

This setup focuses on:

* Fast stream retrieval
* Clean stream cards
* 1080p-first prioritization
* REMUX detection
* Anime filler skipping
* Minimal UI clutter

Works well with **Torrentio + Debrid services**.

---

# Download Config

The configuration JSON is included in this repository.

Download it here:

**aiostreams-config.json**

---

# Stream Priority

Streams are prioritized approximately in this order:

```
1080p REMUX
1080p Bluray
1080p WEB-DL
2160p REMUX
2160p Bluray
720p WEB
```

Why 1080p first?

* Faster loading
* Less buffering
* Most TVs upscale 1080p very well

---

# Example Stream Card

```
2160p DV CACHED
Oppenheimer
REMUX HEVC
Atmos TrueHD 7.1 | EN
68.4 GB | 62 Mbps | SUB
```

Displayed information:

* resolution
* HDR / Dolby Vision
* REMUX / Bluray / WEB source
* video codec
* audio codec + channels
* audio language
* file size
* bitrate
* subtitle availability

---

# Formatter Configuration

## Name Template

```
{stream.resolution} {stream.visualTags::join(' ')} {service.cached::istrue["CACHED"||""]}
```

Example output:

```
2160p DV CACHED
1080p HDR
```

---

## Description Template

```
{stream.title}
{stream.quality::~Remux["REMUX"||"{stream.quality}"]} {stream.encode}
{stream.audioTags::join(' ')} {stream.audioChannels::join(' ')} | {stream.smallLanguageCodes::join(' ')}
{stream.size::sbytes}{stream.bitrate::exists[" | {stream.bitrate::sbitrate}"||""]}{stream.subbed::istrue[" | SUB"||""]}
```

Example output:

```
Oppenheimer
REMUX HEVC
Atmos TrueHD 7.1 | EN
68.4 GB | 62 Mbps | SUB
```

---

# Anime Configuration

Using **AniList metadata**:

* correct episode ordering
* filler episodes skipped
* better titles for anime releases

---

# Recommended Addons

For best results:

* Torrentio
* RealDebrid / Premiumize
* AIOStreams
* AIOmetadata
* OpenSubtitles

---

# Notes

This repository only contains **configuration settings**.

No private API keys or tokens are included.

Users should configure their own services:

* RealDebrid
* Premiumize
* TorBox (optional)

---

# License

MIT
