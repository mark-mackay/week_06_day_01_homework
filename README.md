# Episode  1
###
###  Anticipate that this will log "The murderer is Miss Scarlet." as all the constants seem to be declared in the same scope.
###
# Episode  2
###  Anticipate this will error as we are trying to change the value of a string constant
###  /Users/markmackay/codeclan_work/week_06/day1/homework.js:19
###    murderer = 'Mrs. Peacock';
###             ^
###
###  TypeError: Assignment to constant variable.

# Episode  3
###  First verdict will declare Mrs Peacock & the second will declare Professor plum as the murderer variable is local to the declaremurderer function.

# Episode  4

###  This will display "The suspects are Miss Scarlet, Professor Plum, Colonel Mustard" as there is a local variable defined with the same name as suspect 3
###  The second log will display "Suspect three is Mrs. Peacock" as this is the value in that external scope

# Episode  5

###  This will display "The weapon is the Revolver" as the elements inside the scenario object can be changed despite it being a constant.

# Episode  6


###  Anticipate this will output The murderer is Colonel Mustard as despite running the functions the variables within them are local and the global value is never changed.
###  Actual Output... The murderer is Mrs. White.
###  Got this wrong! I now see this because the variables were not declared in the functions they were assigned!

# Episode  7


###  Anticipate this will output The murderer is Mr. Green as this is the the last place the global variable is assigned,
###  the assignment within the unexectedOutcome function I think will be local to the plotTwist declaration

# Episode  8


###  Think this will log "The weapon is Candle Stick" as the global object properties are changed to allow a cascade through the whole sequence of functions


# Episode  9

### Think this may error as we are trying to declare the same variable again within the if statement -- Wrong!
Failing that it will remain Professor plum as if the declaration works it is local to the if block. -- Right.

# Episode  10 (# Episode  8 adapted)


````

const scenario = {
  murderer: 'Mrs. Peacock',
  room: 'Conservatory',
  weapon: 'Lead Pipe'
};

const changeScenario = function() {
  scenario.murderer = 'Professor Plum';
  scenario.room = 'Kitchen';

  const plotTwist = function(room) {
    if (scenario.room === room) {
      scenario.murderer = 'Colonel Mustard';
    } else {
      scenario.murderer = 'Miss Scarlet';
    }

`
    const unexpectedOutcome = function(murderer) {
      if (scenario.murderer === murderer) {
        scenario.weapon = 'Rope';
        scenario.room = 'Dining Room'
      }
    }

    unexpectedOutcome('Colonel Mustard');
  }

  plotTwist('Dining Room');
}

const declareMurderer = function() {
  return `The murderer is ${scenario.murderer}.`
}

changeScenario();
const verdict = declareMurderer();
console.log(verdict);

````
###  Expected to be Miss Scarlet...
