##  Examples of calculating q() in the MH-MCMC Hastings Ratio

In this file I will walk you through a few examples of how to calculate the proposal 
(transition) kernel term $q(\theta \rightarrow \theta')$ term in the Hasting's Ratio calculation 
of Metropolis-Hastings MCMC.

First of all, a reminder of the Hasting's Ratio itself. It is defined as:

$$  h = min \left\{ 1, \frac{f(\theta')q(\theta' \rightarrow \theta)}{f(\theta)q(\theta \rightarrow \theta')} 
\right\}  $$


Our context is often Bayesian, in which case $f$ is the posterior distribution $f(\theta \mid D) \propto f(D \mid \theta)\pi(\theta)$, 
for some dataset $D$ and model parameter(s) $\theta$, and then the Hastings' Ratio looks like this:

$$  h = min \left\{ 1, \frac{f(D \mid \theta')\pi(\theta')q(\theta' \rightarrow \theta)}{f(D \mid \theta)\pi(\theta)q(\theta \rightarrow \theta')} 
\right\}  $$

where $\pi()$ is the prior for $\theta$.

The key thing to remember is that the $q(\theta \rightarrow \theta')$ term is just the probability (or probability density 
if $\theta$ is continuous) of **proposing** a move from $\theta$ to $\theta'$.

In the examples we will assume that, as is most often the case, $\theta$ is continuous rather than discrete. 
But discrete examples work in a similar way.

### Example 1

In this example, we suppose that we propose a new value $\theta'$ by taking the existing value $\theta$ and 
adding a mean zero normal random variable $Z \sim Normal(0,\sigma^2)$. Suppose $Z$ took the value $Z=z$, then we have
the following:
* $\theta'=\theta+z$.
* So $q(\theta \rightarrow \theta')=q(\theta \rightarrow \theta+z)=f_Z(z)$, where $f_Z$ is the density function of a $Normal(0,\sigma^2)$ rv.

To evaluate $q(\theta' \rightarrow \theta)$ we write $\theta=\theta'-z$, and so $q(\theta' \rightarrow \theta'-z)=f_Z(-z)$.

Because $Z~\sim Normal(0,\sigma^2)$ is symmetric around 0, we have that $q(\theta \rightarrow \theta')=q(\theta' \rightarrow \theta)$, 
and so those terms will cancel out in the Hastings Ratio. This is one of the major plusses of using a perturbation $Z$ 
that is symmetric around 0. (Those terms will cancel out for any such rv, regardless of its exact distribution.)

### Example 2

In this example, we suppose that we propose a new value $\theta'$ by taking the existing value $\theta$ and 
adding a normal random variable with non-zero mean. So $Z \sim Normal(c,\sigma^2)$. Suppose $Z$ took the value $Z=z$, 
then we have the following:

* $\theta'=\theta+z$.
* So $q(\theta \rightarrow \theta')=q(\theta \rightarrow \theta+z)=f_Z(z)$, where $f_Z$ is the density function of a $Normal(c,\sigma^2)$ rv.

To evaluate $q(\theta' \rightarrow \theta)$ we write $\theta=\theta'-z$, and so $q(\theta' \rightarrow \theta'-z)=f_Z(-z)$.

But now $q(\theta \rightarrow \theta') \ne q(\theta' \rightarrow \theta)$ because $f_Z(z) \ne f_Z(-z)$ when $f_Z()$ is not centered at 0.

### Example 3

So now let's think about an independence sampler, in which rather than proposing $\theta'$ as a perturbation of the existing $\theta$, as in the above examples, we instead propose $\theta'$ as a sample from, for example, an exponential random variable. (So the proposed new value is indpendent of the existing value, contrary to Examples 1 and 2. It doesn't have to be exponential, we could use any distribution here, so long as we use the same dist. each iteration)

So now $q(\theta \rightarrow \theta')=expo(\theta')$, the prob. density of proposing the new value $\theta'$.

And $q(\theta' \rightarrow \theta)=expo(\theta)$, the prob. density of proposing the value $\theta$.

Typically, now, there is no cross-cancelation in the Hastings Ratio, unless we choose $f()$ to be the same density as the prior $\pi()$.



### Note on Latex

Note that this document was written to exploit an installed package called TeXify. It provides a way of writing math using LaTeX on Github. If you install that package it looks for files with a .tex.md extension. Whenever it finds one, it compiles any LaTeX code in that file and creates a rendered version with a .md extension. That's how this README.md file wass created. 
