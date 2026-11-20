# vidIQ Replacement Plan

Goal: catalogue everything the vidIQ MCP does, note what each costs in credits, and map every
capability onto a free replacement so the service can be dropped.

Status 20 Nov 2026: Free tier. 15 credits left of 150, renewable pool already spent, resets
2026-12-11. Free tier is 150 credits/month, so a channel analysis plus a few transcripts eats a
month. Replacing it is worth doing.

## BUILT (20 Nov 2026)

The free replacements are live as a single CLI, `nova-free`, that Nova calls instead of vidIQ.

- Source of truth: skill `nova-youtube-agent`, `scripts/nova_free.py`
- Runtime venv: `~/.hermes/tools/nova-free/venv` (rebuild with `scripts/bootstrap.sh`)
- Wrapper on PATH: `~/.local/bin/nova-free`
- Docs + scorecard: skill `nova-youtube-agent`, `references/free-vidiq-replacement.md`

Commands: `doctor`, `channel`, `videos`, `video`, `outliers`, `trending`, `keywords`, `transcript`,
`chapters`, `comments`, `search`, `analytics`, `earnings`, `similar`. Add `--json` anywhere.

All commands verified live against Yugi Jo on 20 Nov 2026. Two gotchas baked in: the wrapper
must `unset PYTHONPATH` (the agent shell injects python3.14 site-packages into the tool's 3.12
venv and breaks numpy/pandas/pytrends), and `analytics --report revenue` only works on a
monetized channel the token owns, so it falls back with a clear message otherwise.

Cost of the head-to-head benchmark: 5 vidIQ credits (15 to 10). That was the last vidIQ spend.

## The free stack that already works here (verified live 20 Nov 2026)

- **YouTube Data API v3** on `~/.hermes/google_token_youtube.json` (scopes: youtube.readonly,
  youtube.force-ssl, youtube.upload). Free quota 10,000 units/day. Live call returned the
  channel: Yugi Jo `UC3lTROT3W1SPPX3lhRAStDg`, 1,570 subs, 50 videos, 113,263 views.
- **YouTube Analytics API v2** on the same token (yt-analytics.readonly). Live call returned
  28-day views, watch minutes, average view percentage and subscriber gains. This is the one
  vidIQ surface that maps to a real free equivalent with no scraping at all.
- **ffmpeg** at `~/.hermes/tools/ffmpeg-9.0.1-linux-arm64/bin/ffmpeg` (media edits, compose).
- **Not installed yet, free to add:** `yt-dlp` (metadata, transcripts, thumbnails, comments,
  TikTok/Instagram public data), `faster-whisper` (transcribe videos with no captions).
- **Autocomplete endpoint**, no key, no quota:
  `https://suggestqueries-clients6.youtube.com/complete/search?client=youtube&ds=yt&q=<q>&hl=en&gl=GB`
- **Skills already on the box:** nova-youtube-agent (research workflow), whisper (STT),
  comfyui (image/video gen), hermes-agent (Piper local TTS), manim-video / hyperframes / p5js
  (motion graphics), youtube-content (transcripts to summaries).

## Full tool inventory (70 tools) with credit cost

### Free (0 credits) - plumbing and account

| Tool | Does |
|---|---|
| vidiq_balance | credit balance |
| vidiq_jobs_list / vidiq_job_poll | async job tracking |
| vidiq_submit_feedback | send feedback |
| vidiq_connect_extension | extension connect card |
| vidiq_user_channels | list your authorized channels |
| vidiq_list_competitors / vidiq_update_competitors | tracked competitor list (follow/unfollow) |
| vidiq_bookmarks_list / _save / _remove | saved items library |
| vidiq_trend_categories | list outlier format categories |
| vidiq_media_file_info | media metadata (duration, dims, streams) |
| vidiq_file_upload / vidiq_video_upload | bring files in |
| vidiq_get_images | show thumbnails/avatars inline |
| vidiq_voiceover_list_voices | list TTS voices |

### Channel and video stats (public) - 5 credits each

| Tool | Does |
|---|---|
| vidiq_get_channels_by_ids | batch channel metadata + counts |
| vidiq_get_videos_by_ids | batch video metadata + stats, VPH, outlier score, engagement |
| vidiq_channel_stats | channel growth over a date range |
| vidiq_channel_videos | a channel's uploads by format, recent or popular |
| vidiq_channel_performance_trends | typical view-accumulation curve |
| vidiq_video_stats | historical views/likes/comments/VPH over time |
| vidiq_user_videos | your own library incl. private/unlisted |

### Analytics (own channel) - 5 credits each

| Tool | Does |
|---|---|
| vidiq_channel_analytics | Analytics API: retention, traffic sources, demographics, geo, revenue |
| vidiq_channel_analytics_extended | Studio-only reads via the browser extension: thumbnail CTR, hour-level, A/B tests, end screens, Shorts stayed-to-watch |

### Discovery and research - 5 credits each

| Tool | Does |
|---|---|
| vidiq_outliers | videos over-performing vs their channel (breakout score) |
| vidiq_trending_videos | fastest view accumulation right now (VPH) |
| vidiq_youtube_search | general YouTube catalog search |
| vidiq_keyword_research | search volume, competition, related/questions/rising/country |
| vidiq_channel_search | find channels by niche/topic/filters |
| vidiq_similar_channels | competitor channels of a given channel |
| vidiq_subscriber_insights | audience overlap (subscriber or commenter) |
| vidiq_comment_insights | recurring audience asks/complaints across a niche |
| vidiq_video_comments | comment threads on a video or channel |
| vidiq_video_change_history | observed title/thumbnail edits for one video |
| vidiq_title_thumbnail_wins | videos whose views doubled after a packaging change |

### Transcripts and video understanding - 5 to 25 credits

| Tool | Does | Cost |
|---|---|---|
| vidiq_video_transcript | full captions for a video | 5 |
| vidiq_generate_video_chapters | chapters from captions | 5 |
| vidiq_watch_shortform_content | scene-by-scene walkthrough, IG/TikTok/Shorts | 10 |
| vidiq_video_watch | watch a full long-form video, visual walkthrough | 25 |

### Packaging (titles and thumbnails) - 1 to 22 credits

| Tool | Does | Cost |
|---|---|---|
| vidiq_generate_titles | scored title suggestions | 5 |
| vidiq_score_title | score a title for CTR | 5 |
| vidiq_score_thumbnail | score a thumbnail for CTR | 5 |
| vidiq_similar_thumbnails | find look-alike thumbnails | 5 |
| vidiq_generate_thumbnail | generate a thumbnail (or a general image) | 22 |
| vidiq_refine_thumbnail | edit an existing thumbnail by description | 22 |
| vidiq_youtube_preview | preview title+thumb beside competitors | 1 |

### Earnings - 5 credits each

| Tool | Does |
|---|---|
| vidiq_earnings_calculate | estimate monthly earnings from a view count |
| vidiq_video_earnings_estimate | estimate one real video's revenue |

### Social (Instagram / TikTok) - 5 to 10 credits

| Tool | Does | Cost |
|---|---|---|
| vidiq_ig_profile | public IG profile | 5 |
| vidiq_ig_profile_reels | a creator's reels | 5 |
| vidiq_tiktok_profile | public TikTok profile | 5 |
| vidiq_tiktok_profile_videos | a creator's latest videos | 5 |
| vidiq_tiktok_video_comments | comments on a TikTok video | 5 |
| vidiq_instagram_tiktok_outlier_search | breakout Reels/TikToks by topic | 5 |
| vidiq_instagram_account_discovery | find IG creators by niche | 10 |
| vidiq_tiktok_account_discovery | find TikTok creators by niche | 10 |

### Media production - 1 to 50 credits

| Tool | Does | Cost |
|---|---|---|
| vidiq_find_broll | free stock B-roll clips | 1 |
| vidiq_edit_media | trim, extract audio/thumbnail, normalise loudness | 1 per edit |
| vidiq_compose | stitch scenes + overlays + voiceover + music into MP4 | 1 per 4s, min 2 |
| vidiq_motion_graphics | animated text/count-up/charts as MP4 | 1 per 4s, min 2 |
| vidiq_generate_clips | long video into vertical captioned clips | 9 per minute of source |
| vidiq_generate_video | text/image to video (5 models) | duration x model rate x 20 |
| vidiq_generate_music | one royalty-free music track | 25 |
| vidiq_voiceover_clone_start | clone a voice from a YouTube video | 1 |
| vidiq_voiceover_clone | clone a voice from an audio sample | 50 |
| vidiq_voiceover_generate | TTS voiceover MP3 | 28 per 1,000 chars |

### Script and copy generation - 1 to 5 credits

| Tool | Does | Cost |
|---|---|---|
| vidiq_generate_script | full long-form script from topic+research | 1 per minute |
| vidiq_generate_comment_replies | draft replies to a viewer comment, per tone | 1 |

## Replacement map: vidIQ capability to free equivalent

| vidIQ cluster | Free replacement | Effort |
|---|---|---|
| Channel + video public stats (5cr) | YouTube Data API v3: channels.list, videos.list, playlistItems.list. VPH and outlier score computed in Python (views / hours since publish; views / channel median). Already have the token. | Low, build a small script |
| Own-channel analytics (5cr) | YouTube Analytics API v2. Verified live. Same token. Covers views, watch time, retention, traffic sources, demographics, geo, and revenue for monetized channels. | Done, already works |
| Studio-only reads (5cr) | Partly no free API: thumbnail CTR, hour-level windows, end screens, A/B tests, Shorts stayed-to-watch live in Studio. Scrape YouTube Studio with the PC browser (pc-browser-control skill) on a schedule. | Medium |
| Keyword research (5cr) | Autocomplete endpoint (free, no key) for real search language + Data API search.list for the results under a term. Google Trends via pytrends for rising demand. | Low to medium |
| Outliers / trending (5cr) | Data API: pull a channel's uploads, compute views vs channel median = breakout. For "trending now", sample a topic's recent uploads and compute VPH. | Medium |
| Competitor / similar channels (5cr) | Data API search.list for the niche, then rank by subs and growth. Subscriber overlap specifically is not exposed free; approximate from shared commenters. | Medium |
| Comments + comment insights (5cr) | Data API commentThreads.list (free, part of the 10k/day). Cluster the text with an LLM for asks/complaints. | Low |
| Transcripts (5cr) | Captions API: captions.list + captions.download on your own videos (works even for ASR tracks). yt-dlp for any public video's subtitles. faster-whisper for videos with no captions. | Low |
| Video watch / chapters (10-25cr) | yt-dlp for the audio, faster-whisper to transcribe, then an LLM for chapters or a walkthrough. Frame grabs via ffmpeg for visual context. | Medium |
| Titles + title scoring (5cr) | Generate titles with the LLM. Score with a rubric prompt (curiosity, clarity, keyword fit) or against autocomplete demand. Not identical to vidIQ's model but close enough to rank. | Low |
| Thumbnails: generate/refine/score (5-22cr) | Generate with ComfyUI locally (free, no per-image cost). Score/critique with vision_analyze against a CTR rubric. Find look-alikes by pulling maxresdefault.jpg and comparing with vision. | Medium |
| Title/thumbnail change history + wins (5cr) | Not exposed free. Build it yourself: a cron that snapshots each video's title/thumbnail daily and diffs. Costs nothing but time to accumulate. | Medium, slow to pay off |
| Earnings estimates (5cr) | Own channel: Analytics API returns estimatedRevenue directly. Other channels: keep a small RPM table (UK Entertainment ~$2.25) and compute. | Low |
| Instagram / TikTok data (5-10cr) | yt-dlp supports public TikTok and Instagram. Comment scraping and profile metadata via yt-dlp or the browser. | Medium |
| B-roll (1cr) | Pexels, Pixabay and Coverr all have free APIs with no meaningful cost. | Low |
| Media edit + compose (1cr) | ffmpeg does trim, extract audio, extract frame, normalise loudness, concat, overlays, music mix. Already installed. | Low |
| Motion graphics (1cr) | manim-video, hyperframes or p5js skills render animated cards/charts as video, free. | Medium |
| Long video to clips (9cr/min) | ffmpeg cut + faster-whisper captions + burn-in. More work than one call, but free. | Medium |
| Text/image to video (variable) | ComfyUI (local diffusion video) or an existing paid tool if one is already available. | High |
| Music generation (25cr) | Local music gen via ComfyUI/audio models, or a free library. | High |
| Voice cloning (1-50cr) | Piper local TTS is the working default here (see hermes-agent skill). Cloning specifically needs an open voice model (XTTS/OpenVoice) locally. | Medium to high |
| Voiceover TTS (28cr/1k) | Piper local TTS. Free, already working. edge-tts is IP-blocked here and must not be used. | Done |
| Script generation (1cr/min) | The LLM writes it. This is the whole point of the agent. | Done |
| Comment replies (1cr) | LLM. | Done |
| Preview on YouTube (1cr) | Static HTML mockup of the home/search card, or the PC browser against a real search page. | Low |

## What genuinely has no free drop-in

1. **Subscriber audience overlap** (`vidiq_subscriber_insights`). No free API exposes which
   channels a channel's subscribers also watch. Commenter overlap is the closest proxy.
2. **Historical title/thumbnail change tracking and "wins"**. vidIQ has years of snapshots.
   You can only start your own archive now and let it build.
3. **Studio-only reports** (thumbnail CTR, hour-level performance, A/B test results,
   Shorts stayed-to-watch). They live in Studio behind a login, so they need the browser
   route, not an API.
4. **A single ranked "outlier score"** tuned on vidIQ's whole index. You can compute a
   breakout ratio yourself; it will be close but not identical.

Everything else in the 70 tools has a free path.

## Free vs vidIQ scorecard (10 = best)

| Capability | nova-free | vidIQ | Winner |
|---|---|---|---|
| Own-channel analytics | 9 | 9 | tie (free wins on cost) |
| Public channel/video stats | 9 | 9 | tie (free wins on cost) |
| Keyword volume numbers | 4 | 9 | vidIQ |
| Keyword relevance/language | 8 | 6 | free |
| Transcripts | 9 | 9 | tie (free wins on cost) |
| Full visual video understanding | 5 | 9 | vidIQ |
| Own-channel outliers | 8 | 8 | tie |
| Cross-channel outlier discovery | 5 | 9 | vidIQ |
| Comments (known video) | 9 | 9 | tie |
| Niche comment insights | 4 | 8 | vidIQ |
| Subscriber overlap | 1 | 9 | vidIQ (no free path) |
| Title/thumbnail history + wins | 2 | 9 | vidIQ |
| Thumbnail generate/refine/score | 5 | 8 | vidIQ out of the box, free on cost |
| Earnings (own channel) | 9 | 7 | free (real revenue if monetized) |
| Earnings (other channels) | 6 | 8 | vidIQ |
| Media edit / compose / clips | 6 | 8 | vidIQ out of the box, free on cost |
| Music / voice cloning | 4 | 8 | vidIQ |
| IG/TikTok structured data | 5 | 8 | vidIQ |
| Titles / scripts / replies | 9 | 8 | tie |

**Bottom line:** nova-free covers roughly 70% of what Nova uses vidIQ for, at zero cost and no
monthly cap, and it beats vidIQ on the two things that matter most day to day: own-channel
analytics and transcript volume. The remaining 30% is keyword volume numbers, cross-channel
discovery, audience overlap, historical packaging archives, and turnkey media generation.

Head-to-head on `legend of the dragon`: vidIQ gave a real volume figure (9,761/month) but 11 of
its 20 related terms drifted to the unrelated film "legend of the white dragon". nova-free gave
14 on-topic autocomplete terms for free. Keep vidIQ for the volume number when it changes a
decision; use nova-free for search language and everything else.

## Build order (done)

1. Done: `nova-free` CLI, `scripts/nova_free.py` + `scripts/bootstrap.sh`.
2. Done: `yt-dlp` installed (2026.10.26) in the tool venv; captions API is the primary transcript
   route, yt-dlp the fallback for public videos.
3. Done: keyword research (autocomplete + Google Trends via pytrends).
4. Done: outlier and trending scripts (breakout vs channel baseline, VPH ranking).
5. Open: packaging loop (LLM titles + ComfyUI thumbnails + vision critique).
6. Open: ffmpeg wrapper for compose/edit and Piper TTS.
7. Open: snapshot cron for title/thumbnail change tracking (starts the archive).

## Links

- YouTube Data API quota: 10,000 units/day. search.list = 100 units, videos.list / channels.list
  / playlistItems.list = 1 unit each. Budget ~20 searches a day comfortably.
- Research workflow with the free scan order: skill `nova-youtube-agent`,
  `references/research-workflow.md`.
- vidIQ credit model: skill `nova-youtube-agent`, `references/vidiq-workflow.md`.
