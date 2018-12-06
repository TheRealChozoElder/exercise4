<template>
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width">
            <title>RPS game</title>
        </head>
        <body id = "app">
            <script src="https://npmcdn.com/vue/dist/vue.js"></script>
            <script src="app.js"></script>
            <section>
                <!--buttons used for user-->
                <button id="rock" v-on:click="choose('rock')">Rock</button>
                <button id="paper" v-on:click="choose('paper')">Paper</button>
                <button id="scissors" v-on:click="choose('scissors')">Scissors</button>

                <!--paragraphs used to display stuff-->
                <p id="credit">Credits: {{ userCredit }}</p>
                <p id="rounds">Round: {{ round }}</p>
                <p class="userChoice" v-bind:class="computedUser">User Choice: </p>
                <p class="compChoice" v-bind:class="computedRand">Comp Choice: </p>
                <p id="result">Result: </p>
                <p id="high_score">High Score: </p>

                <!--            <button id='five' onclick="bet()">Five credits</button>
                            <button id="ten" onclick="bet()">Ten</button>
                            <button id='double' onclick="bet()">Double last bet</button>-->
            </section>
        </body>
    </html>
</template>

<script>
export default {
    name: '#app',
    data() {
        return {
            function() {
                return {userChoice: null,
                    compChoice: null,
                    userCredit: 100,
                    round: 0
                };
            }
        };
    },
    methods: {
        //This is used to find the computer choice then takes it and runs compare
        choose: function (pick) {
            this.userChoice = pick;
            picks = ['rock', 'paper', 'scissors'];
            this.compChoice = picks[Math.random() * picks.length];
            this.scoreCreds();
        },
        scoreCreds: function () {
            if (this.userChoice === 'rock') {
                if (this.compChoice === 'paper') {
                    document.getElementById("result").innerHTML = 'Computer wins';
                    this.userCredit--;
                    this.round++;
                } else if (this.compChoice === 'scissors') {
                    document.getElementById("result").innerHTML = 'User wins';
                    this.userCredit++;
                    this.round++;
                } else {
                    document.getElementById("result").innerHTML = 'Draw';
                    this.round++;
                }
            } else if (this.userChoice === 'paper') {
                if (this.compChoice === 'rock') {
                    document.getElementById("result").innerHTML = 'User wins';
                    this.userCredit++;
                    this.round++;
                } else if (this.compChoice === 'scissors') {
                    document.getElementById("result").innerHTML = 'Computer wins';
                    this.userCredit--;
                    this.round++;
                } else {
                    document.getElementById("result").innerHTML = 'Draw';
                    this.round++;
                }
            } else {
                if (this.compChoice === 'rock') {
                    document.getElementById("result").innerHTML = 'Computer wins';
                    this.userCredit--;
                    this.round++;
                } else if (this.compChoice === 'paper') {
                    document.getElementById("result").innerHTML = 'User wins';
                    this.userCredit++;
                    this.round++;
                } else {
                    document.getElementById("result").innerHTML = 'Draw';
                    this.round++;
                }
            }
        }
    },
    computed: {
        computedUser: function () {
            return {
                "rock": this.userChoice === "rock",
                "paper": this.userChoice === "paper",
                "scissors": this.userChoice === "scissors"
            };
        },
        computedRand: function () {
            return {
                "rock": this.compChoice === "rock",
                "paper": this.compChoice === "paper",
                "scissors": this.compChoice === "scissors"
            };
        }
    }
}
</script>

<style>
   .text-center {
    text-align: center;
}

.wins {
    width: 80%;
    color: black;
    height: 40px;
    background-color: #eee;
    margin: auto;
    transition: width 1000ms;
}

.controls, .log {
    margin-top: 30px;
    text-align: center;
    padding: 10px;
    border: 1px solid #ccc;
    box-shadow: 0px 3px 6px #ccc;
}

.turn {
    margin-top: 20px;
    margin-bottom: 20px;
    font-weight: bold;
    font-size: 22px;
}

.log ul {
    list-style: none;
    font-weight: bold;
    text-transform: uppercase;
}

.log ul li {
    margin: 5px;
}

.log ul .player-turn {
    color: green;
    background-color: #aaffb0;
}

.log ul .computer-turn {
    color: red;
    background-color: #ffc0c1;
}

.log ul .tie-turn {
  color: blue;
  background-color: #e4e8ff;
}

button {
    font-size: 20px;
    background-color: #eee;
    padding: 12px;
    box-shadow: 0 1px 1px black;
    margin: 10px;
}

#start-game {
    background-color: #e4e8ff;
}

#start-game:hover {
  background-color: #687eff;
}

#rock {
    background-color: #ff7367;
}

#rock:hover {
    background-color: #ff3f43;
}

#paper {
    background-color: #ffaf4f;
}

#paper:hover {
    background-color: #ff9a2b;
}

#scissors {
    background-color: #aaffb0;
}

#scissors:hover {
    background-color: #76ff7e;
}

#restart {
    background-color: #ffffff;
}

#restart:hover {
    background-color: #c7c7c7;
}
</style>
