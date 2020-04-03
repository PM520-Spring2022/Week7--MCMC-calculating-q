##  Examples of calculating Q() in the MH-MCMC HAstings Ratio

In this file I will walk you through a few examples of how to calculate the proposal 
(transition) kernel term <img src="/tex/8e195e1865fe4a5007982ccd72eee6ec.svg?invert_in_darkmode&sanitize=true" align=middle width=67.24305059999999pt height=24.7161288pt/> term in the Hasting's Ratio calculation 
of Metropolis-Hastings MCMC.

First of all, a reminder of the Hasting's Ratio itself. It is defined as:

<p align="center"><img src="/tex/4fdf95a16d2d8c091386b81c439177ae.svg?invert_in_darkmode&sanitize=true" align=middle width=206.23885425pt height=39.452455349999994pt/></p>


Our context is often Bayesian, in which case <img src="/tex/190083ef7a1625fbc75f243cffb9c96d.svg?invert_in_darkmode&sanitize=true" align=middle width=9.81741584999999pt height=22.831056599999986pt/> is the posterior distribution <img src="/tex/f0774b86c352937adf9ce71d16a3fe70.svg?invert_in_darkmode&sanitize=true" align=middle width=58.54102649999999pt height=24.65753399999998pt/>, 
for some dataset <img src="/tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.06623184999999pt height=22.465723500000017pt/> and model parameter(s) <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/>, and then the Hastings' Ratio looks like this:

<p align="center"><img src="/tex/ef281fd76fa3303d1d03bfd490d29eb7.svg?invert_in_darkmode&sanitize=true" align=middle width=239.9889294pt height=39.452455349999994pt/></p>

where <img src="/tex/43c162e821c87ec6b7eec394a26d7c3a.svg?invert_in_darkmode&sanitize=true" align=middle width=22.74552059999999pt height=24.65753399999998pt/> is the prior for <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/>.

The key thing to remember is that the <img src="/tex/8e195e1865fe4a5007982ccd72eee6ec.svg?invert_in_darkmode&sanitize=true" align=middle width=67.24305059999999pt height=24.7161288pt/> term is just the probability (or probability density 
if <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/> is continuous) of **proposing** a move from <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/> to <img src="/tex/a0636197f9b37d9928c1c149816cd7dc.svg?invert_in_darkmode&sanitize=true" align=middle width=11.96348834999999pt height=24.7161288pt/>.

In the examples we will assume that, as is most often the case, <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/> is continuous rather than discrete. 
But discrete examples work in a similar way.

### Example 1

In this example, we suppose that we propose a new value <img src="/tex/a0636197f9b37d9928c1c149816cd7dc.svg?invert_in_darkmode&sanitize=true" align=middle width=11.96348834999999pt height=24.7161288pt/> by taking the existing value <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/> and 
adding a mean zero normal random variable <img src="/tex/c391001ca31b3fde947ba9abd4109bd6.svg?invert_in_darkmode&sanitize=true" align=middle width=139.17434025pt height=26.76175259999998pt/>. Suppose <img src="/tex/5b51bd2e6f329245d425b8002d7cf942.svg?invert_in_darkmode&sanitize=true" align=middle width=12.397274999999992pt height=22.465723500000017pt/> took the value <img src="/tex/353888786ef372f75f3370e6a64b2368.svg?invert_in_darkmode&sanitize=true" align=middle width=42.682521749999985pt height=22.465723500000017pt/>, then we have
the following:
* <img src="/tex/7131b79880fe71065a84aef82f306c3f.svg?invert_in_darkmode&sanitize=true" align=middle width=71.33537234999999pt height=24.7161288pt/>.
* So <img src="/tex/8f29e856418a16aa01e1fdedc9d7a411.svg?invert_in_darkmode&sanitize=true" align=middle width=241.95381044999996pt height=24.7161288pt/>, where <img src="/tex/b89e5521fa987718839126c48f68f4b8.svg?invert_in_darkmode&sanitize=true" align=middle width=17.810563649999988pt height=22.831056599999986pt/> is the density function of a <img src="/tex/e5d47276651d497557d57fd0361322bd.svg?invert_in_darkmode&sanitize=true" align=middle width=104.85944204999998pt height=26.76175259999998pt/> rv.

To evaluate <img src="/tex/04efca0a1314e6cb94a0c00ce831ab39.svg?invert_in_darkmode&sanitize=true" align=middle width=67.24305059999999pt height=24.7161288pt/> we write <img src="/tex/9cd443bcae4fe715be6503ee1cfb82be.svg?invert_in_darkmode&sanitize=true" align=middle width=71.33537234999999pt height=24.7161288pt/>, and so <img src="/tex/0e7d7500edd7e9d8c5158ffa6744e369.svg?invert_in_darkmode&sanitize=true" align=middle width=170.190438pt height=24.7161288pt/>.

Because <img src="/tex/934de97542301722bf3747775d62ed2e.svg?invert_in_darkmode&sanitize=true" align=middle width=144.653784pt height=26.76175259999998pt/> is symmetric around 0, we have that <img src="/tex/19091f2315c9e70e69bcdf56a884d7cc.svg?invert_in_darkmode&sanitize=true" align=middle width=156.403731pt height=24.7161288pt/>, 
and so those terms will cancel out in the Hastings Ratio. This is one of the major plusses of using a perturbation <img src="/tex/5b51bd2e6f329245d425b8002d7cf942.svg?invert_in_darkmode&sanitize=true" align=middle width=12.397274999999992pt height=22.465723500000017pt/> 
that is symmetric around 0. (Those terms will cancel out for any such rv, regardless of its exact distribution.)

### Example 2

In this example, we suppose that we propose a new value <img src="/tex/a0636197f9b37d9928c1c149816cd7dc.svg?invert_in_darkmode&sanitize=true" align=middle width=11.96348834999999pt height=24.7161288pt/> by taking the existing value <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/> and 
adding a normal random variable with non-=zero mean. So <img src="/tex/8d93d701772fe48c003bb94ba41e3f55.svg?invert_in_darkmode&sanitize=true" align=middle width=142.96652369999998pt height=26.76175259999998pt/>. Suppose <img src="/tex/5b51bd2e6f329245d425b8002d7cf942.svg?invert_in_darkmode&sanitize=true" align=middle width=12.397274999999992pt height=22.465723500000017pt/> took the value <img src="/tex/353888786ef372f75f3370e6a64b2368.svg?invert_in_darkmode&sanitize=true" align=middle width=42.682521749999985pt height=22.465723500000017pt/>, 
then we have the following:


