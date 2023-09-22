---
title: "JSON Game Artifact Representations"
seoTitle: "computational thinking and game design"
datePublished: Wed Mar 08 2023 23:57:49 GMT+0000 (Coordinated Universal Time)
cuid: clf0cbez3000409mn0y6p7g9g
slug: json-game-artifact-representations
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678319764248/39b27925-6861-41fd-a98f-cd0397dc6187.jpeg
tags: education, game-design, computational-thinking

---

In this article, I describe JSON variables in a digital game that middle-school children in India have developed using the WearableLearning educational technology. [Early Research Scholar Program](https://sites.google.com/umass.edu/ersp-cics/home) (ERSP) researchers and other educational researchers interested in studying student game design for [computational thinking](https://cultureos.hashnode.dev/computational-thinking) may find this valuable.

In August 2022, young learners from Jammikunta, India, from grades 6 & 7, named this game "hackers". This digital "artifact" is extracted as a JSON to perform [DFS](https://github.com/tinkerpop/gremlin/wiki/Depth-First-vs.-Breadth-First) traverse through states, transitions and connections (finite-state machines). This enables educational researchers to identify unique learner cultural attributes, which can then be reused to create an engaging learning experience for learners from diverse cultural backgrounds.

### First, what does this represent?

In my previous article, I explain why [computational thinking](https://cultureos.hashnode.dev/computational-thinking) is an essential skill for success in the modern world (Wing, 2006). In the education paradigm, game design is a popular way to teach 21st-century literacy skills such as computational thinking to learners of all ages. Using the WearableLearning educational game design platform, children program their games using a drag-drop NoCode interface. For educational research purposes, digital game representations are extracted as JSONs. This particular JSON is a game that middle school children in India created in August 2022. This file is a direct cultural manifestation of the learners' cultural pockets of knowledge, which shape their computational thinking and participatory learning experiences.

Here is a general breakdown of the different components in the JSON file (scroll to the bottom for full prettified JSON):

```json
"gameId": "hackers",
    "teamCount": 2,
    "playersPerTeam": 3,
    "username": { "REDACTED"
      "usernameId": "REDACTED"
    },
    "visibility": true,
    "stateIdCount": 11,
    "transitionIdCount": 10,
    "connectionIdCount": 11,
    "dataLog": false,
    "states": [
```

* gameId: This is the name of the game, "hackers".
    
* teamCount: Shows number of teams in the game, 2.
    
* playersPerTeam: Shows number of players per team, 3.
    
* visibility: A boolean value that indicates if this game is public or private to the user.
    
* stateIdCount: Number of states in the game, 11.
    
* transitionIdCount: This field specifies the number of transitions in the game, 10.
    
* connectionIdCount: This is the number of connections in the game, 11.
    
* dataLog: Another boolean, I think this specifies if the game data is being logged or not.
    

```json
{
        "stateType": "START_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_start",
        "game": "hackers",
        "stateType": "START_STATE",
        "positionX": 0.0,
        "positionY": 68.501,
        "inputConnections": [
          
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_1"
        ],
        "globalVariables": [
          
        ]
```

* states: An array containing information about the different states in the game.
    
    * stateType: Looks like the type of state. "START\_STATE" means that it is the starting state.
        
    * stateId: A unique identifier for the state.
        
    * positionX and positionY: Think of this as (x,y) coordinates on game editor canvas.
        
    * inputConnections: Array with many objects - not visible in this demonstration.
        
    * outputConnections: Array with many objects - not visible in this demonstration.
        
    
    ```json
    {
            "stateType": "OUTPUT_STATE",
            "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_1",
            "game": "hackers",
            "stateType": "OUTPUT_STATE",
            "positionX": 24.5073,
            "positionY": 264.074,
            "inputConnections": [
              "dc5d6e5c0ffd6d1cd249286ced098382_connection_1"
            ],
            "outputConnections": [
              "dc5d6e5c0ffd6d1cd249286ced098382_connection_2"
            ],
            "description": "State",
            "displayText": {
              "Game Wide": "welcome to our game this is a game of hackers  press any button to continune\n"
            },
    ```
    
* description: Specifies the description of the state.
    
* displayText: This is a label that contains learner-defined text:
    
    *"welcome to our game this is a game of hackers press any button to continune\\n"* - indicating that it is a welcome message for the game players.
    

```json
connections": [
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_1",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_start",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_1",
        "backwardsLoop": false,
        "transition": null
```

* connectionId: A unique identifier for this connection.
    
* connectionFrom: ID of the state that this connection starts from.
    
* connectionTo: ID of the state that the connection goes to.
    
* backwardsLoop: Boolean showing if this connection creates a backwards loop in the game. Here, it is false - meaning it does not loop back.
    
* transition: This variable is null. No clue what that means 🤨.
    

```json
"transitions": [
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_1",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_2",
        "activeTransitions": {
          "Game Wide": "Button Press"
        },
        "singleButtonPresses": {
          "Game Wide": {
            "button1": true,
            "button1Label": "Red Button",
            "button2": true,
            "button2Label": "Green Button",
            "button3": true,
            "button3Label": "Blue Button",
            "button4": true,
            "button4Label": "Black Button"
          }
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_1_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_1",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      }
```

* transitionId: A unique identifier for this transition.
    
* connection: ID of the connection that this transition is associated with.
    
* activeTransitions: Don't know what that means 🤨.
    
* singleButtonPresses: This is an object, nested. Possibly represents what color needs to be pressed.
    
* sequenceButtonPresses: This is a sequence-based press that triggers the action.
    
* keyboardInputs: Indicates a keyboard input, which triggers this transition.
    
* timerDurations: Indicates if this is a timed event, which will trigger this transition.
    
* randoms: Randomly picks one transition mode. Need more clarity on how this works.
    
* globalVariables: Indicates if any global variables are associated with this transition.
    

Many repetitive variables have been omitted.

---

---

Full JSON:

```json
{
    "gameId": "hackers",
    "teamCount": 2,
    "playersPerTeam": 3,
    "username": { "REDACTED"
      "usernameId": "REDACTED"
    },
    "visibility": true,
    "stateIdCount": 11,
    "transitionIdCount": 10,
    "connectionIdCount": 11,
    "dataLog": false,
    "states": [
      {
        "stateType": "START_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_start",
        "game": "hackers",
        "stateType": "START_STATE",
        "positionX": 0.0,
        "positionY": 68.501,
        "inputConnections": [
          
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_1"
        ],
        "globalVariables": [
          
        ]
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_1",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 24.5073,
        "positionY": 264.074,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_1"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_2"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "welcome to our game this is a game of hackers  press any button to continune\n"
        },
        "pictureOutputs": {
          "Game Wide": {
            "url": "https://planetsportsandtrophies.com/wp-content/uploads/2022/01/JR34-TY177A-1-300x300.jpg",
            "scale": 72
          }
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_10",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 0.0,
        "positionY": 627.502,
        "inputConnections": [
          
        ],
        "outputConnections": [
          
        ],
        "description": "State",
        "displayText": {
          
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_11",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 489.5,
        "positionY": 867.029,
        "inputConnections": [
          
        ],
        "outputConnections": [
          
        ],
        "description": "State",
        "displayText": {
          
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_2",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 182.046,
        "positionY": 83.4938,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_2",
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_7"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_3",
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_4"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "calculate 9+6=?"
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_3",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 229.001,
        "positionY": 247.997,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_3"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_5"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "great job you go to next question press any button to continue"
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_4",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 544.525,
        "positionY": 44.5562,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_4"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_7"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "oops wrong answer try again press any button"
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_5",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 86.4743,
        "positionY": 515.594,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_5",
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_9"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_6",
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_8"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "19 + 13 =?"
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_6",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 60.0,
        "positionY": 801.0,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_6"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_10"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "good job you go to next question press any button to continue"
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_7",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 458.499,
        "positionY": 668.918,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_8"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_9"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "oops wrong answer try again press any button to continue"
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_8",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 316.495,
        "positionY": 820.566,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_10"
        ],
        "outputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_11"
        ],
        "description": "State",
        "displayText": {
          "Game Wide": "999 + 99 -10 -8 =?"
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      },
      {
        "stateType": "OUTPUT_STATE",
        "stateId": "dc5d6e5c0ffd6d1cd249286ced098382_state_9",
        "game": "hackers",
        "stateType": "OUTPUT_STATE",
        "positionX": 755.398,
        "positionY": 779.047,
        "inputConnections": [
          "dc5d6e5c0ffd6d1cd249286ced098382_connection_11"
        ],
        "outputConnections": [
          
        ],
        "description": "State",
        "displayText": {
          
        },
        "pictureOutputs": {
          
        },
        "soundOutputs": {
          
        },
        "videoOutputs": {
          
        },
        "globalVariables": {
          
        }
      }
    ],
    "connections": [
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_1",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_start",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_1",
        "backwardsLoop": false,
        "transition": null
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_10",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_6",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_8",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_9"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_11",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_8",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_9",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_10"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_2",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_1",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_2",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_1"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_3",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_2",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_3",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_2"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_4",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_2",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_4",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_3"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_5",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_3",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_5",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_4"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_6",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_5",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_6",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_5"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_7",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_4",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_2",
        "backwardsLoop": true,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_6"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_8",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_5",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_7",
        "backwardsLoop": false,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_7"
      },
      {
        "connectionId": "dc5d6e5c0ffd6d1cd249286ced098382_connection_9",
        "game": "hackers",
        "connectionFrom": "dc5d6e5c0ffd6d1cd249286ced098382_state_7",
        "connectionTo": "dc5d6e5c0ffd6d1cd249286ced098382_state_5",
        "backwardsLoop": true,
        "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_8"
      }
    ],
    "transitions": [
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_1",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_2",
        "activeTransitions": {
          "Game Wide": "Button Press"
        },
        "singleButtonPresses": {
          "Game Wide": {
            "button1": true,
            "button1Label": "Red Button",
            "button2": true,
            "button2Label": "Green Button",
            "button3": true,
            "button3Label": "Blue Button",
            "button4": true,
            "button4Label": "Black Button"
          }
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_1_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_1",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_10",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_11",
        "activeTransitions": {
          "Game Wide": "Text Entry"
        },
        "singleButtonPresses": {
          
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          "Game Wide": {
            "keyboardInputId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_10_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_10",
            "scope": "Game Wide",
            "keyboardInputs": [
              "1080"
            ]
          }
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_10_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_10",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_2",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_3",
        "activeTransitions": {
          "Game Wide": "Text Entry"
        },
        "singleButtonPresses": {
          
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          "Game Wide": {
            "keyboardInputId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_2_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_2",
            "scope": "Game Wide",
            "keyboardInputs": [
              "15"
            ]
          }
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_2_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_2",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_3",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_4",
        "activeTransitions": {
          "Game Wide": "Text Entry"
        },
        "singleButtonPresses": {
          
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          "Game Wide": {
            "keyboardInputId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_3_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_3",
            "scope": "Game Wide",
            "keyboardInputs": [
              ""
            ]
          }
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_3_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_3",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_4",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_5",
        "activeTransitions": {
          "Game Wide": "Button Press"
        },
        "singleButtonPresses": {
          "Game Wide": {
            "button1": true,
            "button1Label": "Red Button",
            "button2": true,
            "button2Label": "Green Button",
            "button3": true,
            "button3Label": "Blue Button",
            "button4": true,
            "button4Label": "Black Button"
          }
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_4_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_4",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_5",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_6",
        "activeTransitions": {
          "Game Wide": "Text Entry"
        },
        "singleButtonPresses": {
          
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          "Game Wide": {
            "keyboardInputId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_5_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_5",
            "scope": "Game Wide",
            "keyboardInputs": [
              "32"
            ]
          }
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_5_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_5",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_6",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_7",
        "activeTransitions": {
          "Game Wide": "Button Press"
        },
        "singleButtonPresses": {
          "Game Wide": {
            "button1": true,
            "button1Label": "Red Button",
            "button2": true,
            "button2Label": "Green Button",
            "button3": true,
            "button3Label": "Blue Button",
            "button4": true,
            "button4Label": "Black Button"
          }
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_6_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_6",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_7",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_8",
        "activeTransitions": {
          "Game Wide": "Text Entry"
        },
        "singleButtonPresses": {
          
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          "Game Wide": {
            "keyboardInputId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_7_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_7",
            "scope": "Game Wide",
            "keyboardInputs": [
              ""
            ]
          }
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_7_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_7",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_8",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_9",
        "activeTransitions": {
          "Game Wide": "Button Press"
        },
        "singleButtonPresses": {
          "Game Wide": {
            "button1": true,
            "button1Label": "Red Button",
            "button2": true,
            "button2Label": "Green Button",
            "button3": true,
            "button3Label": "Blue Button",
            "button4": true,
            "button4Label": "Black Button"
          }
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_8_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_8",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      },
      {
        "transitionId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_9",
        "game": "hackers",
        "connection": "dc5d6e5c0ffd6d1cd249286ced098382_connection_10",
        "activeTransitions": {
          "Game Wide": "Button Press"
        },
        "singleButtonPresses": {
          "Game Wide": {
            "button1": true,
            "button1Label": "Red Button",
            "button2": true,
            "button2Label": "Green Button",
            "button3": true,
            "button3Label": "Blue Button",
            "button4": true,
            "button4Label": "Black Button"
          }
        },
        "sequenceButtonPresses": {
          
        },
        "keyboardInputs": {
          
        },
        "timerDurations": {
          
        },
        "randoms": {
          
        },
        "globalVariables": {
          "Game Wide": {
            "globalVariableId": "dc5d6e5c0ffd6d1cd249286ced098382_transition_9_game_wide",
            "transition": "dc5d6e5c0ffd6d1cd249286ced098382_transition_9",
            "scope": "Game Wide",
            "globalVariableInputModifiers": [
              
            ]
          }
        }
      }
    ]
  }
```

---

### References

Wing, J. M. (2006). Computational thinking. *Communications of the ACM*, *49*(3), 33-35.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678333876533/0a91c03a-498b-43fc-810e-ff74574d7cc1.jpeg align="center")