---
layout: post
title: !binary |-
  VGhlIEthbmJhbiBNZXRob2RvbG9neQ==
wordpress_id: 252
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yNTI=
date: 2009-11-16 19:27:38.000000000 +00:00
---
Now I've had some experience of working in a scrum environment, I was keen to find about other similiar methodologies. Kanban (which literally means - visual card) is a methodology direct from manufacturing, specifically in Japan. Limits and constraints are embraced to allow the smooth flow of tasks.

A board is used to map flow of tasks, but generally with extra steps compared to a scrum board. Some of these steps are buffers, indicating that there may be inefficiencies or constraints which are hindering the flow, i.e. tasks which are in the 'awaiting uploading' stage indicates that the uploading stage may have inefficiencies which constrain the throughput.

Each stage has a limit, nominally set to twice the number of people working on the stage minus 1. The limits can be amended , but care must be taken that flow is increased rather than decreased. Work is managed on a pull basis. No one pushes work from left to right, people pull the work from the previous stage. This changes the stress that people encounter, they can only work at the limit which is set, they are not allowed to take on work which would take them above the limit. They can only take things on when they have spare capacity.

I love how it works when there is spare capacity. If there is no task to pick up from the previous stage and say there are too many tasks in the test stage, then rather than jumping in to help someone else or do some testing, use the time to improve the efficiency of the process. Write a tool to make deployment faster etc. It's in an inbuilt part of the processes that inefficiencies (when people are idle) work as a positive feedback loop in to the process to then speed things up, self healing!

It was felt that kanban worked particularly well with

* dedicated teams - keeps variance low
* tasks of a similar size - again variance
* better on maintenance than big build projects, although it can work with both.

Trust underpins it all, building trust for teams and for the client/customer. When we estimate we always add security, then others add further security and on and on we go until the actual estimates are wildly different from how long it takes to do the piece of work!

If you're blocked you can't take on extra work over your limit. Forces concentration on blockers! Each worker has a magnet for the board, they have two magnets which are attached to whatever they are working on, they cannot work on anything else. Forces completion of tasks, and if there is idle time, work on the process.

No planning or estimating in proper kanban process, the devs do the dev, testers test. Someone still has to break the tasks down, but there is an element of ensuring the spec'd bits are the right size too.

The board uses different coloured postits and blockers are stuck on tasks which are stuck. Each day which a task remains in a stage, annotate it with a dot, so you can see how fast it is going.

A few side notes: as a knowledge worker it's important to remember that knowledge is perishable, if we accumulate it but don't use it then it will decay....

if you are sawing down a tree, is it worth stopping to sharpen your saw on a regular basis? Why yes!

For my workplace, I think we still have a lot to learn from scrum - have we ensured that we're following scrum properly and learning the lessons from that before we'd think about taking a new process on. However, there are some principles which are always worth thinking about, especially when it comes to trust within organisations. If however, we had a maintenance team, with analysts, devs, testers - across projects, then I think kanban could prove really useful
