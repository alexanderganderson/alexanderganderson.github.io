---
layout: post
title: 3 Ways to Maximize your Impact as a Machine Learning Engineer
date: 2020-11-23
categories: engineering
---

Congratulations!  You have a job as a machine learning engineer. Maybe you just
got out of school or you recently made a career switch. Or maybe you are
interested in getting into the field and want to know what it takes to excel.
Machine learning has been generating a lot of hype lately due to impressive
research results and some valuable industry applications.  However, machine
learning is more than fancy algorithms and innovative insights.  The
fundamentals of business still apply.  Consider the following points to take
your machine learning career to the next level:


# Do work that is essential to the success of your business

In industry, you are in a better position if you focus on doing work that is
critical for your company. This holds true in machine learning as well.  One
possible reason that this is a common problem is that many ML engineers come
from academia where the goals are fundamentally different than in industry.
Another possible reason is that there was a large hype cycle where many
businesses started ML groups without a clear business objectives.  You have to
think about your given situation and how you can best provide value to the
customers of your business. This is true regardless of whether you are more on
the research or product side.

Suppose that you work at a large company that has a pure research division.
While it is possible to continue doing academic research, the levels of
excitement are waning and hiring is slowing.  While this is an intrinsically
risky place to work, there is still research that you can do to be aligned with
the business. It comes down to understanding why that research organization
exists in the first place. For instance, if the company relies on customers
having confidence in and a positive view of AI, you can do research into
interpretability of ML algorithms or ML areas that are compelling to the
average person (e.g. medical or artistic). Finally, even within a pure research
division, it may be possible to work with product teams.

If your role is more on the product side or you have the opportunity to do
product-relevant work, you should consider building something that will be
highly impactful to an existing product. In the case of a startup or
startup-like effort effort in a larger company, consider doing the work
essential to having a product in the first place.
It can be fun to try new or complicated methods, but if the product fails to
get traction, or if the method doesn't solve a problem for the user, your
efforts won't translate into long-term career growth.
Another way to be successful in a product-focused role is to provide
information so that other people in your organization can make better
decisions.  For instance, managers are going to be wondering how viable your
work is in general and whether to allocate more resources to your project
relative to other priorities. The more clear you can be about the impact your
project has to the rest of the organization, the better.


# Create design documents

Once you've decided on an important problem, you want to create a solution that
is as performant and robust as possible. I recommend making a document that
outlines the different possible solutions.  Here, you can consider the
different potential solutions to your problem in terms of the cost to implement
them, their likelihood of being successful, and their robustness down the line.

The time spent implementing a machine learning method is a tiny fraction of the
overall time it will cost the organization.  The life cycle of a ML product
often includes studying the robustness of the predictions, deploying the
solution, monitoring and maintaining it, handing the code off to future
engineers, debugging unexpected interactions with other systems, and so on.
Therefore, it is important to try and keep things as simple as possible both
because you'll be able to see if it works faster and it will be more robust
moving forward.  A common mistake is to attack a problem with a fancy ML method
that is hard to maintain and interpret.

In addition to helping you structure your thoughts, an additional benefit of
this approach is that you can get specific feedback from others on your design.
It helps you focus the collective knowledge of your coworkers on the problem at
hand.  For instance, a huge amount of time can be saved if a coworker points
out that there is a problem with your approach before you start to implement
your solution.


# Develop comprehensive methods to evaluate your results

One of the key drivers in developing any system is the design of easy to run,
high-quality methods of evaluation. The key to the design of metrics is that
they need to inform the your decisions and the decisions of your organization.
On a macro level, overall performance is going to drive further investment into
the project, and robustness is going to result in the long-term usage of your
work.

Of course, you'll start with some aggregate measure of performance (e.g.
click-through rate, classification accuracy) to show the promise of your work.
However, more granular metrics are likely to build confidence in your efforts
and drive additional improvements to the system. One simple method to get more
fine-grained results is to report performance across different segments of your
product's user base (e.g. users in different geographical region, categories
for classification). This will both build confidence in your solution and help
your organization focus their attention on areas which need improvement.

Another useful approach is to try and classify your algorithm inputs in
terms of difficulty. For instance, in fraud detection, some examples might be
obvious instances of fraud that can be automatically handled, but others might
be ambiguous and require human review.  This type of separation can identify
areas that need more attention from you or others in the company.

A final issue to consider is that if you are doing machine learning which
ultimately impact humans, it is important to manually view the results
regularly.  Even the best metrics are going to miss situations that will be
obvious wrong (or even upsetting) to humans.  Likewise, in a real deployment
situation,  it is important to have metrics that ensure that the system isn't
totally broken. If the metric leaves a predefined range, an immediate response
can be triggered.

Stepping back a bit, a metric is only useful if it is actually used.  To that
end, the metric must be easy to evaluate and track over time.  Furthermore,
there needs to be buy-in from the various stakeholders in the project that the
metrics are important in the first place.


# Conclusion

As I come from an academic background, learning about how to work well within a
business team has been my largest area of growth in the past few years. It has
been, and continues to be, a fun process to figure out how to make better
decisions in a business context.  If you liked this article and want to see
more in the future, connect with me on [LinkedIn]. If you want to get
personalized feedback on how to take your career to the next level, check out
my [coaching] page.

[linkedin]: https://www.linkedin.com/in/alexanderganderson/
[coaching]: /coaching
