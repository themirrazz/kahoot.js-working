# About
Kahoot.js is a library to interact with the Kahoot API. kahoot.js supports joining and interacting with quizzes and challenges.
**Installation requires Node.js 10.9.0 or higher.**


![Dependencies](https://david-dm.org/theusaf/kahoot.js-updated.svg) [![Known Vulnerabilities](https://snyk.io/test/github/theusaf/kahoot.js-updated/badge.svg)](https://snyk.io/test/github/theusaf/kahoot.js-updated) [![HitCount](https://hits.dwyl.com/theusaf/kahoot.js-updated.svg)](https://hits.dwyl.com/theusaf/kahoot.js-updated) ![Builds](https://travis-ci.com/theusaf/kahoot.js-updated.svg?branch=master) ![Docs](https://inch-ci.org/github/theusaf/kahoot.js-updated.svg?branch=master)

**Note: If upgrading from version 1.x.x, read the latest documentation for the new api first.**

# Basic Example
#### Note: this is not yet published to NPM.
```js
const Kahoot = require("./kahootjs-working");
const client = new Kahoot();
console.log("Joining kahoot...");
client.join(9802345 /* Or any other kahoot game pin */, "kahoot.js");
client.on("Joined", () => {
  console.log("I joined the Kahoot!");
});
client.on("QuizStart", () => {
  console.log("The quiz has started!");
});
client.on("QuestionStart", question => {
  console.log("A new question has started, answering the first answer.");
  question.answer(0);
});
client.on("QuizEnd", () => {
  console.log("The quiz has ended.");
});
```

## Full API Documentation
See [Documentation.md](Documentation.md).

## Examples
See `examples/` and `tests/`.

## Event name aliases
* `question` for `QuestionStart`
* `questionend` for `QuestionEnd`
* `start` for `QuizStart`
* `end` for `QuizEnd`
* `podium` for `Podium`
* `connect` for `Joined`
* `2fa` for `TwoFactorReset`

## New events
* `samename` emitted when the connection is terminated because of a duplicate username
* `locked` emitted when the connection fails because the Kahoot is locked
