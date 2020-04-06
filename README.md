##  Examples of calculating Q() in the MH-MCMC Hastings Ratio

In this file I will walk you through a few examples of how to calculate the proposal 
(transition) kernel term <img src="/tex/8e195e1865fe4a5007982ccd72eee6ec.svg?invert_in_darkmode&sanitize=true" align=middle width=67.24305059999999pt height=24.7161288pt/> term in the Hasting's Ratio calculation 
of Metropolis-Hastings MCMC.

First of all, a reminder of the Hasting's Ratio itself. It is defined as:

<p align="center"><img src="/tex/d2e92a75a91fca2682fc3b9a3114cc7f.svg?invert_in_darkmode&sanitize=true" align=middle width=210.85072799999998pt height=39.452455349999994pt/></p>


Our context is often Bayesian, in which case <img src="/tex/190083ef7a1625fbc75f243cffb9c96d.svg?invert_in_darkmode&sanitize=true" align=middle width=9.81741584999999pt height=22.831056599999986pt/> is the posterior distribution <img src="/tex/781942ca7fefedc3cd988bcdb885513d.svg?invert_in_darkmode&sanitize=true" align=middle width=169.91873085pt height=24.65753399999998pt/>, 
for some dataset <img src="/tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.06623184999999pt height=22.465723500000017pt/> and model parameter(s) <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/>, and then the Hastings' Ratio looks like this:

<p align="center"><img src="/tex/109802111693b1825a22dc86233f43fc.svg?invert_in_darkmode&sanitize=true" align=middle width=274.1462757pt height=39.452455349999994pt/></p>

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

To evaluate <img src="/tex/04efca0a1314e6cb94a0c00ce831ab39.svg?invert_in_darkmode&sanitize=true" align=middle width=67.24305059999999pt height=24.7161288pt/> we write <img src="/tex/9cd443bcae4fe715be6503ee1cfb82be.svg?invert_in_darkmode&sanitize=true" align=middle width=71.33537234999999pt height=24.7161288pt/>, and so <img src="/tex/7fb4d2a3fb96dd72a84b2326def7678e.svg?invert_in_darkmode&sanitize=true" align=middle width=174.80231339999997pt height=24.7161288pt/>.

Because <img src="/tex/934de97542301722bf3747775d62ed2e.svg?invert_in_darkmode&sanitize=true" align=middle width=144.653784pt height=26.76175259999998pt/> is symmetric around 0, we have that <img src="/tex/19091f2315c9e70e69bcdf56a884d7cc.svg?invert_in_darkmode&sanitize=true" align=middle width=156.403731pt height=24.7161288pt/>, 
and so those terms will cancel out in the Hastings Ratio. This is one of the major plusses of using a perturbation <img src="/tex/5b51bd2e6f329245d425b8002d7cf942.svg?invert_in_darkmode&sanitize=true" align=middle width=12.397274999999992pt height=22.465723500000017pt/> 
that is symmetric around 0. (Those terms will cancel out for any such rv, regardless of its exact distribution.)

### Example 2

In this example, we suppose that we propose a new value <img src="/tex/a0636197f9b37d9928c1c149816cd7dc.svg?invert_in_darkmode&sanitize=true" align=middle width=11.96348834999999pt height=24.7161288pt/> by taking the existing value <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/> and 
adding a normal random variable with non-=zero mean. So <img src="/tex/95b03635a16ea4f41ed7bdfa1054f8ff.svg?invert_in_darkmode&sanitize=true" align=middle width=138.06893594999997pt height=26.76175259999998pt/>. Suppose <img src="/tex/5b51bd2e6f329245d425b8002d7cf942.svg?invert_in_darkmode&sanitize=true" align=middle width=12.397274999999992pt height=22.465723500000017pt/> took the value <img src="/tex/353888786ef372f75f3370e6a64b2368.svg?invert_in_darkmode&sanitize=true" align=middle width=42.682521749999985pt height=22.465723500000017pt/>, 
then we have the following:

* <img src="/tex/7131b79880fe71065a84aef82f306c3f.svg?invert_in_darkmode&sanitize=true" align=middle width=71.33537234999999pt height=24.7161288pt/>.
* So <img src="/tex/8f29e856418a16aa01e1fdedc9d7a411.svg?invert_in_darkmode&sanitize=true" align=middle width=241.95381044999996pt height=24.7161288pt/>, where <img src="/tex/b89e5521fa987718839126c48f68f4b8.svg?invert_in_darkmode&sanitize=true" align=middle width=17.810563649999988pt height=22.831056599999986pt/> is the density function of a <img src="/tex/b1eedd1da817a307f8bac51da16026dd.svg?invert_in_darkmode&sanitize=true" align=middle width=103.75403609999998pt height=26.76175259999998pt/> rv.

To evaluate <img src="/tex/04efca0a1314e6cb94a0c00ce831ab39.svg?invert_in_darkmode&sanitize=true" align=middle width=67.24305059999999pt height=24.7161288pt/> we write <img src="/tex/9cd443bcae4fe715be6503ee1cfb82be.svg?invert_in_darkmode&sanitize=true" align=middle width=71.33537234999999pt height=24.7161288pt/>, and so <img src="/tex/7fb4d2a3fb96dd72a84b2326def7678e.svg?invert_in_darkmode&sanitize=true" align=middle width=174.80231339999997pt height=24.7161288pt/>.

But now <img src="/tex/3da7638af3d1bc9960133de1cf0d478a.svg?invert_in_darkmode&sanitize=true" align=middle width=156.403731pt height=24.7161288pt/> because <img src="/tex/c2560a57f0f6ff735dc084abdb249a3e.svg?invert_in_darkmode&sanitize=true" align=middle width=114.27409125pt height=24.65753399999998pt/> when <img src="/tex/f050a9b21715c852da6ac528efe4bd6d.svg?invert_in_darkmode&sanitize=true" align=middle width=31.417894199999992pt height=24.65753399999998pt/> is not centered at 0.

### Example 3

So now let's think about an independence sampler, in which rather than proposing <img src="/tex/a0636197f9b37d9928c1c149816cd7dc.svg?invert_in_darkmode&sanitize=true" align=middle width=11.96348834999999pt height=24.7161288pt/> as a perturbation of the existing <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/>, as in the above examples, we instead propose <img src="/tex/a0636197f9b37d9928c1c149816cd7dc.svg?invert_in_darkmode&sanitize=true" align=middle width=11.96348834999999pt height=24.7161288pt/> as a sample from an exponential random variable. (So the proposed new value is indpendent of the existing value, contrary to Examples 1 and 2. It doesn't have to be exponential, we could use any distribution here.)

So now <img src="/tex/ee57210172833d23e1f90ef442b02096.svg?invert_in_darkmode&sanitize=true" align=middle width=148.0192593pt height=24.7161288pt/>, the prob. density of proposing the new value <img src="/tex/a0636197f9b37d9928c1c149816cd7dc.svg?invert_in_darkmode&sanitize=true" align=middle width=11.96348834999999pt height=24.7161288pt/>.

And <img src="/tex/b9128b16b27a786bf1627827a6fc20cc.svg?invert_in_darkmode&sanitize=true" align=middle width=143.40738555pt height=24.7161288pt/>, the prob. density of proposing the value <img src="/tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.17352744999999pt height=22.831056599999986pt/>.

Typically, now, there is no cross-cancelation in the Hastings Ratio, unless we choose <img src="/tex/5f954f0890e759b145da7cc998a0b4a0.svg?invert_in_darkmode&sanitize=true" align=middle width=22.602846749999987pt height=24.65753399999998pt/> to be the same density as the prior <img src="/tex/43c162e821c87ec6b7eec394a26d7c3a.svg?invert_in_darkmode&sanitize=true" align=middle width=22.74552059999999pt height=24.65753399999998pt/>.



### Note on Latex

Note that this document was written to exploit an installed package called TeXify. It provides a way of writing math usoing LaTeX on Github. If you install that package it looks for files with a .tex.md extension. Whenever it finds one, it compiles any LaTeX code in that file and creates a rendered version with a .md extension. That's how this README.md file wass created. 
