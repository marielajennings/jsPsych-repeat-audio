##jspsych-repeat-audio plugin

The repeat-audio plugin allows the user to replay a sound file until they are ready to answer the quiestions shown below the replay button. The questions are presented in a multiple choice format and require a response to proceed. There can be one or multiple questions associated with the sound clip. The user has to click on the "Next" button in order to proceed after answering all the questions in the trial.

###Parameters

The following table lists the parameters associated with this plugin. Parameters with the default value of *undefined* must be specified. 

| Parameter| Type| Default Value| Description|
| ---------|:---:|:------------:|:-----------|
|stimulus|string|*undefined*| Provides a path to the audio file to be played.
|questions|array|*undefined*|An array of strings. The strings are the prompts/questions that will be associated with a group of options (radio buttons). All questions will get presented on the same page (trial).
|options|array|*undefined*| An array of arrays. The innermost arrays contain a set of options to display for an individual question. The length of the outer array should be the same as the number of questions.
|required|boolean|null|A boolean value. Indicates if a question is required (true) or not (false), using the HTML5 required attribute.  If this parameter is undefined, all questions will be optional.
|horizontal|boolean|false| If true, then questions are centered and options are displayed horizontally.
|preamble|array|empty string|Array of HTML formatted strings to display at the top of each page above all the questions. Each element of the array corresponds to a trial/page of questions.
|correct|array|*undefined*|Specifies the correct answer for each question.
|force_correct|boolean|null|Specifies whether the questions in the trial need to be answered correctly before ending the trial.
|superq|string|null|Specifies a question/sentence that applies to all the questions that follow.

###Data Generated


| Name| Type|  Value| 
| ---------|:---:|:-----------|
| rt|numeric|The response time in milliseconds for the subject to make a response. The time is measured from when the questions first appear on the screen until the subject's response.
|preamble|string|The specific preamble for the whole trial if any (otherwise empty string).
|superq|string|The specific superq for the trial if any (otherwise false).
|stimulus| string|A string containing the path to the audio file associated with the questions.
|questions|array of strings|The questions associated with the trial.
|responses|A string in JSON format containing the responses for each question. The encoded object will have a separate variable for the response to each question, with the first answer in the trial being recorded in A0, the second in A1, and so on. The responses are recorded as the name of the option label.

###Example

```
var audio1 = {

type: "repeat-audio",
stimulus: `/static/audio/NAIV-001.mp3`,
questions:['Question1:','Question2:' ],
options: [['Answer1','Answer2'], ['Answer1','Answer2','Answer3']],
correct:['NA','NA'],
required:true,
force_correct:false

};

```
