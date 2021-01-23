---
layout: post
title: Why can 2 times 3 sometimes equal 7 with Android's Neural Network API?

date: 2021-01-23
categories: engineering
---

{:refdef: style="text-align: center;"}
![two_times_three](/static/img/indeterminism.png)
{: refdef}



Two times three equals six or at least that's what I naively expected.


It is well-known that floating point matrix multiplication can result in a variety of [surprises].
But did you know that quantized neural networks are not deterministic as well?
A quantized neural network uses integers to
multiply weights and activations in a neural network.
Thus, the naive logic goes, two and three represented and multiplied as integers should always give the exact same result,
namely six.

However, according to the [Android NNAPI Driver Validation] documentation, a
driver is valid if multiplication of quantized tensors is within plus or minus
one bit.

# What's going on and how did we get here?

The non-determinism of quantized multiplication is a result of optimizing for
the most common neural network deployment use cases.  Neural networks used for
classification and detection generally work well with small amounts of
non-determinism due to the nature of the mathematical operations involved in
[neural networks]. Furthermore, such networks often benefit from training with
some noise (e.g. batch normalization). Likewise, the input to many neural
networks comes from a camera that generates inherently variable images.

The main challenge associated with neural network deployment on the phone
is creating models that are sufficiently fast, power friendly, and small on
disk. Quantizing a neural network helps one improve in all of these categories.
Quantized weights take up less space on disk, take less energy to transfer, and
can be moved more quickly between different levels of memory.

The last issue at play is that it is much cheaper (both in terms of computing
cost and engineering effort) to quantize a pre-trained model than to train an
existing model from scratch. Consequently, the method developed in this
[Integer Inference] paper
targets quantizing existing models. The key idea is that a floating point
value can be approximated as a scale times a quantized value minus a zero
point. (Also take a look at the [Tensorflow Quantization Spec]).
The scale and zero point can be chosen relatively easily by, for
instance, looking at the
range of the weights and activations when evaluating the model on a number of
representative inputs.

The loss in predictive performance due to quantization in many practical use cases is
small and this abstraction is widely implemented and baked into hardware,
for instance, by Qualcomm' [Snapdragon Neural Processing Engine SDK].
[Strictly speaking, the drivers for this hardware could be
changed to ensure determinism, but that may result in a significant loss in
speed at inference time.]
The SNPE was developed and subsequently, Android sought to simplify the process
of deploying neural networks given the wide variety of available
accelerators. The restrictions on the driver tests were relaxed after pushback from
chip manufacturers whose hardware and drivers did not produce deterministic
quantized math.

Unfortunately, the NN API off by at most 1 (or 3 for a larger network) leaves a
lot of room for funny business that can change the results by small amounts.
The hardware and driver vendors want to produce fast times and low energy
usage numbers on
various neural network benchmarks and are less concerned about reproducibility.
This can lead to unexpected changes in neural network outputs.
For instance, the zero point or scale of the
weights might be changed for some reason by the hardware, and the quantized
values are then recomputed. Another thing that can happen is that the range might
be slightly shifted to make zero exactly representable (see Case 3: Inputs are
both negative and positive in the [Snapdragon Neural Processing Engine SDK]).
Likewise, as the off by one error bound is on a per layer basis, larger
networks generate accumulating error. Practically speaking, the error bound is
increased to three for mobilenet in the NN API driver validation tests. Other
networks could produce larger errors.


# Cross Platform Reproducibility and Optimization

The lack of determinism for quantized neural networks touches on the broader
issue of cross platform reproducibility and performance optimization for neural networks.
As the neural networks get deployed more and more widely, these issues will grow in importance.

The first major issue is that if you want to deploy a neural network across
many platforms, you don't have any guarantees that you are going to get the
same results.
Even if you manage to assemble a large team to test your networks on many
different platforms, the problem isn't solved.
*The lack of determinism means that even if you test your network
on every platform, a driver update may unexpectedly change your results*.
This creates an ongoing engineering cost beyond the initial fixed cost of
validating the deployment on existing hardware.

The next major issue is that some application areas have more stringent
standards in terms of reproducibility and auditability. Suppose that a neural
network is used in a self-driving car that gets in an accident. For auditing
purposes, it is important to be able to replay the decisions made by the car's
control system exactly. In the best case, this requires a significant
engineering effort to keep track of all of the driver versions and internal
testing to verify reproducibility for any deployment.

The final issue is that while classification and detection are not particularly
sensitive to small changes in output, the lack of determinism makes it more
challenging to deploy neural network models which are deeper or more sensitive to
changes.  For instance, imagine a language model that is unrolled over many
iterations to parse or generate a sentence. In that case, accumulating errors
could cause unexpected results.

# Final Thoughts

In the past couple years, there has been an explosion of experimentation in
neural network deployment from software frameworks to hardware
accelerators.  As the field matures, questions about best practices will slowly
be answered. The ability to *train once, deploy anywhere* will become easier
and easier. In the particular case of determinism, the most reasonable next
step is to have a driver test that ensures determinism and publish a list of
vendors that implement a deterministic API.

The question of determinism is only one small part of the puzzle of being able
to deploy anywhere. Another subtle but important issue is that different
operations will run faster on different hardware. Even if a network can deploy
anywhere in a reproducible manner, an even more fundamental issue is whether
or not a network will be fast and power efficient on any platform. Indeed, while there
has been a great amount of progress in the field of neural network
deployment, there is much to be done to make the ecosystem easier to use and
more mature.

If you are interested in learning more about issues surrounding neural network
deployment or how to be a better machine learning engineer,
connect with me on [LinkedIn] to see my future [blog] posts!  If you think that I
can help you grow professionally, check out my [coaching] page.

[linkedin]: https://www.linkedin.com/in/alexanderganderson/
[coaching]: /coaching

[surprises]: https://developer.download.nvidia.com/video/gputechconf/gtc/2019/presentation/s9911-determinism-in-deep-learning.pdf
[Tensorflow Quantization Spec]: https://www.tensorflow.org/lite/performance/quantization_spec
[Android NNAPI Driver Validation]: https://source.android.com/devices/neural-networks#validation
[Snapdragon Neural Processing Engine SDK]: https://developer.qualcomm.com/docs/snpe/quantized_models.html
[Integer Inference]: https://arxiv.org/abs/1712.05877
[blog]: /blog
[neural networks]: https://openreview.net/forum?id=B1IDRdeCW
<!-- [zero exactly representable] -->
