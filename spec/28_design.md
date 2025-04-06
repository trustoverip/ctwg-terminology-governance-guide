## Terminology design aids

This chapter addresses the hard work needed when designing terminologies.

Think of designing and writing a consistent and accepted set of term definitions and the process of achieving consensus over them. Let alone the confusion you get when having the exact same terms but different concepts behind them.

::: warning Alert
You can't skip terminology design. It is fundamental to success.
::: 

 **If communication and understanding each other were easy, we could leave the hard part out.**

So **we must remember terminology design** if we want to convey a (new) concept and make sense to others. You need to understand first to be understood.

Let's take the bull by the horns.

### One-word solution (trailer)

::: warning Warning Notice
Hold your breath for the magic word, **the solution for everything** in terminology design! 
:::

But first, we have to make a small but significant detour! And that is: 

> **Why are we doing this?!**

### Who benefits

Who are we doing this for, what can this person do with it, and what is the unique result?

Will you be faster and better at writing texts? Will you be better understood by a larger audience?

The brief answer is *yes*. Just imprint this paragraph for more backing:

#### Why are we doing this?

**Authors and curators** of texts can follow this guideline for terminology design in order to **create their terminology**, **invent smart criteria to distinguish their concepts from others**, thereby identifying their own concepts clearer, understand their peers better, and finally **be understood better** and quicker by others.

Oops, the magic word is in there! Have you been able to locate it? No? Keep going!

### Reality check

Most term definitions in the world do not comply with the distinguishing-criteria rule, and that’s the uniqueness of this guide: it’s easy to follow and the result is an immensely improved terminology.

This guide won't be as comprehensive as the [TNO Terminology Design](https://tno-terminology-design.github.io/design-methods/). However, we offer the best of both worlds, resulting in simplicity and speed and about eighty percent the right way how it should be done.

Before we share the *all-encompassing solution* in just one word, we’ll lay out the step-by-step process to get your terminology done.

### Iterate through concepts

The idea is that anyone willing to explain some concepts by (first) understanding the perception of the receiving party will go through this loop for every term that is unclear, conflates, or is otherwise not fully understood.

::: note At least one criterium?
At least one clear, generally applicable criterion should come from this step-by-step per term.
:::

```mermaid
flowchart TD
A[A:I am writing, but I need to explain something! Help!];B{B:Terms understood?};C[/C:Glossary/]; D{D:Text with criteria understood?}; 
E[E:Term definition incl. criteria]; F[/F:Text with terms/];
 A --> |1: Identify concepts| B
 B --> |Yes, known term. Use ... | C
 B --> |2: No, I'll write criteria| D
 D --> |3: No, I'll adjust the criteria| D
 D --> |4: Yes, understood! Now a term can be defined| E
 E --> |4: Replace criteria by term | F
 E --> |Add term def to ...| C
```
Tada! Our matching guidelines are:
1. Start writing your objectives and ideas, and identify the concepts behind the terms you use ([why](#why-objectives)-[what is it](#what-identifying)?) 
2. Write the concept in a specific way: formulate criteria ([why](#why-criteria)-[how](#how-criteria)-[what is good](#what-good-criteria)?) when you expect confusion to arise
3. As long as the target group does not understand a term, replace it with your criteria ([why](#why-replace)-[how](#how-replace)?) 
4. As soon as it’s understood, define the term with those criteria and replace it with the term in the text. ([why](#why-back-terms)-[how](#how-back-terms)?)

### Example: Health Care intake

Although we inevitably introduce some unexplained terms with an example, here’s an example:

#### Step 1

In the digital identity field, you might want to write a vision document on how Self-Sovereign Identity could work in Health Care. One of the concepts/mechanisms within healthcare is to be sure who(the knee) will be operated on next. You write how that’s going to work out with terms covering this reassurance: *validation* and *verification*. The concept concluded successfully, which we call *authentication*.

#### Step 2

“Validation” and “Verification” of a visitor at the desk of the outpatient clinic are terms that might conflate with the “authentication” that needs to be successfully fulfilled: “Is this person really who he/she says he/she is?!”

You decide to distinguish validation and verification with a criterium for verification: 

> It must be “an automatic digital process” to be "verification".

The criterium is simple: must be an automatic digital process. 

This distinguishing criterion is handy because validation can also be something a person does!

Decryption on a computer is verification; checking a passport by the desk officer is not.

#### Step 3

Although you wrote ‘authentication is partly done by *an automatic digital process* called verification’, your team members are confused by the word ‘digital’. One brought forward that ‘computerized’ instead of digital is clearer, and the team agreed unanimously.

For the sake of the team members who weren’t present at the meeting, you leave the criteria in the text:

‘authentication is partly done by *an automatic computerized process* called verification.’

#### Step 4

Everyone understands the criteria and the term covering the concept behind it. You could now put the term definition, including its criteria, in your Terminology Engine and Glossary and replace the criteria in the text with only the term used:

‘authentication is partly done by verification.'

The term definition looks like this:

```
[[def: verification]]
 ~ 
 A data item or statement may be cryptographically securely attributable to its source (party at the source end) by any recipient verifier (party at the destination end). The process must be automatic and computerized.
 ```

**End of example.**

In this process and iteration, you could look for over-arching or adjacent term definitions (with criteria!) that match your concept. If this is the case, you could adopt a term definition, with or without an extra note. 
That’s when consensus building comes in as a spin-off of your terminology design.

### The magic word

What could the magic word be? No worries! Ladies and gentlemen (drum roll), the magic word in designing all your terms, defining them in a reproducible way so that anyone could identify your concepts, understand your ideas better, and apply the word by themself (drums hold!):
Criteria!

A least one well-formulated criterium is what we need per term definition, or should we say we need *minimally one* in order to distinguish whether something is 
- included or excluded from the definition
- inside or outside of the concept behind the term
Criteria! It's just pure magic.

::: warning Wait, wait. Come back. Please?
Ah, happily, you’re still here. We need to share a question at this stage. Remember, we’re trying to offer a simple and speedy guideline to create great terminology for your project. 
:::

Why is it so **d.mn** difficult to get people to write proper criteria? If the “magic word” ‘criteria’ delivers the promise, why all the fuzz? Why are nearly all definitions in the digital world without proper criteria??

Because
- it’s work, it’s a task
- it needs practice
- it needs communication
- it needs the understanding of others
- it needs the dear wish to want to understand other people first before you push to be understood.

### The why and how of all steps

In the next paragraph, we'll revisit the guidelines with reasons and further instructions.

### 1. Start writing your objectives and ideas, and identify the concepts behind the terms you use 

```mermaid
flowchart TD
A[A:I am writing, Help Terminology!];B{B:Terms understood?}
 A --> |1: Identify concepts| B
```

#### why writing your objectives and ideas down {#why-objectives}
If you want to guide the process of being understood and getting support, it's good to have a reference.

#### What is "identifying a concept"? {#what-identifying}
An identifier points to something, in this case, to a concept. Identification is the process of clearly describing what the concept is and defining the term that points to it.

### 2. Write the concept in a specific way: formulate criteria when you expect confusion to arise

```mermaid
flowchart TD
B{B:Terms understood?}; D{D:Text with criteria understood?}; 
 B --> |2: No, I'll write criteria| D
```

#### why criteria? {#why-criteria}
Another person should be able to apply wording to a particular concept and decide whether something falls in or out of the criteria. Example: if someone defines a stool with the criterium "all furniture to comfortably sit on with exactly three legs from seat to each non-fixed contact point of the leg on the floor," then anyone could (dis)qualify various instances of something to sit on that looks like a stool to many.
Although you might not fully agree that a 4-legged stool is no stool according to this definition with this criterium, the fact is that it's the generally applicable criterium that we were looking for.

##### Stools IN the criterium

![Stools](https://github.com/trustoverip/ctwg-terminology-governance-guide/blob/main/images/Stools.png?raw=true)

##### Stools OUTSIDE the criterium

![Not Stools](https://github.com/trustoverip/ctwg-terminology-governance-guide/blob/main/images/Non-stools.png?raw=true)

::: note Important consideration
Communication, understanding, and learning will skyrocket with clear criteria, invest time in them, and earn time back further down the road.
:::

Example: moving stools

If a group of people had to move every stool, but only stools, from a furniture warehouse into a giant lorry without clear criteria on what a stool is and isn't, you would leave stools behind and for sure bring back half a truck of furniture upon unloading.

#### how to formulate criteria {#how-criteria}

Using text, you can formulate criteria. You could add examples to a criterium of edge cases/corner cases: what falls just in the criterium and outside?

#### What are good criteria? {#what-good-criteria}

Criteria that are deterministic and clearly distinguish something.

### 3. As long as the target group does not understand a term: replace it with your criteria

```mermaid
flowchart TD
D{D:Text with criteria understood?}
 D --> |3: No, I'll adjust criteria | D
```

#### why replace terms by criteria? {#why-replace}

Criteria can be independently applied; terms have an alleged meaning, and interpretations of terms might point to distinctive concepts.
Example: *move the stools into the van* might be interpreted as "break out the fixed stools in the cantina and bring the remnants to the van."

#### How to replace terms with criteria? {#how-replace}

Replace the term with the sentence criteria it might consist of.

Example: *move the stools into the van* -> *move into the van all furniture to comfortably sit on with exactly 3 legs from seat to each non-fixed contact point of the leg on the floor*

### 4. As soon as it’s understood, define the term with those criteria and replace the criteria in the text with the term.

```mermaid
flowchart TD
D{D:Text with criteria understood?}; 
E[E:Term definition incl. criteria]; F[/F:Text with terms/]
 D --> |4: Yes, a term can be defined| E
 E --> |4: Replace criteria by term | F
```

#### why put back terms {#why-back-terms}

Once you've identified a concept for all stakeholders, repeating lengthy criteria descriptions in a text makes no sense. Maintenance of the criteria is also easier with a single point of definition. 

#### how to put back terms {#how-back-terms}

Be sure to create a Terminology definition with the criteria and identify this concept with the term intended.

For example:
```
[[def: stool, stools]]
 ~ furniture to comfortably sit on with exactly three legs from the seat to each non-fixed contact point of the leg on the floor
```
AND then change the concept criteria in the text with the concept term:

move the ```[[ref: stools]]``` into the van.

#### Next time 
You might come across a concept that has already been identified and defined with a term + criteria:

```mermaid
flowchart TD
A[A:I am writing, but I need to explain something! Help!];B{B:Terms understood?};C[/C:Glossary/]
 A --> |1: Identify concepts| B
 B --> |Yes, known term. Use ... | C
```

### Wrap up

Isn’t the magic word "Criteria" a bit cruel? It might snatch average human beings in the heart of their weakness: understanding others. Yet "mutual understanding" is needed to formulate suitable criteria.

### Move forward

Note that Terminology building is concise and extensive work. Beyond the basic terms, often defined as noun or noun phrases (e.g., "validation" and "peer to peer validation") we come across these challenges:
  - **different styles** to describe a concept: nouns, verbs, adverbs, adjectives, and relationships. E.g., validation, validator, validate, validated, valid? Validly? Validated data, validated person, validated intake, etc.
  - **abbreviations** for example VALD, p2p-validation
  - **synonyms** {case dependent}
  - **forms** e.g. validations, Validation, Peer-to-peer Validation, etc.

### Two for the road
1. How could we incentivize people to do the hard work of proper terminology design?

Ideas are welcome.

2. Never forget the *magic* word: **Criteria**!

### Further reading

See more here: 
- [TEv2 Design Methods Pages](https://tno-terminology-design.github.io/design-methods/)
- [TEv2 Tools Repo](https://github.com/tno-terminology-design/tev2-tools)
- [TEv2 Specifications Pages](https://tno-terminology-design.github.io/tev2-specifications)
