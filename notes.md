# Notes on a Denotational Design talk

 <!-- References -->

[*Another lovely example of type class morphisms*]: http://conal.net/blog/posts/another-lovely-example-of-type-class-morphisms/ "blog post"

[*Composing memo tries*]: http://conal.net/blog/posts/composing-memo-tries/ "blog post"

[*Denotational design with type class morphisms*]: http://conal.net/papers/type-class-morphisms/ "Paper"

[*Reimagining matrices*]: http://conal.net/blog/posts/reimagining-matrices "blog post"


## Miscellaneous thoughts

Some thoughts on my denotational design talk from last week:

Most programming puts how before the what.
For me, the essence of functional programming is as a clear and precise illuminating language with which explore the what.
Insert Edster Dykstras quotes about computer science and telescopes.
However, even functional programming can be used in a way that focuses on how and neglects what.
How can we be more clear about what?
I don't think the answer is to be found in software engineering, which places software as a primary artifact.
To me, software has always been a means to an end, not an end unto itself.
So what is the end of that interest me?
It is ideas.
These ideas, of course, could be about machines programs and execution and so on, but those areas are not my particular kink.
No offense to anyone who is into machines for their own sake.
Engineering is a fine discipline.

What makes programs so interesting?
They are just utterances, aren't they?
Why do we feel compelled to put so much of our time and thought into this particular form utterance?
What makes it different from others?
What are some defining characteristics of programming as a means of expression?
One characteristic is that these utterances are executable.
But what really makes them executable?
What distinguishes them from other forms?
I want to suggest that unambiguity is one important characteristic.
Now, if unambiguity is so important, we would probably like to experience that value elsewhere.
What about the goals that we are trying to accomplish by our programs?
What about the ends to which our program are the means?
I have the impression that too many or perhaps most programmers, programming is about making machines do things.
I wonder, however, what makes a person to want to control machines, or to control anyone/anything, for that matter.

"If a man points at the moon, an idiot will look at the finger." (Sufi wisdom.)
I want to suggest that as programmers, we have become beguiled, in the sense of the quote above.
Computers were designed by mathematicians to solve mathematical problems.
Over time, the programmers have become the programmees.
("We shape our tools and afterwards our tools shape us." - Marshall McLuhan)
For the most part, we have become so enchanted by our tools that we have mostly abandoned the original enterprise.
Insert quote about tools shaping us.

If I have a clear understanding of a problem I want to solve, or a domain of thought I want to explore, then I can try to use the machine has a telescope for microscope through which to solve and examine my questions of interest.

Talk about popularity and dilution.
How can I broach this subject in a way that is clear and preferably not too offensive for people to listen to?

## Talk notes

### Math vs programming

How do math and programming compare?
Some thoughts:

*   Math is precise & rigorous, while programming is informal & heuristic.
*   Math is abstract/theoretical, while programming is concrete/applied.
*   Math is about being, while programming is about doing.

Can we bring the strengths of math into programming?
You might think that functional programming does just that.
I want to suggest that FP *can* combine these strengths, but it usually doesn't, even for Haskell.
Furthermore, I'll say that functional programming---including Haskell---has largely lost its unique essential strength on the road to popularity, particularly with what's commonly (and misleadingly) called "monadic IO".

----

The idea of "denotational design" is to use *meanings* (denotations) to as a rigorous and practical basis for designing and developing programs.

What do I mean by "meanings"?
Simply, mathematical values, which needn't be the sort of values we manipulate in programs.

In DD, we distinguish between program types and mathematical types, *and* we make a precise connection between the two.
The connection plays the following crucial roles:

*   It guides the design of an API.
*   It precisely specifies what it means for an implementation to be *correct*, without unduly constraining implementation freedom.
*   It provides a discipline for constructing correct implementations.
*   It guarantees that all class laws hold.

A host language and library provides a basic set of types *and* their denotations.
For instance, in Haskell, we have the type `Integer`, which denotes integers plus bottom.
We also have the type `a -> b`, which denotes a particular class of functions from $A$ to $B$, where `a` and `b` denote $A$ and $B$ respectively.
Not just any functions, but the *continuous* ones, where "continuous" refers to information-monotonicity and limits.

Importantly, not all types in Haskell have denotations.
For this reason, there is a "denotative" subset and a non-denotative subset.
The rigor & elegance follows from the denotative subset and does not apply to the rest of the language.
A prime non-denotative example is what's called "`IO`".
That type is "magical", which I define as having an implementation but no denotation.
(There is a popular but false myth that `IO` is simply the `State` monad specialized to pass the "world" as state. Even if we knew of a correct denotation, it would almost certainly be too complicated for practical use.)

One of the earliest software designs to which I applied DD is what came to be called "functional reactive programming" or "FRP".
Sadly, in popular usage, "FRP" has come to refer to something very different from its original definition, losing its essential characteristics and with it its precision and deep elegance.
I'll talk about what I originally meant and still mean, as contrasted with popular notions.

The DD approach to software design always begins with the same question:

 > What are the things represented by our programs?

Most of the insight and essence comes from hanging out with this question.
Candidate answers will be mathematical "models", i.e., values of a precisely defined mathematical type.
Candidates must satisfy the following properties:

*   Precise --- mathematical rather than hand-waving, to steer clear of deception
*   Adequate --- expressive enough for our programming purposes

Among the precise and adequate candidates, we want to optimize for the following properties:

*   Simple --- for practical reasoning and accurate intuition
*   Compelling --- ...

## Quotes

"The purpose of abstraction is not to be vague, but to create a new semantic level in which one can be absolutely precise." - Edsger Dijkstra

## Talk design thoughts

*   Start with at least one simple example to ground the upcoming abstract explanation.

### Examples

*   FRP: dynamic values / variation over time
*   Image manipulation: variation over space
*   Efficient finite maps (from DD/TCM paper)
*   [Memo tries][*Composing memo tries*]
*   [Matrices][*Reimagining matrices*]
*   [Fold fusion][*Another lovely example of type class morphisms*]
