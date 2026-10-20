# a tiny project

This project is an experiment in large-scale engineering with language model (LM) agents. 

It serves two purposes. 

- The first is as an experiment, testing the hypothesis that agents can be coerced
to write high-performance software. Coercion here roughly means _aligned, with some sort of structured context management_
through tools, including programming languages and systems.
- The second is as a source of high-performance programmable software, for usage more generally
  (beyond the purview of seeing _if agents can write this stuff_: we want it to be useful! To
  laypeople, to scientists, etc)

In any case, it should be abundantly clear ahead of time **that agents are being used to write this software**.
This project does not seek to hide that, *it is the entire point of the project*.

We dream of a world where users can quickly spin up customized high-performance software
for their open access computing devices, without having to reinvent the universe
(indeed, *this project* might serve as such a universe, or as source for your own universe).

If you find our work useful, you might cite the project from the citation key
at https://a-tiny-project.github.io/

## Comments on software and agents

Agents are now capable enough to allow anyone to rapidly spin up new software. This is awesome!
Software deserves to be democratized! Assume that anyone can write any piece of software, what
is the value of the software produced by a project such as this?

Answering this question is analogous, in many ways, to the existential crisis confronting mathematics.
In general, anyone can spin up a piece of software ... but not everyone can do it _well_.

(whether you want “well” depends drastically on what you’re doing, of course!)

At least for
today's agents, what you get out _remains_ a function of what you put in. Here, 
we (and presumably also you) want someone
who is motivated to carefully understand what they are doing at the helm ... a.k.a someone 
who is in it _for the love of the game_ (the game in this case is some combination of PL and systems, etc).

We love the game, and want to understand it!
We’re also interested in the idea that we might teach agents “the game” (can you teach agents good PL / systems design?)

### Agents are programmable search processes

Programming with agents involves programming a search process. 

Inside the large space of software that runs sits a region (our region of concern in this project), 
let's call it "good software": this is software aligned with very human concerns (performance, compositional design, programmability, scalability, and so on). 
If you don't care about this, that's fine, but we do (people care about a lot of weird things), so we're going to talk about it.

Our question is simple: how do we program the agent search process to find / prefer this space?
The very general idea (that nearly everyone who uses agents is pursuing) 
is to somehow apply pressure on the agents through as many signals as possible
to try and increase the probability of finding this space for their concerns.

These signals include: humans-in-the-loop, testing, verification, programming languages with
guarantees, skills, etc. These are all the techniques 
that we're pulling out to try and steer the agentic probability distribution.

When this pressure is applied successfully and the data is made available to them, 
labs can then amortize the successful traces 
back into the models, making them better at software (or whatever they can get their hands on),
reducing the need for the pressure -- in a sort of virtuous amortization cycle.

### Amortization gap

A question arises: if this process continues for long enough, will software be "solved"?

Our hypothesis is that no, software is not solved, and it seems like
where you fall on this question seems to align with whether or not you believe that 
our current trend of AI will lead to general purpose pre-trained systems 
that ultimately understand all of your concerns better
than you do (let's call this _the machine god hypothesis_).

A machine god might understand your desires and concerns, and can then construct good software (or whatever)
to answer them ... okay, aren't we already there? We'd say: there are _definitely_ desires and concerns for which
one can get nearly perfect software out of today's AI systems.

But here's the rub: if you're pushing the frontier, you start move off the "good software" distribution of today's agents,
and then you increasingly find yourself engineering the search process towards your concerns. 
This is an _amortization gap_: the pre-training process leads
to a search process for your concerns, but you find that you can improve it.

(pre-training here means _before usage_ -- it encompasses generative pretraining, SFT, RL, etc)

A big theoretical question here seems to be something like "is there an RL curriculum that leads to superhuman performance
in all possible concerns" or something like that. A related question: suppose that humans (and human organizations)
continue to find and engineer away these gaps -- can training processes for LLMs continue 
to compress all these improvements back into the model, for the rest of time?

Not sure, but it seems like the space of software is infinite, and as we use these tools
to more rapidly explore the space, it seems like a fundamental geometric observation that these
amortization gaps cannot be eliminated via any form of pre-training. The alternative seems like wishful thinking ...
that indeed -- there exists some training process that produces an artifact that "solves software"
seems like it might only be true
in an narrow economically interpreted definition of "software", which we're not really interested in
(after all, we're boundary pushers).

In other words, we're not sure that amortization gaps are ever going away ... and with that in mind,
it behooves us (as human designers and programmers) _to continue to find these gaps_, analogous
(of course) the pursuit of knowledge in the first place.

---

A human programmer searches in small steps. An agent (a language model working in a loop with tools) takes longer (and more frequent!) steps, which we call _leaps_. 
At any point in the search, the agent has many possible next steps, some more likely than others. 
We draw this _distribution of next steps_ as a jagged teal ball, and each leap as one draw from it.

<p align="center">
  <img src="figures/search.svg" alt="A human searches in small steps. A language model agent leaps into software that runs, outside good software. A human at the helm keeps its path smooth only for the leaps they can read" width="720" />
</p>

_On its own (center), the agent (teal) often ends in software that runs (dashed region), but (today!) perhaps not inside the ring of good software. 
A human (red) has a budget of six small steps, and reading one leap costs three. At the helm (right), the human reads the first two leaps. 
At each, the human accepts the draw that keeps the path's direction (red rings) over a longer one that turns away. Past the second leap, the path turns sharply and zigzags._

Frontier labs program part of the agent's search into the model's weights, through pretraining, fine-tuning, and reinforcement learning. They train toward software that runs and, 
using human preference data, toward what people generally want from software. Of course they want good software, and if there was an RL environment that could 
computably represent the preferences which induce this space, they'd use that too and we'd all be happy. Perhaps that will happen in 2026 and we can shut this project down,
and live in a utopia of good PL design.

... but in the meantime, all of this training happens before the model encounters _our project_ and _our concerns_, so it cannot account for them entirely from training. 
We program it after training through the _harness_ (the tools, tests, context, and languages around the model), which a human can read and change.

<p align="center">
  <img src="figures/shaping.svg" alt="Training at frontier labs stretches a language model agent's distribution of next steps into software that runs. A harness a human can read bends it toward good software" width="720" />
</p>

_Training moves the distribution's mass from a dense core (pretraining) out along progressively longer spikes (fine-tuning and reinforcement learning). The longest spikes end in software that runs, all to one side of good software. In the harness (right), types, tests, and benchmarks act as walls (shaded) that remove the steps they rule out, and a plan held by a human (faint red band) bends one spike toward good software._

### Agents programming themselves

The [Mismanaged Geniuses Hypothesis](https://alexzhang13.github.io/blog/2026/mgh/) proposes training models to decompose and manage their own work 
(essentially: can we design harnesses that get out of the way ... programmable in such a way that the 
agent can use the 
programmability to increase the set of tasks it can solve using decomposition). 
We strongly align with the intuitions
behind this hypothesis for harness design (and, of course, training agentic LMs within harnesses) 
inasmuch as _humans are kept in the loop_. This is counter to the dominant narratives in
agents, which, in extreme forms, seek to remove humans from the loop. 
We want humans (yes, often multiple, as part
of great organizations that do great work) in the loop. Agents can be right there as well, of course!

This rests on a simple premise:
_if you remove yourself from the loop, you can no longer verify that the thing is what you wanted_

There are degrees of verification, and the programming of the space of strategies for verification is,
of course, a great concern. But at the very least: we want humans in the ring, verifying, thinking, etc.!

To draw the contrast, there's this term "recursive self-improvement". This term seems to 
apply to _agentic LMs training agentic LMs_, but the term has also been commandeered a bit to refer to harness
programming strategies.

This term doesn't make much sense to us: we're concerned with humans: we ask whether a 
human can keep up with the loop, and steer it, as the loop scales ... because otherwise wtf are we doing? 

RSI (and the systems its proponents seem to propose that we consider) offers that we take the role
of observers on some inscrutable agentic execution trace into the future, 
whose goals we don't understand (the _acceleration_ is just too large for us to keep up).

In other words, we become passengers in an evolving world which we can no longer meaningfully
contribute to, deferring all questions and their answers to a magic box in the sky.
Okay, we ask, bluntly: who the fuck would want this?
Apparently, a religion is indeed a viable business strategy.

The most charitable interpretation of RSI as "only" leading to agents of increasingly
more degrees of _helpfulness_ seems to require a nearly complete solution to the question of alignment.

Alignment, of course,
has many levels -- but we're mostly concerned with "individual" alignment (tools and systems that
work well for the individual, furthering them towards their goals). 
Perfect individual alignment seems to be: a system
which is exactly aligned with my goals (which, by the way, I don't even know very well) but can
accomplish them at increasingly fast speeds. Of course, individual alignment with a sufficiently powerful
autonomous system is dangerous, and so labs are also concerned with "global" alignment and safeguards.

(RSI _as a scientific endeavor_ is perfectly acceptable, but we all know that RSI is not just a scientific 
endeavor ... but one motivated extremely by the philosophy of capital)

### The search for interaction models which scale well

Back to humans. How do we keep up? 

The answer depends entirely on the physical realities of being a human, and our cognitive capabilities. 
In other words, what makes us ... us. These are often framed as limitations. 
They are not limitations: we instead view these
as design constraints that lead to elegant and minimal solutions.
Our "limitations" are required to allow us to perceive the beauty and elegance in things.

More directly, humans will continue to interact with agents in some capacity, and let's say we
want humans to keep up:
an agent's raw chat (every message, tool call, and edit) quickly exceeds what a human can read. 

An _interaction model_ is a system with forms of presentation and interfaces for expressing desires. 
For instance, as a _form of presentation_, if the agent reports its work as checkpoints at a slightly abstracted 
level of detail (avoiding, say, the details of orchestration, or intermediate tool calls) and in a language a 
human can read, a large amount of work may fit into a few messages.

Designing effective interaction models seems to be of the utmost importance ... this is _not going to change_
as long as our biology and cognitive makeup are fixed.

<p align="center">
  <img src="figures/reading.svg" alt="A human reading a language model agent's raw chat falls behind after two of six leaps. When the agent reports checkpoints in a language a human can read, three messages cover all six leaps" width="720" />
</p>

_Reading the agent's raw chat (top) costs three red balls per leap, so the human's six balls cover the messages for two leaps. The soft red area of what the human understands stops there, and past it the path zigzags. With checkpoints (bottom), the agent reports one entry (red square) every two leaps, the human reads each with one red ball, and the soft red area covers the whole route._

Each new generation of models leaps further than the last. If a human reads each leap in steps of human size, each generation leaves the human further behind. But the cost of reading a leap depends on how surprising it is. On a smooth path, where each leap continues in the direction of the last, reading is cheap. We therefore seek interaction models in which the cost of reading a leap grows more slowly than its length. If reading a leap of length L costs about L<sup>α</sup> human steps, we want α below 1, so that a stronger agent leaves the human less far behind.

<p align="center">
  <img src="figures/generations.svg" alt="Each generation of a language model agent leaps further. At human step size, a human reads about a third of the leaps. On a smooth path, reading a leap costs about the square root of its length" width="720" />
</p>

_Each of three generations of models leaps 1.4 times further than the last. In the top row, the human reads in steps of human size, so reading one leap costs three, then four, then six red balls, and the six balls cover fewer leaps in each generation. Beyond them the agent scatters. On a smooth path (bottom), where each generation's checkpoints carry over as building blocks (dashed arrows), reading a leap costs about the square root of its length (α ≈ 0.5), and the agent reaches good software in 6, then 4, then 3 leaps._

Suppose that the steering itself is trained into the weights, as preference training already does in part. The path then stays smooth without a human reading any leap. But training cannot choose the goal, because what counts as good software depends on the task and on what the people working on it understand. A human then keeps up in order to understand the work. We value that understanding for its own sake, and we need it to choose the work's next goal.

<p align="center">
  <img src="figures/goals.svg" alt="With its steering trained into the weights, a language model agent sets its own goals along its current direction. A human who keeps up with the work chooses each next goal" width="720" />
</p>

_With the steering trained into the weights, the agent takes twelve smooth leaps in both rows. In the top row, the soft red area of what the human understands covers only the first leap. Past the first goal, the agent sets its own goals (teal rings and arrows) every three leaps along its current direction, and its last leap runs out of the frame. In the bottom row, the soft red area covers all of the work, and the human chooses each next goal (red arrows to ink rings)._

Two further figures, on how the harness prunes a single step and how the checkpoints of one run become building blocks for the next, are on [a separate page](https://github.com/a-tiny-project/.github/blob/main/profile/figures.md).

### The ultimate goal

At the end of the day, we enjoy fast
programmable software, and wish to see
more of it in the world. This endeavor
seems worthy of our tokens.

## Licensing

All work, unless otherwise specified, is licensed under AGPL v3.0 
(which, as is abundantly clear, is mostly symbolic these days 
-- but we hope it warms the hearts of a few)

If the idea of this project proves valuable, we fully expect people to reverse 
engineer or clean room reconstruct things they want. We've done the exact same here!
There are countless projects that we've drawn upon (and we collect and propagate
their licensing, and maintain references and commentary on influences in the READMEs
throughout our systems).

We can't really stop people going wild with agents. That's fine: use this project if you feel
like you can trust the contributors here to steer the agentic traces in good directions.

## Note on childlike play

We like to have a bit of fun with our software: we hope you find a bit of playful chaos 
in some of our releases. In the words of _The Little Schemer_, bon appetit!
