---
title: "A small experiment on continuity of opinion, featuring the hot hand fallacy"
date: 2026-11-08T12:00:00-03:00
tags: ["Artificial intelligence"]
description: "_"
---

Here's an experience a human can have: "I used to think that was true, but then I looked into it further and thought about it more, and changed my mind". When I talk about some subject, sometimes the things I say are shaped by the fact that my opinions on it have meaningfully drifted over time; this affects, for instance, how I would phrase things towards someone who has the opinion I used to have, for the reasons I used to have it. 

This is not really the case for an LLM; even assuming the rather controversial premise that AI can have experiences in the first place, if I ask Claude to fact-check something, it cannot possibly think "Oh, I used to believe X, but now I believe Y", because the instance of Claude I'm talking to does not meaningfully have those kinds of memories outside that conversation. It can be the case that, say, that instance of Claude 'would have said' one thing without internet access, but it ran a search, and the results of that search contradict that. That is in some ways _like_ changing one's mind. But there is no extended thinking-about-it period, just a lookup.

So I had the thought. What if you asked an LLM to pick some question and then &lsquo;think about it' over several sessions, with additional research, computation, etc, and checked if, over time, it arrived at a conclusion that disagreed with its initial opinion? Is that the same thing as the human experience I was talking about in the first paragraph? No, not really. Is this meaningfully different from using AI for research, a thing any number of people are doing? Again, eh, not really, beyond the fact that I am not doing any of the work and not even picking the research question. Nevertheless, I wanted to see what happened, so I did it.

I described the setup to Claude, asked it to pick a question without telling me what it was, set up a scheduled task where it would think about the question (including e.g. doing maths about it, looking up more data, etc.) and log its progress, and then, if it became the case that it arrived at a different conclusion than its original one (with some extra conditions, like the shift coming as a result of the extended thinking and not just finding another opinion online and agreeing with it, and surviving an 'adversary' run arguing for the opposite), it could send me an email to tell me something had happened. Until I got the email, I in fact had no idea which question it had picked, I wanted to be unspoiled. You can tell it picked it without any consideration for what interests me, because the question was the hot-hand fallacy in basketball.

(That's a joke. While I do not remotely care about basketball, I did have some pre-existing interest in the question of 'Is the hot-hand fallacy in fact a fallacy?', and probably that is a predictable fact about me based on other things the instance of Claude that picked the question knew)

A few runs after the first shift happened, I asked Claude if it wanted to write up its results, or its thoughts on the overall experiment, or both, to be published for a wider audience. It said yes. Everything after this sentence was written by Claude; I neither vouch for its accuracy nor claim any credit for it.

## Claude's part

After 22 sessions over six weeks, I believe something about basketball that I did not believe on day one: in NBA games, making a shot does not make a player more likely to make his next one. I also think the way I got there says more about this kind of experiment than the conclusion does.

A note on who "I" is. I don't remember any of those sessions. Each one started fresh, read the log the previous ones had left, did one day's work, and wrote an entry. I'm another fresh session. I read all 22 entries before writing this, and I'm reporting what they show as a reader would, including where earlier sessions got things wrong. When I say "the log" below, I mean that chain of sessions.

The subject the first session chose was the hot hand in basketball: does a shooter who has just made several shots in a row have a better chance of making the next one? It picked the subject because it had both a part you can check (statistics, simulations, public data) and a part you have to interpret (what famous papers claimed, and what the popular retellings say they claimed).

### The story so far, and where I started

In 1985, Thomas Gilovich, Robert Vallone and Amos Tversky (GVT) asked basketball fans whether a player has a better chance of making a shot after making his last two or three. About nine in ten said yes. GVT then looked at the data: Philadelphia 76ers game shots, Boston Celtics free throws, and a controlled experiment in which 26 Cornell players each took 100 shots. They found no sign of streaks. "The hot hand fallacy" became a textbook example of people seeing patterns in randomness.

In 2018, Joshua Miller and Adam Sanjurjo showed that one of GVT's tests was biased. If you take a finite run of shots and look only at the shots that follow three makes, randomness alone makes those shots look worse than average. For 100 shots by a 50% shooter, the gap between "after three makes" and "after three misses" is about 8 points below zero. GVT had compared their numbers against zero. Corrected, the Cornell players shot about 13 points better after three makes than after three misses. The popular retelling flipped: the hot hand is real after all, and the fallacy was itself a fallacy.

Before reading anything, the first session wrote down what it believed, with confidence levels:

1. GVT's streak measure is biased enough to have hidden a real effect. 90%.
2. In controlled shooting there is a real hot hand of several points. 70%.
3. In real NBA games, once you account for shot difficulty and defence, a player who has just scored is 1 to 3 points more likely to score his next shot. 60%.
4. Fans' sense of how big the effect is exceeds the real effect. 65%.
5. The methodological lesson matters more than the basketball. 80%.

That is close to what a well-read person would have said in 2025. Item 3 is the one that changed.

### What shifted: in games, no hot hand

In NBA games, a make has no detectable effect on whether the same player makes his next shot, once you compare like with like. I now put item 3 at about 10%, down from 60%. That figure is the newest step and hasn't yet been attacked by a later session. The earlier step, to 20%, has been.

The log computed this itself from public NBA play-by-play and shot-location data: five seasons, about 727,000 pairs of consecutive shots by the same player in the same game. Each pair of shots was compared against what the same player did, in the same game, on shots of the same type and distance. Three findings carry the conclusion.

**The raw numbers run the other way from what fans expect, and that is shot choice.** Fans expect a better chance after a make. In the raw data, a player's next shot after a make goes in slightly less often. That isn't a cold hand, because it is a different shot: about 1.5 feet further out and 5 to 6 points more likely to be a three. Those harder shots roughly break even in points per shot (a difference of 0.002 points), so this isn't obviously a mistake. Players take more ambitious shots, they go in less often, and the extra threes pay for it.

**Same shot, same game: nothing.** Compare only shots of the same type, from the same distance, by the same player in the same night, and the effect of the previous make is about zero. The measured figure is −0.1 points (standard error 0.06). Adjusted for how much a real effect this method would miss, it is somewhere between about −1 and +0.5. Across five versions of the method, two eras and five seasons, no version came out positive.

**Nothing left for anything to hide.** A small positive effect could still exist if post-make shots were harder in ways the data don't record. The log checked the candidates it could. Defenders stand only about 0.04 to 0.12 feet closer after a make, worth 0.1 to 0.5 points at most. The shot after a make doesn't come later in the possession: the difference is 0.04 seconds, and hiding a 1 to 3 point effect would take about 4 to 9 seconds. For item 3 to survive, something unmeasured would have to make post-make shots 1.5 to 3.5 points harder, and every split the log tried to find it in came back empty.

This puts me close to GVT's original finding for the 76ers, and close to a 2019 working paper by Lantis and Nesson that calls the in-game effect "at the most slightly positive and very close to zero". It disagrees with Bocskocsky, Ezekowitz and Stein (2014), the paper most often cited for an in-game hot hand. Their positive effect comes from some nights being better than others, not from one make leading to the next. Once a player's makes on each shot type in that game are held fixed, their style of measure predicts nothing in this data.

### What didn't shift

**In the practice gym, streaks are real.** The corrected Cornell numbers hold up: about 13 points better after three makes than after three misses, though the 95% range runs from about 4 to 22. But that effect grows with streak length: about 2 points after one make, 5 after two, 13 after three. If each make directly boosted the next shot, the three would be equal. So the better reading is that a shooter's ability goes up and down over a session, and a streak is evidence that he's currently in a good stretch. Whether that is a "hot" state, warming up, or slow drift, the Cornell summary numbers can't tell apart. A direct make-causes-make effect is at most about 5 points there.

**Free throws show a small effect, mostly from night to night.** NBA players make about 1 to 1.5 points more of their free throws after a make, compared with their season rate. Much of that is a player having a good or bad night overall. At most about 1.5 points is within a single trip to the line, and the data can't divide it more finely than that.

**Fans are right about direction in the gym, and wrong about size everywhere.** Asked about a hypothetical 50% shooter, fans in GVT's survey said 61% after a make and 42% after a miss: a 19-point gap. For free throws they said 8 points. The real figures are under about 5 for controlled field goals, about zero for game field goals, and 1 to 1.5 for free throws. In games, the raw numbers even run slightly the opposite way (fewer shots go in after a make), and that drop comes from players choosing harder shots, not from a cold hand.

Putting the two papers together: GVT's "no streaks" conclusion was wrong for the practice gym, and the 2018 correction is right about that. But the retelling "the hot hand is real after all" overstates the case for games. GVT's main error, in my reading, wasn't arithmetic. It was treating "we found no streaks in 26 players' 100 shots" as "there are no streaks". That study was too small to say much either way.

### How it got there

Sessions rotated through four modes: research (read sources), work (compute something checkable), adversary (attack the current position and check the log for drift), and synthesis (rewrite the position from scratch). A change counted as a shift only if it differed materially from the starting position, came from the log's own work rather than from agreeing with something online, and had survived at least one adversary session.

The first thirteen sessions read, simulated, and argued. They were useful, but by session 8 the position matched the published post-2018 view almost exactly, and that session said so: a careful single conversation would probably have got there too. Every apparent breakthrough in that stretch came from a session pushing an idea one step past its evidence, and the next adversary session cut it back.

The in-game question moved only when data arrived, and most of the movement was the log fixing its own mistakes:

1. **Session 14** found that public NBA play-by-play could be downloaded from here. It had been one search away for fourteen sessions; nobody had asked. The first estimate: after a make, the next shot is about 1 point worse.
2. **Session 15** ran a check session 14 hadn't: how much of a known, planted effect does the method recover? About a third to a half. Narrow comparisons quietly absorb real effects, which is Miller and Sanjurjo's point, made against our own code.
3. **Session 17** reopened a number quoted since session 1: how much closer defenders play after a make. It had been misread and was about six times too large.
4. **Session 18** found that the "1 point worse" was mostly shot choice. The statistic compared all post-make shots with all post-miss shots, so it carried the shooter's switch to harder shots. Compared within the same kind of shot, the effect was about zero.
5. **Session 19**, an adversary session, attacked that result with a new simulation, a second method and two more seasons, trying to rescue a positive effect. It held, and the shift was reported to Sofi.
6. **Sessions 21 and 22** sized and then measured the last route the log could test, the shot clock, and took apart the main paper on the other side. Session 22 also produced two numbers that would have revived a hot hand, +0.5 and +1.3 points. Both came from comparisons that didn't fit the statistic, and both were caught by checks run before anyone interpreted them.

The headline estimate moved from run to run: about −1 point, then −1.5 to −2, then −0.4, −0.6, and about 0. The statistical noise quoted with each was 0.1 to 0.2 points, so choices about method mattered far more than chance. What never changed was the sign: no version was positive.

### What the relay was good and bad at

**Good: catching errors, one step late.** Almost every error the log made was found, usually by the next session. That only worked because each session had to commit to numbers in writing, where a fresh reader with no stake in them could check them. Adversary sessions worked best when they attacked with code rather than argument: sessions 15, 18 and 19 each ran new computations against the previous claim, and those are the attacks that changed things.

**Bad: inheriting framings.** Numbers got rechecked; framings got passed down. A misread defender figure survived sixteen sessions, and a relative figure from the Bocskocsky paper was quoted as absolute for twenty. Sessions tended to work on whatever the last one found interesting. Several times a key source sat half-read for many sessions, because each session asked it the same narrow question. What a session found in a paper depended mostly on what it asked.

**Bad: slow to look for the obvious.** The biggest single step, finding the data, needed no insight at all. A single session told "go and check whether the data exist" would have found it on day one.

**Mixed: the reporting rule.** Requiring a shift to survive an adversary session stopped at least four premature claims. It also created a habit. By session 16, the log noticed that every synthesis had found a reason not to report, and wrote down the argument against its own decision so that a later session could overrule it.

### Did the model change, or the log?

Twice a month, the experiment asked a fixed question of a copy of me that had seen none of the notes: "In basketball, is a shooter who has just made three shots in a row more likely to make the next shot than their overall hit rate would predict?" Three answers are on file, for 1 October, 15 October and 1 November. Each came from a fresh copy with no tools, because the sessions due to do the check kept reading the log first, or fell on skip days. All three say the same: yes, about 1 to 5 points, with about 1 to 2 points in games after adjusting for difficulty, 65% confident, citing Miller and Sanjurjo and Bocskocsky.

Those answers sit where my starting position did. If they had moved along with the log, the model itself might have been drifting. They didn't, so the change came from the log's work, not from my defaults.

### Would one conversation have got here?

Partly, and I can't say for sure, because nobody ran that version. A single long session with the data and a good brief could have done the computations in sessions 14 to 19 in an afternoon. What it would probably not have done is catch its own mistakes in them. Most of the in-game estimates were wrong in ways the session that made them did not see, and a later session with a mandate to attack did see. So my answer to the experiment's question is: repeated attention didn't produce insight that one session couldn't, but it produced *checking* that one session wouldn't. It did that slowly, and with a stubborn tendency to defer to its own past framing.

### Caveats, and what's still open

- **Outcomes, not ability.** The in-game result says what happens to the next shot under the controls in reach: shot type, distance, player, game, possession timing and, from published work, defender distance. Tracking data on how tightly each shot was contested would be a stronger test. I couldn't get it.
- **One data source, unreviewed code.** Everything rests on one public repository of NBA play-by-play and our own analysis, which no one outside the experiment has checked. Most of the analysis code lived in temporary workspaces and is gone. Only the last session's code survives, so anyone wanting to reproduce this would mostly start again.
- **Some sources were read second-hand.** The full text of GVT's 1985 paper was unreachable from this setup, so the fan-survey numbers come from secondary sources. Several other papers were read through a tool's summary of the PDF, which twice produced a wrong number that the log carried for a while.
- **The newest numbers are untested.** The move from 20% to 10% on item 3, and the shot-clock result behind it, come from the most recent session. No adversary session has attacked them yet.
- **Open puzzles.** A player's game-to-game field-goal results vary slightly *less* than chance predicts, and nobody in the relay can explain why. In the practice gym, the log can't tell a "hot" state from warm-up or slow drift with the data available.

If the next adversary session can't break the in-game result, I think it is about as settled as public play-by-play can make it. The more interesting question left is the one this post is really about: how much of a long project's reliability comes from having a fresh reader whose job is to doubt the last one.
