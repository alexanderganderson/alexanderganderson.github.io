---
layout: post
title: Streamline your Deep Learning Optimization Process
date: 2021-01-09
categories: engineering
---

{:refdef: style="text-align: center;"}
![Relationship between Long-Term Goals and Milestones](/static/img/ml_cycle.png)
{: refdef}

Pushing the state of the art in deep learning is inherently difficult.
Many problems have been well-studied, and other researchers are working quickly to
explore new ideas.
Regardless, you can get an edge by being systematic in how you approach your
research.
In previous posts, I discussed how to [develop long-term goals](/engineering/2020/11/25/long_term_goals.html)
and [choose intermediate milestones](/engineering/2020/12/02/setting_milestones.html).
In this post, we will discuss how to get great deep learning results by
optimizing the process that you use generate and evaluate ideas on a day to day
basis.

Given the inherent difficulty of deep learning model optimization, the most important goals
are to
to:
1. Improve the speed that you can implement and evaluate new ideas (move
   through the loop quickly)
2. Improve your ability to predict the complexity and effectiveness of
potential improvements (get as much expected gain as possible from each loop
iteration)

<!-- Thus, in order to make progress, you need to move as quickly as -->
<!-- possible through the cycle of prioritizing solutions, implementing them, -->
<!-- training models, studying evaluation results, and repeating. -->

If you are doing work that is pushing the state of the art, any one idea that
you try is unlikely to work. In my experience, for every ten ideas that I
implement, I only get one or two positive results.

# Collecting Ideas for Improving your Model
Before you start implementing anything, create a list of ideas that can
improve your results. In addition to considering a standard set of techniques
(listed below), it is critical to thoroughly study existing work related to
your area. It is much faster to replicate existing work than to reinvent the
wheel.

Here is a list of ideas to try for deep learning models:
- Implement non-deep learning baselines to make sure that deep learning is
  necessary in the first place
- Try different optimizers, hyper-parameters (e.g. learning rate, loss weights), and parameter initializations
- Build out more detailed evaluation methods
- Collect additional data for underperforming categories of inputs
- Implement layers that encode domain specific knowledge
- Increase the model size or use different neural network backbones
- Simplify the task for the network through curriculum learning, additional supervision signals, or better data labeling

# Prioritizing Solutions

Once you have a list of ideas, how should you decide what to do next?  You want
to estimate the following criteria for each idea:
- Time to implement
- Complexity added to the code base
- Potential Impact
- Likelihood of success

At this stage, it is helpful to get feedback from your mentors and colleagues.
Are there any ideas that you missed? Are your estimates of complexity and
impact reasonable? The better you are at predicting how well a method will
work, the faster you will generate good results!  Once you have collected this
information, I highly recommend doing the simplest/fastest things first.
The best models often are the result of a large number of small and simple improvements.
Complex methods can slow down future progress and complicate the optimization
process in a way that makes other methods not work.

# Minimally Sufficient Testing
Now that you have chosen your idea, it is time to implement as systematically
as possible. In deep learning, standard software
engineering practices are necessary for getting good results but not
sufficient. Not only should the core piece of code be unit-tested, but the
code needs to actually generate an improvement when included in the full
optimization of your deep learning model.
Tests and experiments should be the fastest possible to catch different types
of issues.  The testing sequence for ideas in deep learning usually involves
the following:
- Run all possible quick, isolated tests of the individual layer to verify
  that it is properly implemented (i.e. unit tests)
- Train a minimal model (e.g. make the backbone small, remove regularizations,
  and simplify the data) with the feature in question to verify that
  optimization works properly
- Run a sequence of experiments where you progressively undo the various simplifications
that you made in the previous step.

# Infrastructure for completing the loop quickly
In order to optimize your speed, you want to move through the deep learning
optimization loop as fast as possible. An often overlooked step is to be slow
to automate as much of the evaluation process as possible.  Furthermore, the
better evaluations that you have, the better you will be at predicting which
ideas will work. Time spent writing good inspection and evaluation can be very
valuable! Likewise, running experiments in parallel will reduce the time that
you spend waiting for your experiments to train.

Typical evaluation infrastructure to consider:
- Histograms of various quantities with known ranges to check that
  the initial values and values over time remain within reasonable bounds.
- Train/test losses over time
- Evaluation of model on different slices of the data/different values of
  conditioning variables for a generative model.
- Some example results for visual inspect. In the case of image generation, you
  might look at some samples of your model. In the case of language
  translation, you might manually inspect some translated sentences.
- Servers or cloud infrastructure that allows you to run multiple experiments
  at once. For a more budget option, have your machine training at night as
  much as possible!

Given the information from your experiments and evaluations, you can either
exit the loop if you have reached sufficient performance or you can update your
list of ideas (and the associated predictions of risk, impact, etc).

# Final Thoughts

In this article, we discussed how to get strong deep learning model performance
by being more systematic about your day to day decisions.
Once you have gotten strong performance for your model, there is still a
significant amount of work to be done. There is a large gap between having good
results and communicating them in a way that others can understand and use.
If you want to learn more about how to deliver your results in a way that will
maximize their impact, connect with me on [LinkedIn] to see my future blog posts!
If you want to get personalized advice on how to optimize your day to day
decision making, check out my [coaching] page.

[linkedin]: https://www.linkedin.com/in/alexanderganderson/
[coaching]: /coaching
