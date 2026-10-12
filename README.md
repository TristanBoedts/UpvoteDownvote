# Upvote Drift Playground

An interactive toy that shows one idea:

> With **two** candidates, competing for votes pulls both to the middle. With **three or more** and upvotes only, nobody has a stable position and the stable arrangements are camps out on the sides. A strongly centred crowd (think Norway or Switzerland) pulls back. One **equal downvote** for everyone pulls candidates back to the centre.

Social media feeds are the many-candidate case: every post is a candidate, and the upvote is the only vote.

**Try it:** open `index.html` (or the GitHub Pages link) and press Play. No install, no build, no server. It is a single file.

## Tab 1: Candidates move

People are spread along a left to right line. Each person upvotes the **nearest** candidate. Candidates take turns moving to the spot that gets them the most support.

| Control | What it does |
|---|---|
| Candidates | 2 to 10. Try 2, then 3, then 4, 5, 6 and beyond. |
| Downvote weight | 0 = upvote only. 1 = every person also gets one equal downvote, cast against the candidate **furthest** from them. In between = a lighter downvote. |
| Where people are | Spread evenly, most near the middle (bell shaped), or two hills (a divided crowd). |
| Centre strength | How tight the middle is (bell or hills). |
| Distance between hills | For the two-hill crowd. |
| Extra people at the edges | Mixes in an even crowd to fatten the tails. |
| I play candidate A | A stays where you drag it. The others react. Good for the audience exercise. |
| Speed | Higher = several moves per tick. |

You can drag any candidate (or focus it and use the arrow keys). **Copy link to this setup** stores everything, including the positions, in the page address, so you can share an exact scenario.

### What to look for

1. **Two vendors**: both creep to the middle and stop.
2. **Three vendors**: whoever is in the middle is squeezed and hops over. It never stops.
3. **Five, upvote only**: two camps form out on the sides, the middle empties, and one camp keeps reshuffling. Press *Random start* a few times.
4. **Five + one downvote**: they all end up bunched in the middle, and that is a true resting point.
5. **Bell shaped crowd**: the push outward is weaker. Slide *Centre strength* to the right and watch it come back.
6. **Two hills**: nothing pulls back. Add the downvote.
7. **You play A**: where would *you* stand? Then set the downvote to 1 and try again.

## Tab 2: People respond too

In tab 1 the crowd is fixed. In real systems people drift toward what they see. Here each person leans toward the candidate they back, while being pulled back toward where they started. Over many rounds the crowd reshapes itself.

| Control | What it does |
|---|---|
| Who the people are / Width of the crowd | The starting crowd. A small width is a strong middle, a large width a thin middle. |
| Switch the downvote on at round | 0 = from the start. A later round = the downvote arrives after the system has already drifted. |
| How strongly people follow / stay true to themselves | The two forces acting on each person. |
| Try different random noise | Re-runs the same setup with a different wobble. |

What to look for: with a **strong middle** the two small hills stay close together. With a **thin middle** the centre empties out and the hills drift apart. Add the downvote and people bunch up in the middle again.

With a thin middle the outcome is **touchy**: most runs polarise, but some noise seeds make the candidates bunch up in the centre instead. That is a real feature of the model (it is bistable there), so use *Try different random noise* to see it.

## Tab 3: The norm moves (speculative)

Tab 2 lets people move, but their sense of where "the centre" is stays put. Tab 3 adds one **assumption**: whoever is winning drags the whole crowd's sense of the centre a little toward themselves, every round. Think of an extreme position being normalised, so people start to feel the centre is over there.

| Control | What it does |
|---|---|
| How fast a new normal sets in | 0 = never (this is tab 2). Higher = the centre of the crowd slides further toward the winner each round. |
| Candidates, downvote weight, switch on at round, width of the crowd, speed | As in tab 2. |

On screen: grey = where people started, orange = where they stand now, **dashed outline = what they now treat as normal**, shaded band = the original middle. The chart underneath shows the share of people still in that original middle.

What to look for:

1. **Normal never moves**: the hills form and stop (tab 2).
2. **The extreme slowly becomes normal**: the whole crowd slides, the original middle empties, and it keeps going. The direction (left or right) is **chance**. Use *Try different random noise* to see both, and occasionally a run that does not slide at all.
3. **Same, with the equal downvote**: the candidates huddle in the middle, so the winner is the middle and the centre has nothing to slide toward.
4. **Downvote arrives late**: the slide stops, but the old middle does not come back. The new normal stays.

Be careful with this tab. It is a thought experiment, not a finding: the paper does not model this, and whether extremes really normalise is an empirical question. The spectrum also has walls (at ±3), so a crowd that slides all the way pile up against the edge.

## What this is, and is not

- It is a **mechanism demo** from a simple model, not a forecast of any real platform.
- Positions snap to a ruler of 81 steps. Candidates move one at a time, to whichever spot is best for them right now.
- The "restless" camps are real: with three or more candidates and upvotes only, there are textbook resting points, but they sit on a knife edge and the moving candidates do not settle into them.
- Left out on purpose: people who vote tactically, people who aim their downvote at whoever is most prominent, people who react against what they dislike, and counting angry replies as engagement. Several of these can weaken or even reverse the effect. The paper discusses them.
- The downvote here is **equal for everyone**. Uneven downvotes (some people dislike a lot, others never) change the picture.

## Check the maths

The JavaScript scoring engine was checked against the Python reference model on 36 test cases (three crowds, three downvote weights, four layouts): the scores and best replies agree to about 1e-13.

## Put it on GitHub Pages (recommended)

1. Create a repo and add `index.html` and this `README.md`.
2. Settings → Pages → deploy from the `main` branch, root folder.
3. Your page will be at `https://<username>.github.io/<repo>/`.
4. Share that address, not the raw file link: GitHub's "raw" link shows the code as text instead of running it. People who want their own copy can use their browser's *Save page as…* on the Pages address, or download `index.html` from the repo, and open it from their computer. It needs no internet except for the optional QR code.
5. Make a QR code of that address (the page can also draw one: open *QR code for this page*, it loads a tiny library from a CDN) and put it on the last slide.

## Credit

Based on *Free to Provoke* (Burnat & Boedts), and the classic work on location competition by Hotelling (1929) and Eaton & Lipsey (1975).
