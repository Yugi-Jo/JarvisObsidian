# The 12 Days research — full record

Everything pulled on 15 Nov 2026 for the December event, exactly as it came back.
Nothing here is summarised down; the three passes are reproduced in full.

## What it cost

- vidIQ balance before: **170 credits** (150 renewable + 20 add-on)
- vidIQ balance after: **15 credits**
- **155 credits consumed**, by **36 vidIQ calls** across the three passes
- Renews **11 Dec 2026**

I briefed the research passes to "prefer free sources". That was not good enough — a
subagent cannot see the balance or the cost of a call. The instruction should have named
vidIQ as forbidden. That is now written into Nova's skill.

## Calls made, in order



### PASS 1 — Christmas / seasonal content in the nostalgic-cartoon niche

- `skill_view(nova-youtube-agent)`
- `tool_describe(Reading tool details · 3 tools)`
- `mcp__vidiq__vidiq_balance()`
- `mcp__vidiq__vidiq_youtube_search(forgotten christmas special cartoon)`
- `mcp__vidiq__vidiq_outliers({'keyword': 'christmas special retro cartoon', 'publishedWithin': 'allTime', 'limit': 25, 'language': 'en'})`
- `mcp__vidiq__vidiq_youtube_search(christmas episode ranked anime)`
- `web_search("christmas special" retrospective you...)`
- `mcp__vidiq__vidiq_get_videos_by_ids({'videoIds': ['kwiXHiOplTE', 'slxb1gxYt-Y', 'e4J7Gv6hBpM', 'dJNYh5bmugo', 'oVLtUCCM-Zs', 'qFmc_tloH9o']})`
- `mcp__vidiq__vidiq_youtube_search(christmas special retrospective cartoon)`
- `mcp__vidiq__vidiq_youtube_search(christmas episodes ranked)`
- `mcp__vidiq__vidiq_outliers({'keyword': 'christmas episode anime retro', 'language': 'en', 'limit': 20, 'publishedWithin': 'allTime'})`
- `web_search(youtube "christmas" video essay Jorda...)`
- `mcp__vidiq__vidiq_get_videos_by_ids({'videoIds': ['FEmi88hlLlk', 'gJgnoCTDXsI', 'KxnGuKCA9_s', 'GF7PQaj_fqw', 'MQO5D8FW0Cc']})`
- `mcp__vidiq__vidiq_youtube_search(Power Rangers Christmas special)`
- `mcp__vidiq__vidiq_youtube_search(anime christmas episode forgotten)`
- `mcp__vidiq__vidiq_outliers({'keyword': 'Godzilla Christmas kaiju holiday', 'language': 'en', 'limit': 15, 'publishedWithin': 'allTime'})`
- `web_search("Ben 10" OR "Toonami" OR "Yu-Gi-Oh" C...)`
- `mcp__vidiq__vidiq_get_videos_by_ids({'videoIds': ['mEm9cqElZCk', 'KpEb2gipAHI', 'd09NqJkYx50', '1mUGX42I4Pk', 'n6Wmeg4Tgbk', '4jp9aONCTws']})`
- `mcp__vidiq__vidiq_youtube_search(christmas special)`
- `web_search("Power Rangers" Christmas episode ret...)`
- `terminal(date -u)`
- `terminal(date -u)`
- `execute_code(from hermes_tools import terminal pri...)`

### PASS 2 — The fandom-crossover format landscape

- `skill_view(nova-youtube-agent)`
- `tool_describe(Reading tool details · 6 tools)`
- `mcp__vidiq__vidiq_balance()`
- `mcp__vidiq__vidiq_youtube_search(do fans recognize these yugioh cards)`
- `mcp__vidiq__vidiq_youtube_search(fans recognize yu-gi-oh cards)`
- `mcp__vidiq__vidiq_youtube_search(kamen rider fans recognize yu gi oh c...)`
- `mcp__vidiq__vidiq_youtube_search(godzilla fans recognize yugioh cards)`
- `execute_code(import json, glob, os files = sorted(...)`
- `web_search("do fans recognize these yugioh cards...)`
- `web_search(youtube "fans recognize these" cards ...)`
- `execute_code(import json, glob, re def parse_all(t...)`
- `web_search(Cardmarket yugioh "Magic player" unde...)`
- `web_search("fans react to" yugioh OR pokemon OR ...)`
- `web_search("is a kamen rider" OR "is a power ran...)`
- `web_search(Manga4Dummies "TCG: Can I Convince An...)`
- `web_search("do you recognize" OR "fans recognize...)`
- `mcp__vidiq__vidiq_youtube_search(do fans recognize these cards)`
- `web_search("BEN 10 Is A Kamen Rider" youtube)`
- `web_search("pokemon fans" recognize yugioh cards...)`
- `web_search(digimon fans react to pokemon OR yugi...)`
- `web_search("is a kamen rider" ben 10 OR sonic OR...)`
- `execute_code(import json, glob def parse_all(txt):...)`
- `mcp__vidiq__vidiq_get_videos_by_ids({'videoIds': ['PeKaJB_X2ow', 'C3RrIxD0RD8', 'oF5_5_DC7iA', 'FxoG5B1snVY', 'qMqDffZYdqc', 'Jqogb8zRlzs', 'gNrCrw4QAUk', '9BIlkn81W2g', 'dF3CQ_SY1tY', 'GPhWL82eUuo', 'RNNPO8LTP_I', 'A__d_e51Hdg', 'VtKL6xFSXT4', 'u6E_BH7Q2v …(+14 chars))`
- `web_search("do sonic fans" OR "power rangers fan...)`
- `web_search(bakugan retro youtube video essay nos...)`
- `web_search("can a" OR "does a" yugioh player gue...)`
- `mcp__vidiq__vidiq_get_videos_by_ids({'videoIds': ['PeKaJB_X2ow', 'C3RrIxD0RD8', 'oF5_5_DC7iA', 'FxoG5B1snVY', 'qMqDffZYdqc', 'Jqogb8zRlzs', 'gNrCrw4QAUk', '9BIlkn81W2g', 'dF3CQ_SY1tY', 'GPhWL82eUuo', 'RNNPO8LTP_I', 'A__d_e51Hdg', 'VtKL6xFSXT4', 'u6E_BH7Q2v …(+124 chars))`
- `mcp__vidiq__vidiq_youtube_search(BEN 10 Kamen Rider Yu-Gi-Oh Sonic Pow...)`
- `web_search("BEN 10 Is A Kamen Rider" Yugi Jo you...)`
- `web_search("is a power ranger" OR "is a kamen ri...)`
- `tool_describe(Reading tool details · 2 tools)`
- `web_search(Yugi Jo "BEN 10" Kamen Rider video yo...)`
- `web_search("fans recognize" OR "fans know" godzi...)`
- `mcp__vidiq__vidiq_channel_videos({'channelId': 'UC3lTROT3W1SPPX3lhRAStDg', 'popular': True, 'videoFormat': 'long'})`
- `web_search(SuperDuperDani "fan guesses what I re...)`
- `web_search("does" "know yugioh prices" OR "know ...)`
- `web_search("yugioh cards" "godzilla fans" OR "po...)`
- `web_search(Kamen Stray "Kamen Rider vs Ben10" po...)`
- `write_file(/home/ubuntu/yugi-jo-crossover-landsc...)`

### PASS 3 — December event programming and how the inspirations handled Dec 2025

- `skills_list(nova-youtube-agent)`
- `skill_view(nova-youtube-agent)`
- `skill_view(nova-youtube-agent → references/resea...)`
- `skill_view(nova-youtube-agent → references/yugi-...)`
- `tool_search(Searching tools · channel videos dece...)`
- `tool_describe(Reading tool details · 7 tools)`
- `tool_describe(Reading tool details · 1 tool)`
- `web_search(Jordan Fringe youtube channel)`
- `web_search(Dazz Reviews youtube channel)`
- `web_search(Film Form Studios youtube channel anime)`
- `web_search(Dr Wardy youtube anime)`
- `web_search(Mr Sunday Movies youtube)`
- `web_search(LS Mark youtube channel)`
- `mcp__vidiq__vidiq_balance()`
- `web_search("Dr Wardy" youtube cartoon retrospect...)`
- `web_search("Film Form Studios" youtube channel a...)`
- `web_search(DazzReviews youtube.com/@DazzReviews ...)`
- `web_search(anime youtuber "12 days of" christmas...)`
- `web_search(youtuber "advent calendar" daily Dece...)`
- `mcp__vidiq__vidiq_youtube_search(Jordan Fringe)`
- `mcp__vidiq__vidiq_youtube_search(DazzReviews)`
- `mcp__vidiq__vidiq_youtube_search(Mr Sunday Movies)`
- `mcp__vidiq__vidiq_youtube_search(LS Mark)`
- `mcp__vidiq__vidiq_youtube_search(Dr Wardy)`
- `mcp__vidiq__vidiq_channel_search(Film Form Studios)`
- `execute_code(import json, re from hermes_tools imp...)`
- `tool_call(Unnamed call)`
- `web_search(anime youtube channel "every day unti...)`
- `web_search("12 days of anime" youtube playlist D...)`
- `web_search(cartoon youtuber "advent calendar" da...)`
- `mcp__vidiq__vidiq_get_videos_by_ids({'videoIds': ['ogAadO7tMtE', 'wSBFCbs_6kA', 'XZA9w7JmuTk', 'YZQucbByQfY', '9yjbSgv-tgM', 'IdWtLAcEk5c', 'X2MV4FZvPtY', 'FkLyHaRaoXQ', 'iLgUmZ21Rnc', 'Rn-BahDWB6o', 'UtbFgtUIVAo', '4Qaz08Y8rr4', '58l8pmZg9mg', 'K8cJzuGO4i …(+19 chars))`
- `mcp__vidiq__vidiq_channel_search(animation cartoons film retrospectives)`
- `mcp__vidiq__vidiq_youtube_search(Dazz)`
- `web_search("12 days of anime" blog event origin ...)`
- `web_search(youtube "day 1" "day 12" numbered vid...)`
- `mcp__vidiq__vidiq_youtube_search(Power Rangers)`
- `web_search("12 Days of Cartoons" youtube daily D...)`
- `web_search(youtuber daily upload December challe...)`
- `web_search(anime youtuber "advent calendar" 2025...)`
- `web_search("every day until Christmas" youtuber ...)`
- `web_search("12 Days of Anime" Scamp "The Cart Dr...)`
- `web_search(anime youtube channel December series...)`
- `web_search("vlogmas" youtube strategy daily uplo...)`
- `web_search(cartoon retrospective youtuber Decemb...)`
- `web_search(youtube thumbnail design numbered ser...)`
- `mcp__vidiq__vidiq_get_videos_by_ids({'videoIds': ['oQZwd9CRWdU', '32QrjLTXsq0', 'wiT-zMCZIcE']})`
- `web_search("The Wild Review" youtube "25 Wild Ch...)`
- `web_search(RebelTaxi Christmas countdown series ...)`


---

# PASS 1 — Christmas / seasonal content that performs in the nostalgic-cartoon and anime niche

Snapshot date: 2026-11-15 (UTC). View/date figures are live pulls from the YouTube Data API via vidIQ (5 credits/call) — every one is a real, current number, not an estimate. Where a number could not be verified, it says so.

1. CONCRETE SEASONAL VIDEOS THAT PERFORMED (all verified, URL included)

Jordan Fringe — the single strongest proof in this niche. He ran "Fringemas", a daily December series of single-episode Christmas-special essays in Dec 2021:

| Video | Views | Published | URL |
|---|---|---|---|
| The Jimmy Timmy Power Hour Trilogy Was WEIRD | 1,760,482 | 2021-12-18 | https://www.youtube.com/watch?v=s2PTIzNgAaU |
| This Ed, Edd n Eddy Episode Was Meaner Than I Remember | 297,156 | 2021-12-23 | https://www.youtube.com/watch?v=MQO5D8FW0Cc |
| How Jimmy Neutron RUINED Everyone's Day (Holly Jolly Jimmy) | 202,439 | 2021-12-14 | https://www.youtube.com/watch?v=6RjYa7DTz2g |
| How The Grim Adventures of Billy & Mandy Crafts A Narrative | 119,747 | 2021-12-08 | https://www.youtube.com/watch?v=DJo5Z67cXfI |
| The PERFECT Hey Arnold Episode (Arnold's Christmas) | 105,454 | 2021-12-06 | https://www.youtube.com/watch?v=NifaSd81Jjc |
| The Relatability of The Rugrats (The Santa Experience) | 61,616 | 2021-12-12 | https://www.youtube.com/watch?v=Zjm8Ng3uiTM |

Saberspark — "bad/obscure special" and "top 10" formats:

| Video | Views | Published | URL |
|---|---|---|---|
| What the HELL is the NORTH KOREAN Christmas Special? | 1,264,141 | 2019-12-15 | https://www.youtube.com/watch?v=gJgnoCTDXsI |
| What the HELL is The Christmas Light? – Christmas Crap | 509,554 | 2018-12-28 | https://www.youtube.com/watch?v=GF7PQaj_fqw |
| Top 10 CARTOON CHRISTMAS Specials | 378,112 | 2017-12-15 | https://www.youtube.com/watch?v=FEmi88hlLlk |

Other verified examples:

| Channel | Video | Views | Published | URL |
|---|---|---|---|---|
| RebelTaxi | Doug's Depressing Christmas Special | 394,270 | 2015-12-01 | https://www.youtube.com/watch?v=slxb1gxYt-Y |
| WatchMojo | Top 10 Best Anime Christmas Episodes | 229,483 | 2015-12-25 | https://www.youtube.com/watch?v=roisATBjH9E |
| Akatsuki Tomato | The Akatsuki celebrate Christmas?! | 81,712 | 2025-12-25 | https://www.youtube.com/watch?v=E91VWAqXVoE |
| FamiliarFacesChannel | Familiar Faces: 12 More Forgotten Christmas Specials | 31,285 | 2014-06-17 | https://www.youtube.com/watch?v=oVLtUCCM-Zs |
| Smarty Pants | Santa Claws – Miraculous Ladybug S2 Retrospective | 31,071 | 2024-12-27 | https://www.youtube.com/watch?v=Tmn91fcc2aY |
| RetroDaze | Forgotten Christmas Specials Of Our Childhoods | 30,702 | 2024-12-21 | https://www.youtube.com/watch?v=e4J7Gv6hBpM |
| Open By Chance | 2 Hours of Forgotten Christmas Special Classics (w/ retro ads) | 19,372 | 2025-12-06 | https://www.youtube.com/watch?v=__bHBLK7he0 |
| Vintage Timeline USA | 25 Christmas Cartoons From the 1980s & 90s You'll NEVER See Again | 18,070 | 2025-10-31 | https://www.youtube.com/watch?v=iltrCN-CMvg |
| CineHoarder | A Holiday Retrospective into Past Nickelodeon Christmas Promos & Bumpers | 15,231 | 2023-12-02 | https://www.youtube.com/watch?v=INIciXjdl94 |
| AmpleSamuel | Ranking Every 2010s Cartoon Network Christmas Episode! | 7,585 | 2022-12-24 | https://www.youtube.com/watch?v=mEm9cqElZCk |

Counter-evidence (important for expectations): The Story Weaver After Dark's "Top 25 Cartoon Christmas Specials of the 1990s" got 959 views (2025-11-25, https://www.youtube.com/watch?v=dJNYh5bmugo) and Gnarly Wolfman Reviews' classic Christmas round-up got 520 views (2025-12-22, https://www.youtube.com/watch?v=qFmc_tloH9o). Same topic, no audience — the topic alone is not the lever; the creator/format is.

2. PATTERNS THAT ACTUALLY WORK

1. Single-episode deep dive beats general list — the individual Christmas-special essays (105k–1.76M) outperform every niche listicle found. Angle is always "this beloved show's Christmas episode was darker/meaner/weirder than you remember."
2. "Bad/obscure special" review is the highest-ceiling seasonal format — two verified worst-of videos: 1.26M and 509k.
3. "Forgotten / you'll never see again" framing carries the listicle format — RetroDaze 30.7k, Vintage Timeline 18.1k, FamiliarFaces 31.3k.
4. Retro TV-block and ad-break nostalgia is a separate, working lane — CineHoarder's Nickelodeon Christmas promos 15.2k (his Cartoon Network Halloween promos version: 62,640); AT8's 1980s British Christmas adverts compilation: 24,689. Compilation/ad-break content outperforms talking-head listicles per subscriber.
5. Calendar commitment works — a named daily December series turns one seasonal topic into 20+ videos and repeated home-page impressions.
6. Timing: the big seasonals publish 1–25 December; the "forgotten" listicles also work when posted late Oct/Nov (18.1k on 2025-10-31) because they accumulate before the peak.
7. Length: winners run 6–33 minutes; the channel's own 6–18 min slot fits the Jordan Fringe/Saberspark range.
8. Anime Christmas is effectively unclaimed at niche level — WatchMojo's 2015 list (229k) has no retro-anime successor found, and the only recent anime-Christmas hit is a 7-minute fan-skit. (Inference from search results, not a measured demand curve.)

3. SEASONAL TOPIC IDEAS, EACH TIED TO FOUND EVIDENCE

1. "Wait… Ben 10's Christmas Episode Makes NO Sense" — deep dive on "Merry Christmas" (S3E4). Three separate channels tried it and all stalled: A.S.K. Air 2,114 views (2024-12-27, https://www.youtube.com/watch?v=1mUGX42I4Pk), ShadyBlazeBlizzard 2,211 (2023-12-08, https://www.youtube.com/watch?v=4jp9aONCTws), Binge Warmers 475. No large channel has claimed it. Matches his own proven "Wait… X HAS A Real Ending?" pattern and his proven Ben 10 lane. [competitor-backed + channel-data-backed]
2. "The Christmas Special That Broke Sonic" — Sonic's Christmas Blast. His biggest video is Sonic Underground (62,761). The only existing retro on this special has 71 views (https://www.youtube.com/watch?v=JuQT38lCq1s) — a lane he already owns the audience for. [channel-data-backed + competitor-backed]
3. "Ranking Every Power Rangers Christmas Episode" — 10 exist, incl. "I'm Dreaming of a White Ranger". Power Rangers Official documents all 10 (https://www.youtube.com/watch?v=xkxm6DljZCE); Toku Topics did one at 8 min. Power Rangers is a proven lane for him; use toku as seasoning, not the video's premise. [YouTube-validation-backed]
4. "The Cartoon Network Christmas Special That Got Banned" / worst-of obituary — one obscure/bad special, "Christmas Crap" framing. Saberspark's two Christmas Crap videos: 1.26M and 509k. [competitor-backed]
5. "Forgotten 90s Christmas Specials You'll Never See Again" — tight list, 6–18 min, his own nostalgia lane. RetroDaze 30,702; Vintage Timeline USA 18,070; FamiliarFaces 31,285. [competitor-backed]
6. "Nickelodeon's Christmas Promos Were A Whole Vibe" — Xmas promos/bumpers retrospective. CineHoarder 15,231 on the Nickelodeon Christmas version, 62,640 on the CN Halloween version — same format, holiday-swapped. [competitor-backed]
7. "Every Anime Christmas Episode You Forgot" — retro 90s anime (Digimon "A Very DigiChristmas", Love Hina, Tenchi). WatchMojo's 2015 list: 229,483 views, no niche successor. Must be framed as nostalgia/fandom, not "anime analysis" (his anime-analysis lane averages 870). [YouTube-validation-backed + strategic judgment]
8. "Ben 10's Only Christmas Episode vs. the Rest of the Show" — or a full "Ranking Every Ben 10 Holiday Episode". AmpleSamuel's ranking format exists (7,585 views) but he ranked across a decade of CN, not one show. Narrow scope is the fix; Ben 10 is his lane. [competitor-backed]
9. "Digimon's Christmas Episode Is Actually Canon" (or similar single-anime-episode dive). "A Very DigiChristmas" verified as a listed anime Christmas episode; single-episode dives are the top-performing format in this niche. [competitor-backed + strategic judgment]
10. A named December series ("Yugimas" / "Jo-mas") — 3–5 Christmas-special episodes released daily-ish, 8–15 min each. Jordan Fringe's entire Fringemas slate; all six verified videos are from that one December run. Format is the repeatable unit, not any single topic. [competitor-backed]

NOTES / LIMITS
- No verifiable Godzilla or Kamen Rider Christmas content with meaningful numbers was found — search returned only Roblox "Kaiju" gaming videos. Flagged rather than guessed.
- Did not verify a Yu-Gi-Oh Christmas episode exists in the dub, so it was left out rather than invented.
- All titles/angles are YouTube-native-creator patterns (Jordan Fringe, Saberspark, RebelTaxi, RetroDaze) — no podcast-channel formats borrowed, no AI topics, no gaming topics, no Shorts.
- View counts are a single snapshot (2026-11-15) and will drift; one Saberspark record returned viewCount: null, so it is excluded from the claims table rather than quoted.



---

# PASS 3 — December / countdown event programming in the anime and nostalgic-cartoon niche

1. VERIFIED EXAMPLES OF DECEMBER EVENTS / COUNTDOWN SERIES

Two clusters: 12-day runs use full-length videos; 24/25-day runs cut length hard (Shorts or 1–3 min clips) because daily production is otherwise unsustainable.

| # | Channel | Series name | Videos | Date range | Typical views | URL |
|---|---|---|---|---|---|---|
| 1 | The Wild Review (cartoon retrospectives — closest match to this niche) | "25 Wild Christmas Review Days: The Cartoon Specials" | 25 daily | Dec 1–25, 2024 | Very low — Day 1 = 218, Day 17 = 299 | https://www.youtube.com/playlist?list=PL3FRtj_YMm7VEwtngGX22JfL4Jjtv2EV_ |
| 2 | ChrisBe | "24 Days of Weeb-mas" / Anime Advent Calendar | 24 daily (~1–2 min) | Dec 1–24, 2025 | Very low — 9–62 views | https://www.youtube.com/playlist?list=PLBcOBeKCJ-N_-Z9QLmbjJ7mrJ239Ls8v_ |
| 3 | ShumShumm | "Shumsmas" | ~25 daily | Dec 1–25, 2025 | Day 1 (37 min) = 55 | https://www.youtube.com/watch?v=9yjbSgv-tgM |
| 4 | SeaTactics | "12 Days of Anime" | 12 daily | Dec 14–25, 2017 | 39–243 (~4 min each) | https://www.youtube.com/playlist?list=PLA6pjWSIjbRGS0JFHpNEFi6qwwO9XSJW0 |
| 5 | THE AnimeHERO | "12 Days of Anime 2016" | 12 daily | Dec 2016 | Day 12 = 1,422 | https://www.youtube.com/watch?v=Rn-BahDWB6o |
| 6 | Element Animation | "12 Days of The Crack" | 12 daily | Dec 14–25, 2017 | Finale = 4,018,312 (outlier 8.2x) | https://www.youtube.com/watch?v=UtbFgtUIVAo |
| 7 | Weebl's Stuff (Mr Weebl) | "Advent Calendar" — 24 animations in 24 days | 24 daily | Dec 2018 | Announcement = 29,520 | https://www.youtube.com/watch?v=58l8pmZg9mg |
| 8 | Grant Baciocco / Saturday Morning Media | "Grant's Advent Calendar" | 25 daily, every year since 2005 | Dec 1–25 annually (2025 verified) | video podcast, ~2 min eps | https://saturdaymorningmedia.com/shows/gac/ |
| 9 | DGCubes + 13 YouTubers / 12 puzzle makers | "Puzzle Advent Calendar" (collab) | 24-part daily collab | Dec 1–24, 2018 | sampled day = 10,182 (outlier 6.3x) | https://www.youtube.com/watch?v=K8cJzuGO4iQ |
| 10 | Tank Bank | "25 animation videos in 1 month" | 25 daily, then compiled | Dec 2018 | compilation = 1,497 | https://www.youtube.com/watch?v=wiT-zMCZIcE |

Provenance (verified): the "12 Days of Anime" format is a borrowed anime-blog tradition — posts every day Dec 14–25, co-ordinated via a shared tracker (https://thecartdriver.wordpress.com/2014/12/14/12-days-of-anime-12-tissues-for-hunter-x-hunter/). It moved to YouTube via small anime channels, not the big retrospective channels.

2. RECURRING CONVENTIONS (verified patterns; strategy claims labelled)

Series naming — formulaic and countable: "12 Days of X", "24 Days of X", "25 Days of X". Creator-name + "-mas" pattern: Vlogmas, Shumsmas, #Shortsmas. Anime-specific: "Anime Advent Calendar", "Days of Weeb-mas".

Thumbnail numbering / branding (industry-guide consensus, verified as published guidance, not creator-confirmed for these channels) — put "Day N" / "Part N" in the same corner every time on a shape for legibility; reserve only 20–30% of the thumbnail for series branding; build a 3-template brand system rather than one identical layout; the "two-point timeline" (Day 1 vs Day 12) is a recognised countdown device.

Video length during a daily run (verified from the table) — 24/25-day runs collapse length to Shorts or 1–3 min; 12-day runs stay full-length (~4 min up to ~9 min). Pattern: fewer days means you can afford length; more days means you must sacrifice it.

Daily vs alternate-day — advent / "12 days" is strictly daily. The six flagship inspirations publish every 2–3 days, not daily, in December, and do not run numbered countdowns at all.

Stated results the creators shared (verified quotes, mixed/negative) — a case study reports vlogmas slowed views and subs and dropped CTR, "if I post every day, my uploads become less of a big deal"; a small channel saw roughly normal performance during vlogmas with +98 subs, "no significant effect"; a creator attempting 25 days finished 15, with lower watch time; Element Animation called it "painstaking work but it was worth it"; December ad rates do peak.

3. WHAT THE SIX INSPIRATION CHANNELS ACTUALLY DID IN DECEMBER 2025 (all verified)

Key finding: none of the six ran a numbered December event. They published normal standalone videos on a ~2–3 day cadence, with Christmas theming carried by topic choice, not by a banner or numbering.

| Channel (subs) | Dec 2025 cadence | Noteworthy Dec 2025 video |
|---|---|---|
| Jordan Fringe (774K) | 9 videos, ~every 2 days | "WAIT... Remember Beyblade?" (Dec 17, 2h15m) — 321,813 views · https://youtube.com/watch?v=xwHNOEFjcAA |
| | | "The New Gumball Season Is BIZARRE" (Dec 23) — 75,729 · https://youtube.com/watch?v=B7Q6OX47Nyo |
| DazzReviews (645K) | ~12+ long-form, near-daily | "Wow… Now McDonalds Is Making AI Generated Commercials" (Dec 9) — 577,891, 11.1x outlier · https://youtube.com/watch?v=Dgjyeaz73s4 |
| | | "Illumination's TERRIBLE Grinch Movie" (Dec 23) — 217,925 · https://youtube.com/watch?v=6-fLsCtyfA8 |
| Mr Sunday Movies (1.42M) | 9 videos, ~every 3 days | "Biggest Box Office Bombs Of 2025" (Dec 30) — 468,057 · https://youtube.com/watch?v=NaSSpjyf2UI |
| LS Mark (867K) | 3 videos (Dec 6, 18, 31) | "Catching Up – Episode 2: Mary Jane" (Dec 18) — 2,478,082, 9.0x outlier · https://youtube.com/watch?v=DDTUHx8cjTI |
| DrWardy (28.7K) | 2 videos (Dec 16, 21) | "What If Ben 10's Aliens Were Swapped?" (Dec 16) — 19,800 · https://youtube.com/watch?v=vPVzO9VGTJM |
| Film Form Studios (55.1K) | 5 long-form + ~25 daily Shorts | "This Show TRIED to be Power Rangers" (Dec 20) — 66,749 · https://youtube.com/watch?v=RwHS8-VBE80 |

Note: Film Form Studios ran a daily Shorts blitz through December, and several of those Shorts are credited "Edited by Yugi Jo" in the description (e.g. https://youtube.com/watch?v=XBMP5t2_wBY, https://youtube.com/watch?v=N79luMGQF3w). Claimed by the research, not verified independently.

4. RECOMMENDATIONS FOR A 12-VIDEO, DEC 12–23 EVENT

Cadence — publish daily, every day, Dec 12–23 with no gaps; the day-numbering promise only works if the slot never breaks. Anchor each upload to the same daily clock time. Build a 2–3 video buffer before Dec 12. Do not attempt 24–25 days.

Length — stay at the channel's normal 6–18 min; the 12-day runs keep full length. Add a 30–60s "Day N" cold-open that recaps and teases tomorrow.

Banner naming — countable and formulaic so the numbering is self-evident: "The 12 Days of [show/theme]", "12 Days of Yugi Jo", or "Yugi Jo's Advent Calendar". Register a playlist with the same name. Avoid "-mas" naming unless the brand is already strong.

Thumbnail numbering — fixed "Day N" badge in the same corner, same shape/colour, on every thumbnail, ~20–30% of the frame. Vary only the subject art. Use one series icon, consider a cool-to-warm colour progression. Put "Day N" in the title too.

Main risks — (1) dilution / CTR drop from daily posting, mitigated by genuinely strong per-video topics; (2) burnout / non-completion, the single most-common stated outcome; (3) weak views in the niche, where small December series got 200–300 and under 100 — numbering retains, it does not recruit; (4) filler quality dragging the run's CTR; (5) clip copyright, where a channel in this niche has had uploads blocked and reinstated; (6) numbering regret if a day slips; (7) framing beyond Christmas — a theme that works across the whole 12–23 window is safer than a strictly-Christmas banner.



---

# PASS 2 — The fandom-crossover format landscape

(This pass wrote its findings to a file rather than reporting inline. Reproduced in full.)


# YouTube "Fandom Recognition / Crossover" Format Landscape
### Prepared for: Yugi Jo (channel https://youtube.com/@yugi_jo) — 1,560 subs, 42 public long-form videos
### Verified live via vidIQ (YouTube API surfaces) + web search. Shorts excluded. Podcast-derived titles excluded.

All view counts / dates below come from vidIQ `get_videos_by_ids`, `channel_videos` or `youtube_search`
(current snapshots). Where a number could not be verified, it is marked as such.

---

## 1 + 2. Catalogue of working crossover formats (25 verified examples)

### Format A — "[Non-card fandom] Fans Recognize These Yu-Gi-Oh Cards?" (his own format; on-camera recognition test)
The mechanic: put Yu-Gi-Oh cards in front of fans of another franchise and film whether they recognise the
reference (Kamen Rider/Godzilla monsters printed on cards). No gameplay knowledge required — it's a recognition
+ reaction test, and the "will they get it / what will they say" tension creates the retention hook.

| # | Channel | Title | Views | Date | URL |
|---|---------|-------|-------|------|-----|
| 1 | Yugi Jo | Do GODZILLA Fans Recognize These Yu-Gi-Oh Cards? | 8,156 | 2026-03-04 | https://www.youtube.com/watch?v=QOFX78zcH44 |
| 2 | Yugi Jo | Do Kamen Rider Fans Recognize These Yu-Gi-Oh Cards? | 6,237 | 2026-02-25 | https://www.youtube.com/watch?v=VHt1Fb2sbR4 |

Observation: outside his own two videos, I found **no other channel running this exact format** — showing
Yu-Gi-Oh cards to a *non-TCG* fandom and filming their recognition. That is the core unclaimed gap (see §3).

### Format B — "TCG player rates/guesses the OTHER card game's cards" (the cross-game guessing format)
The mechanic: an expert in game A is shown cards from game B and guesses if they're good / real / expensive.
This is Format A's cousin, but the guest is a TCG player, not a nostalgia fan. Massively saturated, and it
produces the biggest view counts in this whole space.

| # | Channel | Title | Views | Date | URL |
|---|---------|-------|-------|------|-----|
| 3 | Cardmarket - Yu-Gi-Oh! | Magic Pro Can't Understand Broken Yugioh Cards! | 1,029,055 | 2026-10-01 | https://www.youtube.com/watch?v=C3RrIxD0RD8 |
| 4 | Cardmarket - Magic | Can a Yu-Gi-Oh Player Spot Bad Magic Cards? \| Staple or Stinker | 692,159 | 2025-05-29 | https://www.youtube.com/watch?v=9BIlkn81W2g |
| 5 | Cardmarket - Yu-Gi-Oh! | Magic Player Can't Understand Broken Old School Yugioh Cards! | 623,103 | 2026-02-05 | https://www.youtube.com/watch?v=PeKaJB_X2ow |
| 6 | Cardmarket - Magic | Can Two Yu-Gi-Oh! Players Tell Which Magic Cards Are Bad? | 283,198 | 2026-07-16 | https://www.youtube.com/watch?v=A__d_e51Hdg |
| 7 | Cardmarket - Yu-Gi-Oh! | Magic Player Rates Yu-Gi-Oh! Power Levels! | 197,337 | 2022-09-23 | https://www.youtube.com/watch?v=dF3CQ_SY1tY |
| 8 | Cardmarket - Yu-Gi-Oh! | Magic Player Guesses Yu-Gi-Oh Card Power Levels! | 136,295 | 2025-04-27 | https://www.youtube.com/watch?v=RNNPO8LTP_I |
| 9 | Cardmarket - Yu-Gi-Oh! | We Asked a Magic Player... What's Wrong With Yugioh? | 131,820 | 2026-03-24 | https://www.youtube.com/watch?v=VtKL6xFSXT4 |

### Format C — Cross-game guessing on mid/small channels (proves the format, shows the ceiling)
| # | Channel | Title | Views | Date | URL |
|---|---------|-------|-------|------|-----|
| 10 | Rarran | Can a Yugioh Player Guess if a Hearthstone card is FAKE? | 157,819 | 2023-08-13 | https://www.youtube.com/watch?v=XOrjFPJXN38 |
| 11 | Taste Of Victory | YGO Player Tries to Guess How Good Digimon Cards Are w/ MBT Yugioh | 144,477 | 2022-10-01 | https://www.youtube.com/watch?v=-Ca6iwzw8yc |
| 12 | Cimoooooooo | Guess That Yu-Gi-Oh! Card! \| Episode 1 (ft. Nyhmnim) | 85,742 | 2022-11-03 | https://www.youtube.com/watch?v=1bqLgnEv3S0 |
| 13 | TheDuelLogs | Can A Newer Player Guess How Good Old School Staples Were? W/ MariMari_en | 60,249 | 2022-10-27 | https://www.youtube.com/watch?v=zj891xhf_6k |
| 14 | TheDuelLogs | Yugioh Players Tries to Guess if Digimon Cards Are Good or Not [P2] | 22,459 | 2022-06-27 | https://www.youtube.com/watch?v=IZHIOOX-cj4 |
| 15 | TheOneJame | MTG Player Tries To Guess How Good Digimon Cards Are (w/ AgitoSwiftly) | 9,092 | 2024-04-18 | https://www.youtube.com/watch?v=EJs6G2Pm0Tg |
| 16 | Woody [REC] | Pokemon Player Guess How Good Yu-Gi-Oh Cards Are | 2,904 | 2022-08-01 | https://www.youtube.com/watch?v=oF5_5_DC7iA |
| 17 | The Test Table | Can a POKEMON Player GUESS Which YU-GI-OH Cards are Good!? | 1,249 | 2024-10-12 | https://www.youtube.com/watch?v=-i_43MlPHag |

Note the pattern: when the guest is a **card-game player**, these can hit 100K–1M (Cardmarket) — but the same
Pokémon↔Yu-Gi-Oh premise on a small channel (rows 16–17) dies at 1–3K views. The format's ceiling depends on
the host's audience, not the premise.

### Format D — "Does [creator] know Yu-Gi-Oh prices?" (creator-quiz, saturated inside the YGO bubble)
| # | Channel | Title | Views | Date | URL |
|---|---------|-------|-------|------|-----|
| 18 | Ruxin34 | Does @PokeRev Know Yugioh Prices? | views not verified | 2022-10-24 | https://www.youtube.com/watch?v=A9SiKsf0mgU |
| 19 | Ruxin34 | Does @MBTYuGiOh Know Yugioh Prices? | views not verified | 2022-11-30 | https://www.youtube.com/watch?v=4_b6PkoMeXw |

(Ruxin34 runs this as a long series — Farfa, Cimoooooooo, Dzeeff, DistantCoder, Nyhmnim, TomBox, jarvis.)

### Format E — "[Fandom] Fans React To [Other Fandom]" (fandom-war reaction)
| # | Channel | Title | Views | Date | URL |
|---|---------|-------|-------|------|-----|
| 20 | TheDigiDude | 5 Pokemon Fans React to Digimon | 134,515 | 2025-12-19 | https://www.youtube.com/watch?v=FxoG5B1snVY |
| 21 | Manga4Dummies | TCG: Can I Convince An Old Digimon Fan? | 166 | 2023-05-22 | https://www.youtube.com/watch?v=qMqDffZYdqc |

The Digimon↔Pokémon reaction space is heavily worked (multiple channels react to JaidenAnimations' "Pokemon fan
plays Digimon and hated it"), but mostly as *reaction to existing videos*, not fresh original crossover.

### Format F — "[Fandom A] Is [Fandom B]" argument video
| # | Channel | Title | Views | Date | URL |
|---|---------|-------|-------|------|-----|
| 22 | Yugi Jo | BEN 10 Is A Kamen Rider! | 3,393 | 2026-04-08 | https://www.youtube.com/watch?v=3iq2CxJWGFs |
| 23 | Tidepool Orchestra | Ben 10 vs Kamen Rider Decade | 4,140 | 2020-01-25 | https://www.youtube.com/watch?v=gNrCrw4QAUk |
| 24 | Kamen Stray | Kamen Rider vs Ben10: The Power Gap Nobody Talks About | views not verified | 2026-03-30 | https://www.youtube.com/watch?v=Jqogb8zRlzs |
| 25 | DosmRider | Should There Be Modern Kamen Rider Adaptions? | views not verified | — | https://www.youtube.com/watch?v=FXhNmIqYJVc |

The Ben 10↔Kamen Rider argument is a small but live niche (his own video is breakout 2.29 on his channel). The
power-argument ("who wins") variant is done; the *identity* argument ("X IS a Y") is much thinner.

### Bonus analog — on-camera recognition quiz (not cards, but same mechanic)
SuperDuperDani runs "What Pokémon did I REMOVE from this card?" — quizzing real Pokémon fans at conventions.
vidIQ's YouTube search surfaced several uploads at **703,386 / 1,037,691 / 233,145 / 63,376 views** (2026).
Direct video URLs were not captured, so treat these figures as vidIQ-search-derived and unconfirmed by URL.
The takeaway: filming real fans' recognition on camera, with a tight quiz mechanic, is a proven retention
engine at scale.

---

## 3. Saturated vs unclaimed

### SATURATED — avoid as a primary strategy
- **Card-game ↔ card-game card guessing** (MTG ↔ YGO ↔ Digimon ↔ Pokémon ↔ Hearthstone ↔ One Piece). Dozens
  of videos, the biggest hitting 600K–1M. Owned by Cardmarket and the big TCG channels.
- **"Does [creator] know Yu-Gi-Oh prices?"** — Ruxin34 has effectively claimed it inside the YGO bubble.
- **Pokémon card recognition quizzes** — saturated (SuperDuperDani, Ndup, PokéReveal, etc.).
- **Digimon ↔ Pokémon fandom reaction** — saturated with reaction-channel content.
- **"Who wins: Ben 10 vs Kamen Rider"** — a handful of channels already there.

### UNCLAIMED — visible demand, little or no competition
1. **Yu-Gi-Oh cards shown to a NON-TCG nostalgia fandom, filmed on camera.** Only Yugi Jo does this (2 videos).
   Zero competitors found across all searches. This is his format and nobody has copied it.
2. **Sonic fandom crossover.** His Sonic video is the biggest thing on his channel (62,767 views, breakout
   110.01) yet there is **no** Sonic recognition/card crossover anywhere. Demand proven, format absent.
3. **Power Rangers / tokusatsu-adjacent nostalgia.** His most-covered lane; the Godzilla→Power Rangers bridge
   is unexploited.
4. **Bakugan.** His own Bakugan video holds strong retention (32.3% per brief; 757 views) and no Bakugan↔YGO
   crossover exists at all.
5. **Ben 10 recognition.** Ben 10 is validated on his channel (three videos), and "BEN 10 Is A Kamen Rider!"
   works — but no "Do Ben 10 Fans Recognize These Yu-Gi-Oh Cards?" exists.
6. **Card games shown to non-TCG fandoms, other than Yu-Gi-Oh** (e.g. Pokémon cards to Sonic/toku fans).
   Completely open.

---

## 4. Ranked shortlist — 8 crossover concepts for Yugi Jo

Ranked by (evidence strength on his own channel) × (format proven) × (competition absent). Each carries an
evidence URL. Titles are drawn from the *format* (not from podcast channels).

1. **"Do SONIC Fans Recognize These Yu-Gi-Oh Cards?"**
   His Sonic video is the channel's outlier (62,767 views, breakout 110.01) and the recognition format is
   proven (8,156 / 6,237). Demand strong, competition zero.
   Evidence: https://www.youtube.com/watch?v=ikpmGbwjaw4 + https://www.youtube.com/watch?v=QOFX78zcH44

2. **"Do POWER RANGERS Fans Recognize These Yu-Gi-Oh Cards?"**
   Power Rangers is his deepest catalogue lane and the Godzilla→kaiju→PR audience overlaps. Format proven.
   Evidence: https://www.youtube.com/watch?v=QOFX78zcH44 + https://www.youtube.com/watch?v=TnVDu0LV4HA

3. **"Do BEN 10 Fans Recognize These Yu-Gi-Oh Cards?"**
   Ben 10 is triple-validated on his channel; he already owns the Ben 10↔toku bridge. Format unclaimed here.
   Evidence: https://www.youtube.com/watch?v=3iq2CxJWGFs + https://www.youtube.com/watch?v=MIkyHcl0pc4

4. **"Do DIGIMON Fans Recognize These Yu-Gi-Oh Cards?"**
   Cross-game Digimon↔YGO guessing already proven at 144K (Taste Of Victory). The *non-TCG fandom recognition*
   version is unclaimed.
   Evidence: https://www.youtube.com/watch?v=-Ca6iwzw8yc

5. **"Do BAKUGAN Fans Recognize These Yu-Gi-Oh Cards?"**
   His Bakugan video holds 32.3% retention (per brief); no Bakugan↔YGO crossover exists anywhere.
   Evidence: https://www.youtube.com/watch?v=OHyujqTbHj0

6. **"Sonic Is A Kamen Rider!" (identity-argument video, following "BEN 10 Is A Kamen Rider!")**
   His Ben 10 version is breakout 2.29; the IDW Sonic comic literally gives Sonic a Kamen-Rider-style "Phantom
   Rider" guise (confirmed by the writer), so the claim has real receipts.
   Evidence: https://www.youtube.com/watch?v=3iq2CxJWGFs + https://kamenrider.fandom.com/wiki/List_of_references_to_Kamen_Rider_in_popular_culture

7. **"Do POKÉMON Fans Recognize These Yu-Gi-Oh Cards?" (framed at the nostalgia *anime* fandom, not the TCG)**
   Huge audience; the TCG-channel versions underperform (2,904 / 1,249) precisely because they target card
   grinders, not nostalgia fans — which is his angle.
   Evidence: https://www.youtube.com/watch?v=oF5_5_DC7iA + https://www.youtube.com/watch?v=-i_43MlPHag

8. **"Do TOONAMI Fans Recognize These Yu-Gi-Oh Cards?"**
   Toonami is a nostalgia identity, and his Toonami video exists. Weakest evidence in the list (239 views on
   that video), so rank last.
   Evidence: https://www.youtube.com/watch?v=-g7UQMUjSPg

9. **"Do GODZILLA Fans Recognize These POKÉMON Cards?" (extend the proven format to a second card game)**
   His Godzilla video is the best-performing card crossover (8,156); swapping the card game tests whether the
   *fandom* or the *cards* carry the format.
   Evidence: https://www.youtube.com/watch?v=QOFX78zcH44

10. **"Legend Of The Dragon Is A Kamen Rider!" (identity-argument, his existing niche)**
    He already made the Legend of the Dragon retrospective; the "forgotten Power Rangers" framing is his voice.
    Higher risk (tiny fandom), so included as a long-tail idea.
    Evidence: https://www.youtube.com/watch?v=fL2mvlKaNRQ

---

## Compliance checks
- Titles/format ideas derived from the *format mechanic*, not from podcast channels (Have A Word / The Weekly
  Planet excluded). No podcast-channel title or thumbnail patterns used.
- No pro-AI topics. No gaming content (Yu-Gi-Oh/kaiju/toku/anime treated as nerd-culture, not gaming).
  No Shorts.
- Every figure above is tagged verified (vidIQ) or explicitly marked "not verified".



---

# What I did with all this

Consolidated into Nova's memory: `competitor-scans.md` (the demand scan and these findings),
`crossover-landscape.md` (the raw Pass 2 report), and `pipeline.md` (the event plan, revised
after the research). The event-planning conventions are also in the skill's
`references/event-programming.md`.

## The three things that changed the plan

1. **The numbered banner is not proven by his inspirations.** None of the six ran a numbered
   December event in Dec 2025. Small channels that did got 200–300 views a day. Numbering
   retains the audience you have; it does not recruit. Every entry must stand alone.
2. **There is a blueprint worth copying** — Jordan Fringe's "Fringemas": daily single-episode
   Christmas-special deep dives, 61,616 up to 1,760,482 views.
3. **The honest counter-evidence** — a near-identical seasonal listicle from a small channel
   got 959 views. The angle and the creator carry it; the season does not.
