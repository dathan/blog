---
title: "Engineering Methods Based on Fictional Characters"
date: 2023-05-30T15:49:07-07:00
draft: false
---


## Problem

What are effective strategies for an engineer to communicate with their peers and answer their inquiries efficiently?

## Solution

Appeal to your fellow engineers through shared cultural touchstones, like the well-known characters from science fiction that most engineers are familiar with.

## Case: Time Estimation in Software Engineering

Every software engineer inevitably has to provide an estimate for when a code block, task, or project will be completed. Defining what "done" means can be complex. Does "done" mean when the software engineer gets it to work once? Is it when the solution has undergone thorough testing as per the team's established processes? Is it when the code is deployed, activated, or when a customer runs the code without encountering any issues?

First and foremost, I ensure these questions are addressed. Then, I consider the effort required for the task, whether there's enough time for writing tests, and then I use the "Scotty Method". Here's where we can borrow from our favorite fictional characters to elucidate this concept.

### What is the Scotty Method?

Arguably the most iconic fictional engineer is Scotty from Star Trek. In my opinion, he surpasses Lt. Commander La Forge from the Next Generation series because he never revealed the actual potential power output. Scotty always managed to squeeze out just a bit more power from the warp engine to go just a tad faster. Essentially, `Scotty padded the numbers`. So when providing an estimate, utilize the Scotty Method and add at least 45% to your initial estimate. This is a classic case of under-promising and over-delivering. `Avoid providing the exact time frame you believe the problem can be solved in.`

## Case: Identifying System Issues

As a Systems Reliability Engineer (SRE) or a backend engineer in platform engineering, you'll be asked, "Why did this break?" Frequently, engineers attribute the issues to the network, insufficient IOPS on the disk, or problematic code. Unfortunately, these explanations often fail to identify the root of the problem, as they are biased towards what's observable rather than the underlying cause.

To mitigate this, I prefer using the "Sherlock Holmes method", which is best summarized as: `Rule out what is known, so the only thing left is the unknown`.

### What is the Sherlock Holmes Method?

Consider this scenario: the architect asserts that a particular problem could never occur with this system and suggests searching elsewhere for the cause. The architect's knowledge and intimate understanding of the system might create a bias. They may overlook the fact that someone else could modify the code, thereby disrupting the architect's intended functioning. It's essential to verify such 'never' statements. Although the architect is often correct, this presumption should not prevent an investigation.

Once it's confirmed that a 'never' statement is indeed valid, the next step is to identify any recent changes or new elements. By systematically narrowing down the possibilities, you can significantly reduce the mean time to resolution of the root cause.

### Conclusion

Engineers often appreciate references to science fiction and fantasy. Leveraging familiar characters' strategies to elucidate and answer problems can be remarkably effective. Remember, these characters are successful because they're grounded in real-world applications. Use that as a guide to explain and solve issues.
