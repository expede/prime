# Forward

> 1. Avoid "success at all costs"
> 2. "Avoid success" at all costs
>
> — Two views of the Haskell motto

## Why I Care

I'm a huge fan of Haskell. I'm a self-taught programmer, and it was one of the first languages that I picked up very early in my career. To say that it has coloured my approach to programming would be a gross understatement — it has changed the way that I think in any language, introduced me to many sub-fields of PLT, broadened the scope of what I thought was possible when working in OO languages, and taught me how to think about problems in a very structured way. Much more of Haskell has been discovered than invented, which feels like you're programming with reality rather than microcode.

I'm so passionate about FP that I've volunteered many, many hours to spread these ideas. I co-founded the Vancouver Functional Programming Meetup, and ran it for several years. I facilitated an intro to Haskell group for much of that time, teaching the basics of Haskell to several dozen developers are various stages of their careers \(pro tip: more experienced devs had a harder time picking it up\). I even ported the most common idioms to Elixir \(the [Witchcraft suite](https://github.com/witchcrafters/)\). [My company](https://fission.codes/)'s core technology is built on Haskell. I regularly give conference talks on why you'd want to write in a structured, algebraic style.

Over the years I've found Haskell \(as both a language and ecosystem\) to have challenges that would obstruct learning and adoption by product teams. 30 years of cruft, inconsistent tooling, lack of standardization, and general newcomer hostility. The documentation is improving \(but lacking overall\), and much of the material is either written for total newcomers to functional programming or for category theorists.

There is clearly interest in Haskell, despite \(or perhaps because of\) the aura of mystery that surrounds it. It's a challenge to become proficient in without help. Many people attempt to learn the language several times over many years. There's a lack of good introductory material \(though that's thankfully changing\). From my own experiences and time giving back to the community, I've learned a lot about what developers want from Haskell, and where they're getting stuck.

## A New Hope

> It doesn't matter how beautiful your theory is, it doesn't matter how smart you are. If it doesn't agree with experiment, it's wrong.
>
> — Richard Feynman

I've been holding on for Haskell Prime / Haskell 2020 for several years, in hope that it would address the long list of concerns. When I saw the "[Haskell 2020 is Dead](https://reasonablypolymorphic.com/blog/haskell202x/)" article a few weeks ago, I ranted to anyone that would listen about how deeply disappointing the situation is.

My best guess is that the people with the ability to embark on a Haskell-compatible language are all happily using Haskell. The GHC is continuing to improve, but so much of the effort is going into type-level features. The type of person who gets deep enough into the language to mess around in GHC has mastered the language, no longer notice the sharp edges, and are generally happy with the state of things since they know all of the intricacies. They're more likely to add cool new feature than overhaul the language for approachability.

I feel that it's time for more than an overhaul — it's time for a Haskell-compatible language. I'm colloquially referring to this project as simply "Prime", a nod to the Haskell Prime committee, but for various reasons \(not least of which that it's intimidating\) this should remain only the working title. Haskell proper should continue doing its thing — there's clearly space for a language that's pushing the boundary for type systems going forward. For example, [Dependent Haskell](https://arxiv.org/pdf/1610.07978.pdf) and [Linear Haskell](https://arxiv.org/pdf/1710.09756.pdf) are some of my all-time favourite initiatives, and ones that I would love to pull into Prime as they evolve in Haskell proper.

I'm proposing that instead of simply starting from scratch, reusing the incredible ecosystem and GHC. This is an ambitious project, and not one that I'm either willing nor able to do alone. If there's sufficient community interest, this could be the project that many of us in the community have been waiting for — one that addresses the frustration of using Haskell in industry, for those curious about learning a new way of thinking, and delivering the productivity and safety that those that have mastered the language feel we have.

## [It's All Been Done](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwiX4Z-LmtfmAhVLHTQIHXdtBKIQyCkwAHoECAsQBQ&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DZs3xXlXSOKk&usg=AOvVaw2FFz6CoFCJqb8gbZ7_2qH_)

There is precedent for such a project. Beyond porting languages to new platforms, or other forms of close emulation, several languages have seen popular variants pop up over the past several years. These go beyond simple syntactic changes to provide different semantics, developer features \(e.g. first-class docs\), high-level features \(e.g. type systems\), and — importantly — new cultures optimizing for different things than their forebears.

| Ancestor | Descendant |
| :--- | :--- |
| Erlang | Elixir |
| OCaml | Reason |
| APL | J |
| Java | Scala |
| JavaScript | TypeScript |

On the other end of the spectrum, Haskell has been massively influential, to the point of having created an entire family of Haskell-like languages, or "Haskells". To the best of my knowledge, no other language targets the GHC specifically.

Part of Haskell's intention early on was to be an _influential_ language. A quick glance at the current versions of Ruby, Python, and TypeScript suggest that it's been exceedingly successful. It's time to close the circuit, and port some ideas back into Haskell. We've learned a lot about programming since the last Haskell standard in 2010. We can draw from lessons learned from Elixir, Elm, Rust, Idris, Hackett, PureScript, Unison, Golang \(yes really\), and of course Haskell itself, just to name a few.

## Bringing Tools [Nearer to Hand](https://www.infoq.com/presentations/Simple-Made-Easy/)

> The tools we use have a profound \(and devious!\) influence on our thinking habits, and, therefore, on our thinking abilities
>
> — Dijkstra, [How do we tell truths that might hurt?](http://www.cs.virginia.edu/~evans/cs655/readings/ewd498.html)

Developers in 2020 are looking for more than ideas — they want a toolkit that helps guide them. Systems for where things should go, to guide their approach, and sensible defaults to keep them pointed in the right direction. Beyond a language, they want a package manager, REPL, standardized configuration, and to have someone hand them "The `$Langauge` Way". In short, most developers want tools to Get Shit Done™. Haskell is a wide open field; you have the freedom to do essentially _whatever_, arrange your project to your personal tastes, and tailor even the lanaguge itself to the project. The paradox is that by being fully unconstrained, many people have more roadblocks, not fewer.

Look at some of the [most loved and wanted languages](https://insights.stackoverflow.com/survey/2019#most-loved-dreaded-and-wanted) today: Rust, Elixir, and Go. They all have integrated toolkits, standard libraries that suggest the "right way" \(e.g. Elixir's `GenServer`, Golang's `http`\), and attention to community management \(e.g. [Rust's GH Issues](https://github.com/rust-lang/rust/issues)\), standardized project scaffolding, [monitoring](https://elixir-lang.org/getting-started/debugging.html#observer) tools, and so on. This goes beyond a language, but less than a framework. Perhaps it's closer to an SDK.

A killer feature of Idris is interactive development. Elm and Rust have really amazing error messages with explanations and shockingly good suggestions. System F itself puts you in conversation with the type checker. An SDK in 2020 should nudge you towards better code, save you from making silly mistakes, encourage you to write clear code, and teach you about how to use the tools themselves. Like all [tools of thought](http://www.eecg.toronto.edu/~jzhu/csc326/readings/iverson.pdf), it should be a bicycle for the mind. This family of languages has the opportunity to create space for computer-assisted development / augmented programming.

## GHC Haskell Compatibility

> In the programming-language world, one rule of survival is simple: dance or die. It is not enough to make a beautiful language. You must also make it easy for programs written in your beautiful language to interact with programs written in other languages.
>
> — SPJ, [Tackling the Awkward Squad](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/07/mark.pdf?from=https%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsimonpj%2Fpapers%2Fmarktoberdorf%2Fmark.pdf)

The Glorious [Glasgow Haskell Compiler](https://www.haskell.org/ghc/) is an incredible piece of technology. It makes this very high level, lazy, immutable, functional language far more performant than it has any right to be. It provides essentially unbounded abstraction, green threads, and language features galore above and beyond Haskell 2010. In theory, it has the elements to have a developer experience without equal. It's the de facto Haskell compiler, and it would be ideal to be able to access the entire existing Haskell ecosystem \(compiler flags and all\).

GHC Haskell has its drawbacks. Many GHC features are implemented as specially formatted comments, doing anything practical with the ecosystem requires enabling a slew of features \(often several _dozen_\), and support for both the LLVM and fully static binaries \(always a hard problem\) are pretty grim. These aren't all GHC issues per se; it's that the language is being spread thin to meet the needs of a highly varied community between academe and industry.

The other compiler to keep an eye on is [GRIN](https://grin-compiler.github.io/). It looks like it has a lot of good ideas expressed clearly. I would actually like to target GRIN in the future, especially as we get more optimization benchmarks on larger programs, and potentially see if interoperability between GRIN languages get first-class support \(a challenge when they may have substantially different type systems and other statics\).

## Balancing Act

This project has potential risks. While its intention is to draw more people to the ecosystem, it could also split the community. It may be able to sufficiently balance newcomers and experienced Haskellers/MLers. It may get a reputation as "Haskell Lite", which the intent is certainly to avoid. Perhaps this time and energy should go into GHC Haskell itself to improve error messages and general developer experience. These are all possible, and we'll only know in retrospect.

Around 40% of the benefits of this project would come from a really robust Haskell standard library that was widely adopted — something that labeling a project as a "new language" actually does help with. The plethora of alternate `Prelude`s shows that this is probably a losing battle. Even if it were successful, my personal feeling is that it doesn't go far enough.

## [What Say You?](https://www.youtube.com/watch?v=f_4-rCROcsM)

Haskell is a really lovely ecosystem brimming with amazing ideas, is capable of creating highly reliable software, and makes refactoring a breeze. On the other hand, there's several decades of cruft, lack of standardization, quite a few gotchas, and it's difficult to extend. I believe that this is an ecosystem fully worth investing in, and drawing more people into.

What do you think? Is this project worth doing? Do you have other suggestions on how we can improve the ecosystem? Want to show support or opposition? Get in touch at:

* Twitter: [@expede](https://twitter.com/expede)
* Email: [hello@brooklynzelenka.com](mailto:hello@brooklynzelenka.com)

