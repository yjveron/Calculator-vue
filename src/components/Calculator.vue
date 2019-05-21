<template>
    <div id="calculator">
        <input type="text" class="input" v-model="equation" @keyup.enter="compute()" @keyup.esc="reset()"><br>
        <div class="buttons">
            <button @click="reset()">C</button>
            <button @click="buildEquation()">+/-</button> <!-- IDK PA HOW I PLAN ON DOING THIS -->
            <button @click="buildEquation('%')">%</button>
            <button @click="buildEquation('/')">/</button>
            <button @click="buildEquation(7)">7</button>
            <button @click="buildEquation(8)">8</button>
            <button @click="buildEquation(9)">9</button>
            <button @click="buildEquation('*')">x</button>
            <button @click="buildEquation(4)">4</button>
            <button @click="buildEquation(5)">5</button>
            <button @click="buildEquation(6)">6</button>
            <button @click="buildEquation('-')">-</button>
            <button @click="buildEquation(1)">1</button>
            <button @click="buildEquation(2)">2</button>
            <button @click="buildEquation(3)">3</button>
            <button @click="buildEquation('+')">+</button>
            <button @click="buildEquation(0)">0</button>
            <button @click="buildEquation('.')">.</button>
            <button class="equals" @click="compute()">=</button><br><br>
        </div>
        {{answer}}
    </div>
</template>


<script>
export default {
    name: 'Calculator',
    data() {
        return {
            equation: '',
            equationRight: '',
            answer: 0
        }
    },
    methods: {
        buildEquation(val){
            // IF INPUT IS + - * / REMOVE FIRST INPUT MOVE TO TOP
            // IF BEGINNING OF STRING, DO NOT ACCEPT + - * /
            // CHECK IF + - * / HAS BEEN CLICKED
            this.equation += val;
        },
        compute(){
            // IF END OF STRING IS + - * / PRESENT ERROR MESSAGE
            this.answer = eval(this.equation)
            // HOW TO MAKE IT SO THAT THE ANSWER REPLACES EQUATION IN THE INPUT BOX
        },
        reset(){
            this.equation = '';
            this.answer = 0;
        }
    }
}
</script>

<style scoped>

#calculator {
    width: 300px;
    height: 100%;
    background-color: silver;
    margin: 0 auto;
    border-radius: 5px;
}

.input {
    height: 100px;
    width: 100%;
    text-align: right;
    font-size: 3rem;
    padding-top: 40px;
    background-color: #202020;
    border: none;
    color: white;
    text-overflow: clip;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 75px);
    grid-template-rows: repeat(5, 75px);
}

.buttons button {
    border: 0.2px solid gray;
    background: linear-gradient(180deg, rgba(242,242,242,1) 0%, rgba(233,233,233,1) 50%, rgba(218,218,218,1) 100%);
}

.buttons :nth-child(17) {
    grid-column: span 2;
}

.buttons :nth-child(4n),
.buttons .equals {
    background: none;
    background-color: #F98910;
    color: white;
}




</style>
