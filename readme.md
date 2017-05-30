## Alexa Skills

Alexa Skills is a repository for 3 Alexa Skills built for the Amazon Echo that helps programmers stay sharp with their programming concepts.  This repository contains skills that improve your algorithms, sorting algorithms and data structures.

***

[Alexa Store Link for Programmer Quiz][programmerquiz]  
[Github Repo](https://github.com/peterzhen/ProgrammerQuiz)  

***

[Alexa Store Link for Daily Data Structure][dailydatastructure]  
[Github Repo](https://github.com/peterzhen/DailyDataStructure)  

***

[Alexa Store Link for Daily Sorting Algorithm][dailysortingalgorithm]  
[Github Repo](https://github.com/peterzhen/DailySortingAlgorithm)  

***

[programmerquiz]: https://www.amazon.com/THOS-Programmer-Quiz/dp/B06XT4V8VF/ref=sr_1_1?s=digital-skills&ie=UTF8&qid=1496019754&sr=1-1&keywords=programmer

[dailydatastructure]: https://www.amazon.com/THOS-Daily-Data-Structure/dp/B071Y57LN4/ref=sr_1_1?s=digital-skills&ie=UTF8&qid=1496122993&sr=1-1&keywords=data+structure

[dailysortingalgorithm]: https://www.amazon.com/THOS-Daily-Sorting-Algorithms/dp/B071DH61G8/ref=sr_1_2?s=digital-skills&ie=UTF8&qid=1496123003&sr=1-2&keywords=sorting


## Instructions

To use these Amazon Alexa Skills, follow the links to add the specific skills to your Amazon Account.  This will enable the skill on all your Alexa enabled devices(Amazon Echo, Amazon Dot etc...).  

### To invoke ProgrammerQuiz simply say:

`"Alexa, open Programmer Quiz"`

This will start up the application and ask a random algorithms question for you to answer.

### To invoke Daily Data Structure simply say:

`"Alexa, open Daily Data Structure"`

This will start up the application and provide a Data Structure and it's properties..

### To invoke Daily Sorting Algorithm simply say:

`"Alexa, open Daily Sorting Algorithm"`

This will start up the application and provide a sorting algorithm with it's time complexities and properties.

## The Code

These skills are built using the `Amazon Alexa SDK` using Node and `JavaScript` as the language of choice.  Leveraging the `Alexa SDK`, I set up event listeners for specific voice commands to interact with the user when the program is active.  

When a new request for a programming question is activated, a random question from the preset data is selected and is given to the user.

```javascript
function handleNewQuestionRequest(response) {
    // Get a random space fact from the space facts list
    var questionIndex = Math.floor(Math.random() * QUESTIONS.length);
    var randomQuestion = QUESTIONS[questionIndex];

    // Create speech output
    var speechOutput = "Here's your Programming Question: " + randomQuestion;
    var cardTitle = "Your Question";
    response.tellWithCard(speechOutput, cardTitle, speechOutput);
}
```

For Daily Data Structure and Daily Sorting Algorithm, speech objects are created to request a response from Amazon Services.

```javascript
function createSpeechObject(optionsParam) {
    if (optionsParam && optionsParam.type === 'SSML') {
        return {
            type: optionsParam.type,
            ssml: optionsParam.speech
        };
    } else {
        return {
            type: optionsParam.type || 'PlainText',
            text: optionsParam.speech || optionsParam
        }
    }
}
```
