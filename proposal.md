---
layout: article
title: Proposal
---

<!--

# Project Proposal

For the proposal, you have to finalize your teams of 3, propose an idea for your
course project, describe the evaluation plan, and set up a project website with
a page for this submission. If you have a team of 2, you'll have to either find
someone to join you, or break up and join another team of 2. We expect you to
maintain a private Github repository for the code, and an associated website.

## Summary of the Project

In a paragraph mention the main idea behind your project. Focus on the problem
setup, not the solution, i.e. what is your goal? At the very least, you should
have a sentence that clearly explains the input/output semantics of your
project, i.e. what information will it take as input, and what will it produce.
Mention any applications, if any, for your project.

## Evaluation Plan

Mention how you will evaluate the success of your project. In a paragraph, focus
on the quantitative evaluation: what are the metrics, what are the baselines, by
how much you expect your approach to improve the metric, what data will you
evaluate on, etc. In another paragraph, describe what qualitative analysis you
will show to verify the project works, such as what are the sanity cases for the
approach, how will you visualize the internals of the algorithm to verify it
works, what’s your moonshot case, i.e. it’ll be awesome and impressive if you
get there. Note that these are not promises, we’re not going to hold you to what
you say here, but we want to see if you are able to think about evaluation of
your project in a critical manner.


## Goals

Next pick 3 goals. The first goal is the minimum goal. This is the minimum your
project should achieve to pass the course. The second goal is the realistic
goal, this is a goal you will likely achieve during the course and should
provide some interesting results. The third goal is the ambitious one, this
would provide you awesome results but would be difficult to achieve. For
reference think of how goals are described in crowdfunding projects like
Kickstarter.

Break down the minimum goal into 2 milestones, the first one of which should be
achieved by February 7. For the realistic goal also define 2 milestones. For the
ambitious goal define 1 milestone. The milestones have to be verifiable based on
what you define in your evaluation plan section. List the 5 milestones (in
total) as 5 bullets breaking down the 3 goals.

## Appointment with the Instructor

One member should schedule for the team an appointment with the instructor in
the week starting 01/27 (or 02/03, if no slots are available). Try to select a
time such that all members of the team can attend (there shouldn’t be conflicts,
since we are meeting during lectures). On the proposal page, mention the date
and time you have reserved the appointment for.

You can make select a time using https://calendly.com/uci-cs175rl-w20

-->

## Summary

One of the key measures of a reinforcement learning algorithm is its sample
efficiency. Despite the recent success of deep reinforcement learning on a wide
variety of tasks {% cite Mnih2015 DBLP:journals/corr/HeessTSLMWTEWER17 %}, it is
still difficult to train an agent in a manner that is both performant and sample
efficient. One popular approach to solving this problem is to incorporate
demonstrations from humans or other controllers, as in {% cite AAAI1816976 %}.
Demonstrations provide a "starting point" for the agent, so that it does not
have to waste steps wandering the environment. Meanwhile, looking at supervised
learning, a common approach to improve performance involves ensembles,
essentially collections of models whose predictions are aggregated to create a
more accurate prediction {% cite Goodfellow-et-al-2016 %}. Though ensembles have
been attempted before in deep reinforcement learning, they have not gained much
traction. Yet, we believe they may hold some promise, as {% cite Faußer2015 %}
has shown that feeding environment interactions to an ensemble, instead of a
single agent, can lead to better performance on tasks such as SZ-Tetris. Thus,
we seek to combine these two approaches -- demonstrations and ensembles, and
investigate their effects on sample efficiency and performance. Specifically, we
seek to implement our algorithms (likely an actor-critic method such as
{% cite soft-actor-critic %}) in the Duckietown platform {% cite duckietown %}
and ultimately compete in the lane following challenges of the AI Driving
Olympics {% cite aido %}.

## Evaluation Plan

### Quantitative

We will evaluate our project by running it in the Duckietown platform. Due to
the compressed timeline of this project, we will focus on running in simulation,
as real robots introduce technical difficulties that are out of scope. Within
the Duckietown platform, our goal will be to perform the LF (Lane Following),
LFV (Lane Following with dynamic Vehicles), and LFVI (Lane Following with
dynamic Vehicles and Intersections) tasks of the AI Driving Olympics. The
metrics for our project will consist of the performance metrics defined in
{% cite aido %} -- namely, Performance, obedience to Traffic Law, and Comfort.
In addition to these metrics, we will measure sample efficiency by looking at
our agents' performance after various numbers of interactions with the
environment. We plan to vary our algorithms along two axes -- with and without
demonstrations, and with varying ensemble sizes. Our baseline will be an agent
that does not use any demonstrations and has an ensemble of size 1 (i.e. a
single model). As we have little prior experience with Duckietown, it is
difficult to estimate how much better our algorithms will do, but based on the
performance improvements described in {% cite Faußer2015 %} and
{% cite AAAI1816976 %}, we estimate that adding ensembles and demonstrations
will cause our policies to have 50% improvement in performance over the
baseline, while requiring on the order of 10<sup>7</sup> fewer episodes to
achieve the same performance as the baseline agent. To summarize, we will
evaluate our algorithms on the AI Driving Olympics in Duckietown on the basis of
performance and sample efficiency.

### Qualitative

We will evaluate our performance qualitatively by watching videos of our agents'
performance in the Duckietown simulation (and perhaps in real world). We will
know our agent is working if it is successfully completing the lane following
challenges, i.e. driving along the road in the simulation. To visualize the
internals of our algorithm, we will plot the average return of the agent after
various numbers of environment interactions and training steps, as well as the
loss functions of our neural networks. In general, loss should converge to zero,
while return should increase and stabilize at an asymptote. As a stretch, we
could evaluate our algorithm on a physical Duckiebot at UCI, and as the ultimate
moonshot, we could submit our algorithm to the upcoming iteration of the AIDO.

## Goals

1. Minimum Goal: Train and evaluate ensembles of actor-critic models
   - Milestone 1 (due February 7): Implement and evaluate a Soft Actor-Critic
     agent in the LF challenge
   - Milestone 2: Implement a Soft Actor-Critic agent that uses an ensemble, and
     evaluate it in the LF, LFV, and LFVI challenges
2. Realistic Goal: Incorporate demonstrations into the agent and evaluate it on
   the LF, LFV, and LFVI challenges
3. Ambitious Goal: Transfer the algorithms to a physical Duckiebot and compete
   in the next iteration of AI-DO

## References

{% bibliography --cited %}
