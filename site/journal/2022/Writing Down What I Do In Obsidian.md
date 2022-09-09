---
title: Writing Down What I Do—In Obsidian
subtitle: An update on my years-long habit, with a new tool.
tags:
    - working effectively
    - Obsidian

qualifiers:
    audience: >
        People who are interested in working effectively, particularly with an eye to keeping track of accomplishments, building “brag docs,” etc.

date: 2022-09-08T20:45:00-0600

templateEngineOverride: md

---

Over the past year or so, I have transitioned my note-taking out of [Bear][b] and into [Obsidian][o]. The piece of my notes system I took longest to transition over, for a variety of reasons, was my habit of writing down what I do (see [here][log-1] and [here][log-2] for previous write-ups). Getting [my basic Obsidian config][config] to a point where I was mostly satisfied with the typography meant I was comfortable enough with using it for work tracking.

[b]: https://bear.app
[o]: https://obsidian.md
[log-1]: https://v4.chriskrycho.com/2018/just-write-down-what-you-do.html
[log-2]: https://v4.chriskrycho.com/2019/update-writing-down-what-i-do.html

Sitting down last Friday to wrap up my week, I was doing my usual dance of copying over my daily summaries into the week-level note to help with my weekly review and *its* summary. This has been a fairly repetitive and error-prone process for me in the past. Sometimes writing up the summary of the week reminds me of something I did one of the days, which I want to include for posterity, so I have to write it up in both the week note *and* the daily note. It is easy for those to get out of sync. Yes, this is a function of my own fastidiousness about this note-keeping, but I genuinely find that very valuable when I look back at these for mid-year or annual reviews. But it is a pain in the neck to *do*.

Then I had a flash of inspiration: Obsidian has the fantastic idea of [block embedding][be].[^ideas] Block embeds are wiki-style links that embed the content of the corresponding part of the linked note. That works most directly and easily with headings, though Obsidian will also generate references for paragraphs, lists, etc. if you so choose.

[be]: https://help.obsidian.md/How+to/Link+to+blocks

You write a block embed like this:

```markdown
![[other-note-id#heading]]
```

My work notes have a fractal structure to them: Every view is just a more granular or more abstract view of what I’ve done over a given period of time, but by definition has the same structure, though possibly with additional *sub*-structure. In particular, every single note has an **Outcomes** heading, with **Summary** and **Artifacts** subheadings.[^sub-outcomes] Each level of note above the daily note has links to the lower-level note which makes it up, so weekly notes link to daily notes, monthly notes to weekly, and so on. (There are links the other way for easy navigation, too, but those are not as relevant to the work of summarizing!) Given the ability to embed blocks and the fractal structure, then, I realized I can directly embed (as well as link to) the level down.

Here's how that might look, stealing from last week's weekly note:

```markdown
## Outcomes

- [[Work/Tracking/2022.08.29|2022.08.29]]: ![[Work/Tracking/2022.08.29#Outcomes|2022.08.29]]

- [[Work/Tracking/2022.08.30|2022.08.30]]: ![[Work/Tracking/2022.08.30#Outcomes|2022.08.30]]

- [[Work/Tracking/2022.08.31|2022.08.31]]: ![[Work/Tracking/2022.08.31#Outcomes|2022.08.31]]

- [[Work/Tracking/2022.09.01|2022.09.01]]: ![[Work/Tracking/2022.09.01#Outcomes|2022.09.01]]

- [[Work/Tracking/2022.09.02|2022.09.02]]: ![[Work/Tracking/2022.09.02#Outcomes|2022.09.02]]

```

This renders the contents of the daily work note directly in line. The folder organization with `<full path>|<short title>` means these wiki-links work in *every* tool that understands wiki-links (for example: I use [iA Writer][ia] a lot for note-taking on iPad at present) but still look nice.

[ia]: https://ia.net/writer

<!-- TODO: add screenshot -->

The basic workflow for me now is:

## Video walkthrough




## Bonus: Templates

<details>

<summary>Daily note template</summary>

```markdown
---
aliases: ["{{date}}"]
---

**Week:** ==TODO==

## Goals

### Quarterly deliverables

- [ ] ==TODO==

### Miscellanies & administrivia

- [ ] ==TODO==


## Meetings


## Details

### Session 1

1. **Goal:** **Actual:**


## Outcomes

### Summary


### Artifacts


## Hours Standing

- [ ] 1
- [ ] 2
- [ ] 3
- [ ] 4
- [ ] 5

```

</details>

<details>

<summary>Weekly note template</summary>

```markdown
---
aliases: ["YYYY.MM.DD – YYYY.MM.DD"]
---

**Month:** ==TODO==

## Goals

### Quarterly deliverables

- [ ] ==TODO==

### Miscellanies & administrivia

- [ ] ==TODO==


## Details

- [[Work/Tracking/YYYY.MM.DD|YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD#Outcomes|YYYY.MM.DD]]

- [[Work/Tracking/YYYY.MM.DD|YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD#Outcomes|YYYY.MM.DD]]

- [[Work/Tracking/YYYY.MM.DD|YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD#Outcomes|YYYY.MM.DD]]

- [[Work/Tracking/YYYY.MM.DD|YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD#Outcomes|YYYY.MM.DD]]

- [[Work/Tracking/YYYY.MM.DD|YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD#Outcomes|YYYY.MM.DD]]


## Outcomes

### Summary


### Artifacts

```

</details>

<details>

<summary>Monthly note template</summary>

```markdown
---
aliases: ["YYYY.MM"]
---

**Quarter:** ==TODO==
**Year:** ==TODO==

## Goals

### Quarterly Deliverables

- [ ] ==TODO==

### Miscellanies & administrivia

- [ ] ==TODO==


## Details

- [[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD|YYYY.MM.DD – YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD#Outcomes|YYYY.MM.DD – YYYY.MM.DD]]

- [[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD|YYYY.MM.DD – YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD#Outcomes|YYYY.MM.DD – YYYY.MM.DD]]

- [[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD|YYYY.MM.DD – YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD#Outcomes|YYYY.MM.DD – YYYY.MM.DD]]

- [[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD|YYYY.MM.DD – YYYY.MM.DD]]: ![[Work/Tracking/YYYY.MM.DD – YYYY.MM.DD#Outcomes|YYYY.MM.DD – YYYY.MM.DD]]


## Outcomes

### Summary


### Artifacts


```

</details>

<details>

<summary>Quarterly note template</summary>

```markdown
---
aliases: ["YYYY.MM – YYYY.MM"]
---

**Year:** ==TODO==

## Goals

- [ ] ==TODO==

## Details


- [[Work/Tracking/YYYY.MM|YYYY.MM]]: ![[Work/Tracking/YYYY.MM|YYYY.MM]]

- [[Work/Tracking/YYYY.MM|YYYY.MM]]: ![[Work/Tracking/YYYY.MM|YYYY.MM]]

- [[Work/Tracking/YYYY.MM|YYYY.MM]]: ![[Work/Tracking/YYYY.MM|YYYY.MM]]

## Outcomes

### Summary

### Artifacts


```

</details>

<details>

<summary>Annual note template</summary>

```markdown
---
aliases: ["YYYY (FY)"]
---

## Goals

- [ ] ==TODO==

## Details

- [[Work/Tracking/YYYY.MM – YYYY.MM|YYYY.MM – YYYY.MM]]: ![[Work/Tracking/YYYY.MM – YYYY.MM#Outcomes|YYYY.MM – YYYY.MM]]

- [[Work/Tracking/YYYY.MM – YYYY.MM|YYYY.MM – YYYY.MM]]: ![[Work/Tracking/YYYY.MM – YYYY.MM#Outcomes|YYYY.MM – YYYY.MM]]

- [[Work/Tracking/YYYY.MM – YYYY.MM|YYYY.MM – YYYY.MM]]: ![[Work/Tracking/YYYY.MM – YYYY.MM#Outcomes|YYYY.MM – YYYY.MM]]

- [[Work/Tracking/YYYY.MM – YYYY.MM|YYYY.MM – YYYY.MM]]: ![[Work/Tracking/YYYY.MM – YYYY.MM#Outcomes|YYYY.MM – YYYY.MM]]

```

</details>



[^ideas]: An aside: I had the *exact* same idea when working on [<b><i>re</i>write</b>][r]… but my idea never went anywhere, because I put that work on indefinite hiatus. Ideas are cheap. Execution is what counts.

[r]: https://rewrite.software

[^sub-outcomes]: I don’t always preserve the distinction between “Summary” and “Artifacts” but it is sometimes helpful in distinguishing between the gist of what I did and the kinds of items I can actively share to represent that work to someone else—pull requests opened or reviewed, documents written or reviewed, etc.