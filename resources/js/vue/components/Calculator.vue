<template>
    <div class="calculator">
        <div class="screen">{{ current }}</div>
        <div>C</div>
        <div>+/-</div>
        <div>%</div>
        <div class="operator">÷</div>
        <div>7</div>
        <div>8</div>
        <div>9</div>
        <div class="operator">x</div>
        <div>4</div>
        <div>5</div>
        <div>6</div>
        <div class="operator">-</div>
        <div>1</div>
        <div>2</div>
        <div>3</div>
        <div class="operator">+</div>
        <div class="zero">0</div>
        <div>.</div>
        <div class="operator">=</div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            current: '0',
        }
    },
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