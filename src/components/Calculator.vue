<template>
    <div id="calculator">
        <div class="usedEquation">{{usedEquation}}</div>
        <input type="text" class="input" v-model="equation" @keyup.enter="compute()" @keyup.esc="reset()" ><br>
        <div class="buttons">
            <button @click="reset()">C</button>
            <button @click="alert('I am buggy')">+/-</button>
            <button v-for="(button, index) in buttons" v-bind:key="index" @click="buildEquation(button.content)">{{button.content}}</button>
            <button class="equals" @click="compute()">=</button><br><br>
        </div>
    </div>
</template>


<script>
export default {
    name: 'Calculator',
    data() {
        return {
            usedEquation: '',
            answer: 0,
            buttons: [
                {content: '%'},{content: '/'},
                {content: 7},{content: 8},{content: 9},{content: '*'},
                {content: 4},{content: 5},{content: 6},{content: '-'},
                {content: 1},{content: 2},{content: 3},{content: '+'},
                {content: 0}, {content: '.'},
            ]
        }
    },
    props: [
        'equation'
    ],
    methods: {
        buildEquation(val){
            // IF INPUT IS + - * / REMOVE FIRST INPUT MOVE TO TOP
            // IF BEGINNING OF STRING, DO NOT ACCEPT + - * /
            // CHECK IF + - * / HAS BEEN CLICKED
            this.equation += val;
        },
        compute(){
            // IF END OF STRING IS + - * / PRESENT ERROR MESSAGE
            this.usedEquation = this.equation
            this.answer = eval(this.equation)
            this.equation = this.answer
            this.$emit('compute', this.usedEquation)
        },
        reset(){
            this.usedEquation = '';
            this.equation = '';
            this.answer = 0;
        },
        alert(val){
            alert(val)
        }
    },
}
</script>

<style scoped>

#calculator {
    width: 300px;
    height: 100%;
    background-color: silver;
    border-radius: 5px;
}

.usedEquation,
.input {
    width: 100%;
    background-color: #202020;  
    text-align: right;
    border: none;
}

.usedEquation {
    height: 30px;
    color: lightgrey;
    padding-top: 10px;
}

.input {
    height: 70px;
    color: white;
    font-size: 3rem;
    padding-top: 30px;
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
