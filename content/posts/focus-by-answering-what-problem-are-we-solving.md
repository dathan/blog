---
title: "Focus by Answering What Problem Are We Solving"
date: 2023-07-12T15:13:44-07:00
draft: false
---


#  Problem

One of the most effective ways that has helped me focus is answering the question, "What problem are we solving?". For this post, the problem that I am solving is how to communicate this idea to readers so they too can focus on what to solve.


# When there are 100 things to fix, what do you fix?

One of the better articles that I read about focusing on a problem https://jasonfeifer.beehiiv.com/p/how-to-solve-big-problems this is a great write-up. One analogy used to convey the thought is how a Physical Therapist will work their way to figure out why the patient is having a problem with their shoulder but in reality, the cause is the lower back. This reminds me of my day-to-day, finding root causes, coordinating a team, setting priorities, and incrementally getting better so the problem
goes away. How does this all work, it starts by focusing on the team.


# Method

There are three things I repeat a lot.
* What problem are we solving?
* If it's the problem, how do we measure the problem? (Any problem should be measurable, this makes it easy to communicate)
* What things are we going to try to effect that measurement?


Asking these questions focuses a team, to agree 1st that there is a problem and 2nd that everyone understands the problem that is being solved. 3rd the problem has an effect and we need to see that effect go away over time. Recording attempts and measuring the effect of the attempt reducing the problem measurement. It is best to illustrate this with a common thing that I have seen.

## Example

`The SRE team is ignoring pages. Fix it.`

So what is the problem? Is the SRE team lazy? Are the pages noisy? Is the problem that there is no process to acknowledge the pages? Is the problem that there is not a runbook to handle the page? Are the pages all describing the same issue, and only one page is being addressed?

### To have a problem to fix, let us find a measurement to define the problem

What do we measure? We measure the mean time to respond. What is that? That is the time that the on-call engineer takes to acknowledge that a page was sent. Are they all ignored? Is the mean-time to the 1st response good? Are they not going to the correct person? Is the problem a routing issue? Is the problem the pages have no actionable action? Is the problem the runbook is not complete?

To fix the problem we must experiment, and try new things to verify. We see that the meantime for a page is roughly 2 minutes, we are getting 30 pages. 
It doesn't make sense to acknowledge 30 pages, it also doesn't make sense to turn off pages. So since the 2-minute time shows that SRE is not lazy, the problem is the page noise. How do we stop the noise and not expose the team to turning off the paging system?


Experiment

We need to correlate the pages:
- Let us look at all the pages in that period.
- Let us define which pages are actionable
- Let us define which pages are noisy and move that to a warning
- Let us record the number of pages that are set to warnings
- Let us simulate the failure
- Let us verify that the pages that require action are paging
- Let us make sure each of these pages has a runbook associated with them
- Let us make sure that there is a dashboard representing the state and a graph of the problem
- Let us make sure that there is a list of warnings along with errors of the error in question

### Concrete example

*Database server is down*

200 web servers alert because the load is shooting up and 500 errors are thrown.

What is the alert that matters, the database or the 200 webservers? What needs to be answered? The database is a choke point for the system. The database requires power. The database requires a network. The probe needs a route to the database.

Let's come together as a team and say ok we need to alert on:

- power dies
- no route to host (this covers if the DB is down too)
- no available connections
- traffic drops below 10 %


In this stack, we see that if the power dies, we do not need to care about anything below it. The runbook will call onsite engineers to flip the breaker or verify the generator has fuel to power the rack.

If there is power and we do not have a route, verify the switch is up, verify the hub in the cabinet is up, and verify the host is up. If anything in that path is down, cycle it, if it still doesn't come up isolate and replace it.

If there is a route and the connections are down, connect to the Unix sock and kill off the things that are filling up the connection.

If traffic is dropping below 10% traceroute from the front ends.


Now what did we solve? We removed 200 pages per second, defined a run book, cut down on the noise, and tracked the vital paths. Giving a better stat for the SRE to post about responsiveness and keeping the SLO stable while achiving the SLA.


## Conclusion

Focusing on what is the problem we are solving has helped me out in the long run. I hope it helps you to, and it starts by asking the question, "What is the problem we are solving"
