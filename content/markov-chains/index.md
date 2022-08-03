+++
title = "Markov Chains"
description = "Markov chains, what are they, uses and examples."
date = 2022-08-03
[taxonomies]
categories = ["machine learning", "natural language processing"]
tags = ["markov", "markov chains", "nlp", "HMM"]
[extra]
keywords = "markov, markov chains, HMM, nlp, ml, pytorch, tensorflow"
+++

### Markov Chains

Markov chain is a mathematical system and also a stochastic process, but differs as the general stochastic process have memory of previous steps while markov chains are made to not have any form of memory. This is easily visualized by the following:

- A general stochastic process is a bag of balls (with various) where you take out 1 ball each time ***without*** replacement
- Markov Chains ***with*** replacement 
  - This allows markov chains to not depend on the previous change as if it were not replaced the chance of another ball of the same color the probabilty of balls of different colors will change.

