<template>
    <div class="calculator">
        <div class="screen">{{ current }}</div>
        <div @click="clear">C</div>
        <div @click="switchSign">+/-</div>
        <div @click="percent">%</div>
        <div @click="divide" class="operator">÷</div>
        <div @click="append($event.target.textContent)">7</div>
        <div @click="append($event.target.textContent)">8</div>
        <div @click="append($event.target.textContent)">9</div>
        <div @click="times" class="operator">x</div>
        <div @click="append($event.target.textContent)">4</div>
        <div @click="append($event.target.textContent)">5</div>
        <div @click="append($event.target.textContent)">6</div>
        <div @click="minus" class="operator">-</div>
        <div @click="append($event.target.textContent)">1</div>
        <div @click="append($event.target.textContent)">2</div>
        <div @click="append($event.target.textContent)">3</div>
        <div @click="add" class="operator">+</div>
        <div @click="append($event.target.textContent)" class="zero">0</div>
        <div @click="dot">.</div>
        <div @click="equal" class="operator">=</div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            current: '0',
        }
    },
    methods: {
        clear() {
            this.current = '0';
        },
        append(number) {
            if (this.operatorClicked) {
                this.current = '';
                this.operatorClicked = false;
            }
            if (this.current == '0') {
                if(number == '.'){
                    this.current = `${this.current}${number}`;
                }else{
                    this.current = number;
                }
            } else if (this.current != '0') {
                this.current = `${this.current}${number}`;

            } 
        },
        dot() {
            if (this.current.indexOf('.') === -1) {
                this.append('.');
            }
        },
        switchSign() {
            if (this.current != '0') {
                this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
            }
        },
        percent() {
            this.current = `${parseFloat(this.current) / 100}`;
        },
        setPrevious() {
            this.previous = this.current;
            this.operatorClicked = true;
        },
        divide() {
            this.operator = (a, b) => a / b;
            this.setPrevious();
        },
        times() {
            this.operator = (a, b) => a * b;
            this.setPrevious();
        },
        minus() {
            this.operator = (a, b) => a - b;
            this.setPrevious();
        },
        add() {
            this.operator = (a, b) => a + b;
            this.setPrevious();
        },
        equal() {
            this.current = `${Number(this.operator(
                parseFloat(this.previous),
                parseFloat(this.current)
            ).toFixed(10))}`;
            this.previous = null;
        }
    }
}
</script>
  
<style scoped>
.calculator {
    margin: 0 auto;
    width: 8em;
    font-size: 3em;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(1em, auto);
}

.screen {
    text-align: right;
    height: 2.5em;
    word-wrap: break-word;
    grid-column: 1 / 5;
    background-color: #333;
    color: white;
    overflow: auto;
    padding-right: 0.5em;

}

.zero {
    grid-column: 1 / 3;
    text-align: center;
}
.calculator div {
    border: 1px solid #999;
}
.calculator div:not([class]) {
    background-color: #F2F2F2;
    text-align: center;
}

.calculator div:hover {
    cursor: pointer;
}

.operator {
    background-color: orange;
    color: white;
    text-align: center;
}
</style>