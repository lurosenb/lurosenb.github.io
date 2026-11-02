---
layout: post
date: 2026-11-02 12:00:00-0400
inline: true
---

New pre-print that I'm quite excited about: [Differentially Private Synthetic Data from Sliced Chebyshev Moments](https://arxiv.org/pdf/2610.42081) with [Teal Witter](https://www.rtealwitter.com/) and [Chris Musco](https://www.chrismusco.com/). Many practical DP synthetic data methods only preserve low-dimensional marginals, and so can only capture global structure by (essentially) luck. Our algorithm, SPLICE, gets around this by matching noisy *sliced* Chebyshev moments. We actually prove a Sliced Wasserstein-1 guarantee that is **independent of the data dimension**, and  we show that SPLICE is state-of-the-art on some measures in an extensive benchmark. This paper ties together a few different threads from the past few years, please reach out with questions / comments!
