# 1.0.3 Lab: Project Planning with a CLI App
- [1.0.3 Lab: Project Planning with a CLI App](#103-lab-project-planning-with-a-cli-app)
  - [Welcome to your first JS lab!](#welcome-to-your-first-js-lab)
  - [Goals](#goals)
  - [CLI vs GUI](#cli-vs-gui)
- [The Ask](#the-ask)
- [Features](#features)
- [Choosing the foundations, MVP, and stretch features](#choosing-the-foundations-mvp-and-stretch-features)
- [Research](#research)
  - [Some help](#some-help)
- [Step 1: Create a project](#step-1-create-a-project)
- [Step 2: Research](#step-2-research)
- [Step 3: File setup](#step-3-file-setup)
  - [Check connections](#check-connections)
- [Step 4: welcomeAndGetName()](#step-4-welcomeandgetname)
  - [State](#state)
  - [handling white space](#handling-white-space)
- [Step 5: List the options](#step-5-list-the-options)
- [Step 6: sayGoodbye](#step-6-saygoodbye)
  - [DRY - Don't Repeat Yourself](#dry---dont-repeat-yourself)
- [Pause: That's our foundations!](#pause-thats-our-foundations)
- [Step 7: Select an option](#step-7-select-an-option)
  - [Validation](#validation)
- [Step 8: "Route" to an "event handler"](#step-8-route-to-an-event-handler)
- [Step 9: Pick a random number](#step-9-pick-a-random-number)
- [Step 10: Compare answers and output](#step-10-compare-answers-and-output)
  - [Pure functions](#pure-functions)
- [Pause: MVP Done!](#pause-mvp-done)
- [Stretch Goals: More options](#stretch-goals-more-options)
  - [File Structure](#file-structure)
- [Next steps: Looping](#next-steps-looping)

## Welcome to your first JS lab!
This looks a little different than your assignments, huh? That's because labs are all about starting from scratch, and learning on your own (or with a partner). Assignments prepare you for plugging into the middle of a project,

## Goals
- Understand how to create your own NPM project
- Understand the basics of project management
- Use an NPM package as a dependency
- Build a CLI App that takes user input

## CLI vs GUI
By the way "CLI" stands for "Command Line Interface" and it's what we call programs that don't have a "GUI" (Graphical User Interface). It means the only way to interact with our program is via the terminal with text. It's not as old school as you think, you'll use a *lot* of CLI apps in your career. Sometimes, they're just faster to use than clicking around a GUI.

Alright, let's start at the beginning by breaking down what the "ask" of today's project is!

# The Ask
Basically, projects can usually be boiled down to a sentence or two. It's like the elevator pitch. This is where you *start*, and the ask for this app today would be:

> We want a simple CLI app that greets the user, does something with them, then closes.

As you can see it's super vague, but that's often how projects start. Sometimes they're literally just a question. It would be up to you and the project managers to distill exactly what features we want.

# Features
With the pitch out of the way, a project manager would either work with you or tell you about the specific "user stories" they want. A user story is basically a sentence that explains what a user could or would do with the program. They should each be simple, and they combine to form more complex flows.

In this case, I'm the project manager and I set these stories:

- A user can interact dynamically with the program
- A user will be greeted by the program
- A user will choose from options about what they want to do
- A user can play a random number guessing game
- A user can get a random piece of advice
- A user can get a random cheer
- A user's inputs can be validated
- A user can abandon the program by pressing any key at the option select
- When exiting, the program will say goodbye to the user

# Choosing the foundations, MVP, and stretch features
With the stories, you then have to break them up by priority. What should you build first? There's basically 3 stages of project deliverables:

1. The foundations are technically done, but basically no features.
2. This now has just enough features to be useful.
3. I can add additional features one by one safely now!

What do you think those three things would be for us here? Keep in mind what your skill level is. If you're unfamiliar with a tech stack or process, dial back your deliverables. **It's always better to under promise and over deliver.**

Before popping these open, think about how you would've split it up.
<details>
    <summary>Foundations</summary>
    <ul>
      <li> A user can interact dynamically with the program </li>
      <li> A user will be greeted by the program </li>
      <li> A user can see a list of options for the program </li>
      <li> When exiting, the program will say goodbye to the user </li>
    </ul>
</details>

<details>
    <summary>MVP</summary>
    <ul>
      <li> A user will choose from options about what they want to do </li>
      <li> A user can play a random number guessing game </li>
      <li> A user can abandon the program by pressing any key at the option select </li>
    </ul>
</details>

<details>
    <summary>Stretch Features</summary>
    <ul>
      <li> A user can get a random piece of advice </li>
      <li> A user can get a random cheer </li>
      <li> A user's inputs can be validated </li>
    </ul>
</details>

Is that how you would've done it? We're splitting it up the foundations pretty conservatively because we're going to use some new tech. Also you might notice we split some of the users stories up, that's totally fine as you plan more!

Now let's talk about another crucial step: research.

# Research
Ok so right off the bat, we know there's a big thing we've never worked with:

> A user can interact dynamically with the program:

As well as some general uncertainty about all the random pieces
> - A user can play a random number guessing game
> - A user can get a random piece of advice
> - A user can get a random cheer

When kicking off a project, always take some time to research the more difficult aspects of the project. This time upfront can show you where roadblocks will occur, and identifying and prioritizing un-blocking these bottle necks is the true trick to getting good at estimating projects.

## Some help
Ok, but since this is a lab (and unbeknownst to you, JS has a heck of a time with synchronous user input), we're going to give you 2 big hints:
- We'll use `prompt-sync` to get keyboard inputs from the user
- We'll give you some starter functions for getting words of wisdom and cheers

Ordinarily, after research and rough prototyping, we'd revist our overall plan, but we're going to be fine for this project.

**SO LET'S GET GOING!**

# Step 1: Create a project
Let's get things started right
- use the npm command to initialize the project
- make a `src` folder with an `index.js` inside
  - Probably will also want a `playground.js` file but live your life
- Add a start script that's uses `node` instead of `nodemon`
  - The interactive nature of `prompt-sync` doesn't seem to play nicely with `nodemon` unfortunately.
- Finally, install the `prompt-sync` package as a dependency

# Step 2: Research
The trick to a good research phase is *knowing when to end it*. Go into your research with very specific questions that you want answered. In this case, we gave you `prompt-sync` so the question is:

> How do you use this package to get user input?

That's it. To get started here are the [NPM docs on prompt-sync](https://www.npmjs.com/package/prompt-sync#promptask-value-opts) and a nice bit of starter code to play with:

```js
const prompt = require('prompt-sync')();

const name = prompt("What's your name? ");
const age = prompt("What's your age? ");
console.log(typeof name)
console.log(typeof age)
```

Read the docs but don't go crazy, look for only what you need to get started. Focus on things like functions, required arguments vs helpful arguments, and return data.

Once you feel confident about your answer to the primary question, move on! You can learn more as you go later, let's keep moving. Always keep moving forward.

# Step 3: File setup
For now let's keep it simple and use this mental framework:

```js
// imports at the top
const prompt = require('prompt-sync')();

// small, helper functions
const example = () => {}

// more complex event handler functions
const handleSomething = () => {
  example()
}

// Primary runner function
const main = () => {
  getInput()
  handleSomething()
  moreThings()
}

main();
```

Basically, imports always go first, then the smallest functions go on top, then the functions that reference them go after, and finally our `main()` function. In the file, the only file that actually gets *run* is `main()`. As our file grows, we can split things off into a `utils` or `lib` file, but this is fine for now.

Alright so all we actually have to do now is `require` prompt sync (Don't forget the extra `()`, that's not normal, but it's easy!) and a `main()` function.

## Check connections
Throw a log or something into `main` and run the `npm` start command to make sure everything is set up properly!


# Step 4: welcomeAndGetName()
Alright our first function should do 3 things:

- Log a generic welcome
- get a user's name via `prompt`
- return the user's name

```js
welcomeAndGetName();

// prints
Welcome!
What is your name: [input: Carms]
Hello Carms, nice to meet you!
```
We want to isolate our logic to a method, however since we have other functions who will want to read that name, we should return it.

Let's put this into our main function, and as a short check, we can also log our new `name` variable to see that it works:


```js
const main = () => {
  const name = welcomeAndGetName();
  console.log(name)
};

main();
```

## State
We might now consider that name as **"State."** State is just another word for "data our program uses internally." Sometimes it's **mutable**, which means it can be changed, and sometimes it's **immutable** which means once it's set, it can't be altered. Another way to say that is write/read.

Since we can't edit the `name` after get it, is this piece of state mutable or immutable?

> Keeping track of state is a really important part of our job. Poorly managed, mutable state is responsible for a lot of bugs.
> <br />-- Mike

## handling white space
What if a user accidentally puts a space like " name" or "name ", that would goof up our printing. Check out [the docs for `trim()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim), it might be what we're looking for.

# Step 5: List the options
This one is straightforward technically, but let's talk about dealing with users. In general, we want to give them as little opportunity as possible to make a mistake. So we *could* have them pick options like this:

```plaintext
Here are your options:
game - play a guessing game
advice - words of wisdom
cheer - cheer you on!
quit - exit the program
```

However, that's a *lot* of typing, and each keystroke is an opportunity for a mistake. Instead, what about single letters or numbers like this:

```plaintext
Here are your options:
1 - play a guessing game
2 - words of wisdom
3 - cheer you on!
Any other key - exit
```

So your next task is to create a function `showOptions()` that logs this information to the screen. Now, for the MVP, we're aren't doing all of the options. So it's up to you what you actually want this to output. All of them, or just add them as you go? It's up to you! This is your world.

# Step 6: sayGoodbye
To close out our program we need a function like:

```js
sayGoodbye(name);

// logs: Goodbye, Itzel!
```

Now, you may be wondering why we'd bother with such a simple function. That's logging a template string under the hood (spoilers). I'll tell you why: DRY code.

## DRY - Don't Repeat Yourself
Coders are a lazy bunch. Smart, but lazy. In general, if you can do something once and use it multiple times, that's real nice. So, it's true that we could just log a template with the name, however what if our app has multiple exits? No problem, just cut and copy the template log a few places.

But then we decide to edit the message. Uh oh. Now we have to go back to every copy (we might even have to use a global search to be sure) and edit the new text. That's annoying and error prone. **Manually cutting and copying too much can lead to inconsistent code**.

So instead, let's say we wrapped it in a function, and just used that *function* everywhere. Now, if we want to edit the string, we do it once in the function, and we're set! This is also the same idea with string constants. By using string constants we can make project or file wide edits instantly. Also, misspellings become errors and not just typos, so we can catch them.

```js
// Project wide constants example
const SCHOOL_NAME = 'Marcy';
const SCHOOL_ADDRESS = 'Industry City';

module.exports = {
  SCHOOL_NAME,
  SCHOOL_ADDRESS,
}

// Or less formal local constants, like in tests:
const cat = 'cat';
const dog = 'dog';
const iguana = 'iguana';

// constants also help catch typos
console.log('iguanna') // typo, no error
console.log(iguanna) // error, unknown variable
```

Now, not *everything* needs to be wrapped in a function or using a constant, but they're definitely tools for your toolbox to use when you see fit.

# Pause: That's our foundations!
Congrats! We set out a plan and executed it. The foundations seem like small output, but remember, we learned things and set the project up for success later. Foundations aren't ever shown off, but without a strong one, the Empire State Building would just be a pretty picture on a blueprint.

Good job, now let's press on to our MVP!

# Step 7: Select an option
We've listed out the options for the user, but we need someway to get their option. Let's make a function like `getUserNumber()` that uses our `prompt` to get a number input from the user:

```js
const option = getUserNumber();
// options would be 2 for example, not "2"
```

But our `prompt` always returns strings? How are we supposed to convert "2" to `2`? An easy way to do that is to use [the `Number()` function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number). Give it a try (and don't forget about `trim()` to format input)!

## Validation
Obviously, the user could type nonsense instead of a number. One of the benefits of wrapping this "simple" logic into a function is that we could handle errors right her. That way, no logic has to change beyond this function, but our entire app is safer. For example, we could automatically set any non-number input to equal 0, and elegantly handle that.

HOWEVER! Don't do it now! An MVP is *mostly* about the happy path, and we specifically said validation and error handling was a stretch goal, let's not get distracted from out plan and keep moving forward.

# Step 8: "Route" to an "event handler"
You may hear that a program is "event driven." That means it's really easy to follow a pattern of "When a user does X action, trigger Y function." Very often the function that "handles" the event, so it's called something like `handleSubmit()` or `handleClick()`. Let's use that convention and write a stub (meaning valid syntax but empty) function called `handleGuessingGame()`.

Now, the "event" is selecting an option, but how do we know what to do based on their selection? Simple, let's "route" them to their destination based on their choice. We have a couple options.

```js
// Traditional if/else
const option = getUserNumber();

if (option === 1) {
  handleGuessingGame();
} else if (option === 2) {
  // handleWordsOfWisdom() // doesn't exist yet
} else if (option === 3) {
  // handleWordsOfWisdom() // doesn't exist yet
}
sayGoodbye();

// ------------------------------------------------
// switch case
switch(option) {
  case 1:
    handleGuessingGame();
    break;
  case 2:
    // handleWordsOfWisdom() // doesn't exist yet
    break;
  case 3:
    // handleWordsOfWisdom() // doesn't exist yet
    break;
}
sayGoodbye();

// ------------------------------------------------
// guard clauses
const option = getUserNumber();
if (option === 1) return handleGuessingGame(name);
// if (option === 2) return handleWordsOfWisdom(name);
// if (option === 3) return handleCheers(name);
sayGoodbye()
```
There are pros and cons to each approach. For example, the guard clauses look the sleekest, however the catch is that now each one exits the `main` function. Meaning, we have to copy our `sayGoodbye()` into each of them. Not that none of them have a "else" case. That's because our function is just finished if they don't pick a number. If our program were more sophisticated, that may not be the case.

The point is, there are trade offs when picking code patterns. Some people vehemently dislike single line `if` guard clauses for the extra complexity they can sometimes hide. Whatever approach you take, make it with care and data to back it up.

> My one line `ifs` will be my downfall one day, but I'll be damned if I don't look good on the way down.
> <br />--mike

# Step 9: Pick a random number
With routing taken care of, let's move on to the question of how to deal with random. It seems like quite a few of our other functions could benefit from selecting random numbers in a range, so lets make a helper function `getRandomIntInRange()`. It should take in inclusive min, and an exclusive max (you'll see why later on) and return an integer:

```js
getRandomIntInRange(0,11)
// 0 -> 10
```

# Step 10: Compare answers and output
Let's turn back to our stubbed `handleGuessingGame()` function. It needs to do a few things:
1. Get the users guess and convert it to a number
2. create a random number as the right answer
3. compare those two numbers
4. congratulate if won, otherwise say better luck next time
5. (If you used guard clauses, you also need to sayGoodbye())

That's a lot of things! It's common that handler functions do a few more things than average functions, which is why helper functions are so important. We're already using a helper function for `getRandomIntInRange()`, but there's another one that might help too, a `checkAnswer()` function. It would handle steps 3 and 4

## Pure functions
You might hear the term "pure function." One of the most important pieces of a pure function is that given the same inputs, it will *always* have the same outcome. This is beneficial for a lot of reasons: it makes testing easy, it makes state management obvious, and it keeps functions small.

So, our `getRandomIntInRange()` is a helper function, but it's not pure. We could call it ten times with the same arguments, but get wildly different outputs. However, a `checkAnswer()` would have exactly the same outputs no matter how many times you called it with the same arguments. If you send in matching numbers, it will always congratulate, and if they don't match, it will always say better luck.

If you're interested in pure functions, check out this article on Functional [Programming in JS](https://www.freecodecamp.org/news/functional-programming-in-javascript/)

# Pause: MVP Done!
You did it again! Absolutely *crushing* these checkpoints. See how quickly we can move with good planning and foundations?

# Stretch Goals: More options
Well, you hit the main functionality, and now you can just add more handlers for more routing options. Here's the starter code for some wisdom and cheers (since we haven't technically gone over `arrays` yet). Look how it uses the length as the end of the random number range.

```js
const wordsOfWisdom = [
  'You should go to bed by 12:30',
  "It's better to mostly understand a little more every day, than to never move forward until you understand everything",
  'Eating breakfast has statistical benefits to brain power',
  "The best laid plans often fail, but plans that don't exist can never succeed",
  'Time management and communication are the two most important skills in the workplace',
  'Try to listen to others more than you speak',
]

const cheers = [
  'You can do it!',
  'You are the best!',
  'You are a coding machine!',
  'YOU ARE UNREALLLLLLLLL!',
  'LITERALLY UNSTOPPABLE!',
  "Can't even handle your greatness right now!",
];


const getWordsOfWisdom = () => wordsOfWisdom[getRandomIntInRange(0, wordsOfWisdom.length)];
const getCheer = () => cheers[getRandomIntInRange(0, cheers.length)];

```

However, you could also focus on adding validation to our *existing* features as well. It's up to you! But whatever you choose, move step by step.

## File Structure
By now, you have quite a few functions in your `index.js` It may be worth it to think about splitting up your files. In general, your projects *main* `index.js` doesn't export things. It just imports things and runs your app. So you could break out all your little helper functions into a `utils.js` (short for "utilities"), or perhaps knock out all the handlers into a `handlers.js`. Maybe each handler gets its own file, and then you import with a barrel file?

However you choose to organize your project, make sure you can back up your decision with a strong opinion. Don't do things unless you understand why.

# Next steps: Looping
And that's all for this project. But you may be wondering: "How would I make this all keep going?" It's kind of a bummer we essentially only get one round, and then we exit. Well, the answer is **looping!** And we'll learn about it next week. But if you're truly ready to go, why don't you learn about `while` loops. They are perfect for programs like this. they can run *until* you tell them to stop.