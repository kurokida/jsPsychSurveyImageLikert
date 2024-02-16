# jsPsychSurveyImageLikert

This plugin is based on [the jsPsych survey-likert plugin](https://www.jspsych.org/7.3/plugins/survey-likert/). A stimulus image is displayed on the left and the Likert scales on the right. This plugin may be useful when many scales are used for a single image.

# Added properties
You can use this plugin in much the same way as the survey-likert plugin. The following properties are newly added.

```javascript
stimulus: {
    type: jspsych.ParameterType.IMAGE,
    pretty_name: "Stimulus",
    default: undefined,
},
image_preamble: {
    type: jspsych.ParameterType.HTML_STRING,
    pretty_name: "Image Preamble",
    default: null,
},
image_width: {
    type: jspsych.ParameterType.INT,
    pretty_name: 'Image width',
    default: 500,
    description: 'Width of the image in pixels.'
},
scale_height: {
    type: jspsych.ParameterType.INT,
    pretty_name: 'Scale height',
    default: 300,
    description: 'Height of the likert scales in pixels.'
},
```

# Example

```javascript
const jsPsych = initJsPsych({})
    
const images = [
    "stim/A.png",
    "stim/B.png"
];

const preload = { // Note that manual preloading of the images is needed.
    type: jsPsychPreload,
    images: images,
}

const scale = [
    "Strongly Disagree", 
    "Disagree", 
    "Neutral", 
    "Agree", 
    "Strongly Agree"
];

const likert_trial = {
    type: jsPsychSurveyImageLikert,
    stimulus: "stim/A.png",
    preamble: "For each of the questions about the image, please select the one that best describes your impression.",
    scale_height: 500,
    image_width: 400,
    questions: [
        {prompt: "Beautiful", name: "Beautiful", labels: scale, required: true},
        {prompt: "Comfort", name: "Comfort", labels: scale, required: true},
    ],
};

jsPsych.run([preload, likert_trial])
```