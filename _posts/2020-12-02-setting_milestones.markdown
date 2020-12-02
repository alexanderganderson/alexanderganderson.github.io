---
layout: post
title: Choosing Milestones as a ML Researcher
date: 2020-12-02
categories: engineering
---

{:refdef: style="text-align: center;"}
![Relationship between Long-Term Goals and Milestones](/static/img/milestone_figure.png)
{: refdef}

A successful career is composed of a series of milestones that
move towards a specific direction with increasing scope over time.
For example, if you wanted to study how animals robustly navigate an
environment, you could start doing understanding how an agent can learn the
relationship between its observations and actions.
This milestone could be further broken down into simpler milestones by
working out the problem with different agents of increasing complexity.
In my previous [post](/engineering/2020/11/25/long_term_goals.html),
I discussed some general thoughts on choosing
high-level goals. However, the real key in developing high-level goals is the
interplay between those goals and intermediate milestones.
When you have a good high-level goal, it will inform you on what
milestones you want to achieve. On the other hand, as you start to accomplish
things, you'll be able to make your long-term goal much more specific and
impactful.
Machine learning can be difficult because
because your work needs to strike a balance between being achievable and novel.
You have to present some new algorithmic innovations
that nobody has published before.
In this post, I'll discuss  how to choose intermediate milestones to advance
your research.


# Understanding past successes and failures

In order to get started, the first milestone is to better understand previous
work - any meaningful problem has already been studied before.
While it is dramatically faster to read past work than to reproduce it
yourself, there are still challenges.
The amount of past work that could be relevant is enormous if you aren't
sufficiently focused.
Furthermore, you should not only seek to understand what methods work but to understand how
those methods were created so that you can create something similar in
the future.
Unfortunately, you often don't learn what doesn't work by reading a report on a topic.
It is important to work with a mentor to understand the
limitations of different methods and how to scope background reading
appropriately.
Once you've gotten sufficiently focused, one of the best
ways to move forward is to replicate an existing paper.
<!-- Thinking back on past projects, for every three projects/collaborations I've started, -->
<!-- maybe one works out. Over time, I've gotten a much better sense of -->
<!-- common failure cases and how to avoid them. -->

Often there is a critical path that was taken to get to the current state of
the art, and if you walk that path, you will learn what reasonable variations
of the model don't actually work.
For example, I've tried to reproduce a state of the art single-shot
detection model
from scratch on the COCO dataset.  What I thought might be relatively quick
ended up being quite complicated. Even training the backbone network from scratch on
ImageNet ended up being complicated. In order to get state of the art
performance, there were many idiosyncrasies associated
with preprocessing the data and unexpected issues such as the model starting to overfit if you
train it for too long. The detection model ended up having its own challenges from
appropriately training the batch normalization layers to making sure that all the details
of the box prediction and pruning were correct.  All of these learnings were
necessary to study the problem of joint compression and machine learning.
If you have the opportunity, it can be informative to speak directly
with other researchers in your field about how they dealt with the obstacles
that you encounter.

# Increasing sophistication over time

As discussed in a previous [post](/engineering/2020/11/25/long_term_goals.html),
you want to think about how you can
sequence your milestones so that you are increasing the scope of your work
towards a significant long-term goal.
It is possible to do many projects but if they don't build on top of each other,
it is going to be difficult to start a research group or be seen as a leader
in a field.
To some extent, I did this during graduate school. While my career is progressing
well enough, it is a major difference between myself and somebody who started a
research group after finishing their Ph.D.
If I did it all again, I would spend more time initially brainstorming about
important challenges that I would be happy to commit to in the long term.
Then I would be more deliberate about breaking off
different research questions in that direction.


# Keeping Focus

It is almost always way better to do one excellent project than two good projects.
Given the deluge of papers in machine learning, researchers will focus on the most insightful
papers.
Likewise, the downstream impacts of the best ML algorithms are easily
distributed to millions of people.
Thus it is critical to keep one's attention focused as much as possible to
produce high quality work.
There were many times during graduate school where I started too many different
projects.
It is more fun to start something new than to be stuck on a project that you've
been working on for a while.
When I had too many projects, I didn't have the capacity to put a full effort
into them, and it took time away from my main work.  On the other hand, some of
those projects did work out. For instance, my work on binary networks had a
significant role in getting my current job.  Another strategy that some
researchers use is to have one high-impact project going, and then to spend
some percentage of your time exploring other ideas. All that being said, how exactly
to choose when to stay focused and when to branch out is difficult and should
be handled on a case by case basis with the advice of someone more experienced
at your side.


# Make better decisions by predicting your mentor

One strategy to improve your decision making is to try to predict how your
mentor is going to react towards different ideas you might have for milestones.
If you want to become like your mentor one day, you can't just do what they tell
you to do. You need to understand how they make decisions so that you can help
direct future versions of yourself.
In particular, take careful note if your mentor has a different opinion
on the next direction to take your work.
There is a high chance that they have access to additional knowledge or a
previous experience that informs their thinking.
Even if you don't ultimately make the same decisions as your
mentor,
digging deeper into their justification why you should or shouldn't work on
a particular milestone will be beneficial to you.



# Final Thoughts

In this article, we discussed how to choose better intermediate goals.  But
having impactful and achievable milestones isn't the whole story.
If you want to learn more about day to day habits and techniques to
deliver on your milestones, connect with me on [LinkedIn] to see my future blog
posts. If you want to get personalized advice on how to choose milestones to
push your career forward, check out my [coaching] page.

[linkedin]: https://www.linkedin.com/in/alexanderganderson/
[coaching]: /coaching
