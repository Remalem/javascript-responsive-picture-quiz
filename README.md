# JavaScript Validation Method - Picture Quiz

An interactive, mobile compatible picture quiz with JQuery validation.

## Getting Started

### Description

To demonstrate a method of javascript validation, I've created a responsive image grid forming a quiz. A user can guess the video game character's name shown in each image by entering their answer into the corresponding input within each block. The user will be notified with a visual element as to whether the answer was correct or incorrect, based on a list of pre-defined possible answers for each block. 

## Functionality

### If Statement

        if ($.inArray($(element).siblings('.answer').val().toLowerCase(), answer) > -1) { //Default any entered text to lower case.
            //If answer matches, display "correct" visual element.
            $(element).parent().siblings(".correct").slideDown("500");
            //If answer matches, hide corresponding "clue" element.
            $(element).parent().siblings(".clue").slideUp("500");
        }
        else {
            //If answer does not match, hide "correct" visual element in the case it was already displayed.
            $(element).parent().siblings(".correct").slideUp("fast");
            //If answer does not match, display "incorrect" visual element.
            $(element).parent().siblings(".incorrect").slideDown("500").delay("1000").slideUp("500");
        }
        
The above statement firstly converts whatever answer the user has entered into the input to lower case, this makes creating the validation lists later a lot easier and safer. It then displays a different visual element within the block depending on whether the answer was correct or incorrect.

### Submit Button

        $(".answer-button").click(function () {
            quiz($(this));
        });
        
Allows execution of the above if statement if the submit button within each block is pressed.

### Enter Key

        $(".answer").keypress(function (event) {
            if (event.keyCode == 13) {
                event.preventDefault();
                $(this).siblings('.answer-button').click();
            }
        });
        
Allows execution of the above if statement if the enter key is pressed.

### Validation

        var GetAnswer = function(answer){
            if(answer == "1")
            {
                return ["possible answer 1", "possible answer 2", "possible answer 3", ];
            }
        };
        
The above function matches the user answer entered into the input box against the if statement within this function that correlates to the block in which it was entered. Any number of possible answers can be defined here. If the entered answer matches a defined answer, the "correct" visual element will display.


## Authors

* **Graham Speed** - [GitHub](https://github.com/remalem)

