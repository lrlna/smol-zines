## Cellular Automata

I've given a bunch of talks last year about the concept of cellular automata,
but I realize I am yet to write about it. This guide is a mixture of the
sketches you might expect in this repo and some explanations of the concept.

Cellular automata are essentially decentralized spatially extended systems 
consisting of large numbers of simple identical components with local
connectivity.[source](http://web.cecs.pdx.edu/~mm/ca-review.pdf)

Sounds quite a bit confusing, so let's debunk this in the context of one
dimensional automata, which are the best ones to talk about when trying
to build a simplified model of a complex system. The
[initial idea](http://www.stephenwolfram.com/publications/academic/computation-theory-cellular-automata.pdf)
of one dimensional way of looking at this came about from Stephen Wolfram, 
who's constructed different automata based on 256 different rules. But
what are rules even?

Okay, so going back to `decentralized spatially extended systems` statement,
we can start by working backwards. We know are are working with simple
components, which, to be simple, will be binary. So an single automaton 
can take shape in two states:

![binary](/guides/img/automata/binary-states.jpg)

We then know these simple components are somehow connected. In the 'space'
of automata, that generally means a single automaton is dependant on its
neighbours and 'makes decisions' based on those neighbours. Your neighbourhood
looks something like this:

![your-hood](/guides/img/automata/your-hood.jpg)

One dimensional automata are `spatially extended`, which suggests a change over
a period of time. This change is based on the rules that these automata follow.
Because they are **identical**, each automata will follow its rules in an identical
fashion. The rules are constructed around types of neighbourhoods. And because
we are only dealing with binary, there can only be eight types of neighbourhoods.
Something like this:

![all-hoods](/guides/img/automata/all-hoods.jpg)

So essentially you, as an automaton, would match yourself and your two neighbours
to a particular predefined neighbourhood. The rule-of-update you follow will be
based on one of the 256 rules defined by Wolfram. Those are defined based on an
8-bit representation of 1-256 (our rules!!) and are then matched up to a particular
neighbourhood. Here is how rule 110 would look like:

![rule-110](/guides/img/automata/rule-110.jpg)

Because automata are spatially extended, a single year in the life is just a
lattice of cells.

![lattice](/guides/img/automata/lattice.jpg)

This lattice then gets updated based on the rules year over a year, so you end
up with an entire lifetime of automata.

![multiple-lattice](/guides/img/automata/multiple-lattice.jpg)

The diversity of these lifetimes based on the rules they follow is the
fascinating bit, and that's what has been making me excited about the entire
concept. Here is an example of what you get:

![automata.gif](/guides/img/automata/automata.gif)

P.S. you can play around with the rules yourself [here](http://lrlna.github.io/cellular-automata/)

P.S.S. I built a library for automata, called [olivaw](https://github.com/lrlna/olivaw), you should check it out ✨

