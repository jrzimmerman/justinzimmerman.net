+++
author = "Justin Zimmerman"
date = "2015-12-13T10:37:06-04:00"
description = "Identifying triggers in whiteboarding situations, and how to deal with those triggers."
keywords = ["Whiteboarding"]
tags = ["Whiteboarding"]
title = "On Whiteboarding: Triggers"
topics = ["Whiteboarding"]
type = "post"

+++

I will be the first to admit, I struggle in whiteboarding situations, especially in the context of technical interviewing when triggers arise. I hope this post helps you become better at whiteboarding when these certain triggers occur.

I have recognized that there are two types of triggers that happen while whiteboarding. The first trigger is an interpersonal trigger that I will call a **"spiraling"** trigger. The next is an external trigger that I will call a **"questioning"** trigger.

Let's dive into what each of the triggers are and what we can do about them.

### Spiraling Triggers

This first type of trigger is what happens when our plan starts to "spiral downward" and ultimately fall apart the moment when we realize our initial solution to the problem *isn't* going to work.

When I first started attempting technical questions, or what I like to call *"toy problems"*, spiraling triggers were the demise of many solutions. So what can we do about them?

The first step is **recognizing** that you have started to spiral downward. It seems like something obvious right? Maybe not at first to the unexperienced.

> Thoughts of "Oh man, my solution doesn't work. I can't solve this. What am I even doing here? I can't believe I am wasting this interviewers time!" can easily start creeping into the mind.

We need to recognize when the spiraling starts, and quickly break out of it. **Take a deep breath, and stand up straight.** Seriously. It helps.

We need to get oxygen back into our brains and start thinking down the correct path again. Wasting brain power on how we aren't solving the problem won't help us find a solution.

Don't worry though, if we can recognize our spiraling, it becomes much easier to break out of the spiral after some practice.

After taking a breath, start thinking of what new information has been introduced. This segues nicely into the next trigger.


### Questioning Triggers

This next type of trigger is a **questioning trigger**. This occurs when new information is provided by the interviewer, or a new realization modifies our understanding of the problem.

> If an interviewer asks "Does that work?" or "Is that right?" consider it a questioning trigger.

Here are a few steps when approached with a questioning trigger.

#### 1. Amend the current line of pseudocode

Okay, maybe this isn't as earth shattering as we might have hoped, but do not overlook this simple strategy. For me, when a *questioning trigger* occurs, I think of a solution and want to rush to the beginning of my pseudocode and start changing everything from the beginning.

![best idea](http://i.giphy.com/BfBqQV47hLFh6.gif)

>This is actually counter productive and will hamper our ability to solve the problem.

What's the big deal? By the time we get back to the current line of pseudocode, we've forgotten our epiphany making it harder for us to move forward.

#### 2. Visualize the conflicting information

Let's say our toy problem requires us to traverse a tree and we find a flaw in our logic. Trees are excellent opportunities to visualize what our data looks like.

For instance, we realize our solution won't traverse left nodes if right nodes of the tree have data in them. Let's visualize examples of edge cases.

```
USEFUL DIAGRAM!
      (N)
    /      \
  (Null)    (RC)
            /
          (LC2)

USEFUL DIAGRAM!
      (N)
    /      \
  (LC)    (Null)

USEFUL DIAGRAM!
      (N)
    /      \
  (Null)    (Null)
```

When we can visualize different edge cases, it will be a lot easier to incorporate solutions into our pseudocode.

#### 3. Create new example data

After visualizing the new information, our next step is to create example data to help solve the problem.

If we realize our problem needs a function that will require a callback to store data asynchronously, think of example data that we can provide to our solution.

```js
  asyncMap([
   function(cb){
     setTimeout(function(){
       cb('one');
     }, 200);
   },
   function(cb){
     setTimeout(function(){
       cb('two');
    }, 100);
   }
  ],
   function(results){
     // the results array will equal ['one','two'] even though
     // the second function had a shorter timeout.
     console.log(results); // ['one', 'two']
 });
```

Write an example function, include an example timeout length, and example data that results from the function.

It is imperative that our example data includes edge cases. The more edge cases we add to our example data, the easier finding a solution will be.

#### 4. Step through pseudocode with example data

This is a critical step that I am continuing to work on while solving toy problems.

We want to write in-line pseudocode as if we were the compiler. Using our example data created in the previous step, iterate through each line of the pseudocode. We want to write down what our variables store at each pass.

```js
// after 100ms
// 2
// counter = 1
// result = [,,'one']
// check if 1 === 2 -> false


// after 200ms
// 2
// counter = 2
// result = [,, 'two']
// check if 2 === 2 -> true
// callback(result) Boom! // -> ['one, 'two']
```

This allows us even greater insight to any flaws within our pseudocode.

#### 5. Finish pseudocode completely before rushing to write code

When I figure out part of the solution, I get excited and want to start coding right away. From experience, I can safely say this is the best way to run into additional problems.

We want to be sure to finish iterating through pseudocode with our example data from step 4. This allows us to get a better idea of what exactly needs to happen to solve the problem, and write correct code.

> We want to make our pseudocode a cheat sheet, not a general overview.

When in whiteboarding situations, we only want to be doing 2 out of 3 tasks at all times:

- thinking
- writing
- talking

When we do more than 2 of these things at once, we are at risk of spiraling. This is why it is important that we have complete pseudocode before we start coding. We now only have to worry about the last 2 points: **writing** and **talking** when writing actual code.

Thanks for taking the time to read this lengthy post. If you can remember these steps I guarantee you will not only come to a solution, but impress your interviewer along the way.
