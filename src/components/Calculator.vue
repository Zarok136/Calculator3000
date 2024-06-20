<script setup>
import { ref } from 'vue'

const inputValue = ref('')

// Function pour ajouter une valeur à l'input
const updateInputValue= (value) => {
    inputValue.value += value;
}

//fontion pour calculer le résultat
const calculateResult = () => {
    try{inputValue.value = eval(inputValue.value)}
    // Si l'expression est invalide, on affiche "ERROR" et on log l'erreur
catch (error) {
    console.error("Invalid expression", error);
    inputValue.value = "Error";
  }
}

// fonction pour supprimer le dernier caractère
const deleteLastCharacter = () => {
    inputValue.value = inputValue.value.slice(0, -1);
}

// fonction pour supprimer le dernier caractère avec la touche delete du clavier
const handleKeydown = (event) => {
    if (event.key === "Delete") {
        deleteLastCharacter();
    }
}

</script>

<template>
    <h1>Bienvenue sur Calculator 3000</h1>
    <div class="calculator" @keydown="handleKeydown">
    <!-- L'input est désactivé par défaut pour permettre de ne pas écrire dedans (evitons les injections) -->
        <input type="text" placeholder="0" v-model="inputValue" disabled/>
        <button id="7" @click="updateInputValue('7')">7</button>
        <button id="8" @click="updateInputValue('8')">8</button>
        <button id="9" @click="updateInputValue('9')">9</button>
        <button id="DEL" @click="deleteLastCharacter">DEL</button>
        <button id="4" @click="updateInputValue('4')">4</button>
        <button id="5" @click="updateInputValue('5')">5</button>
        <button id="6" @click="updateInputValue('6')">6</button>
        <button id="+" @click="updateInputValue('+')">+</button>
        <button id="1" @click="updateInputValue('1')">1</button>
        <button id="2" @click="updateInputValue('2')">2</button>
        <button id="3" @click="updateInputValue('3')">3</button>
        <button id="-" @click="updateInputValue('-')">-</button>
        <button id="." @click="updateInputValue('.')">.</button>
        <button id="0" @click="updateInputValue('0')">0</button>
        <button id="/" @click="updateInputValue('/')">/</button>
        <button id="x" @click="updateInputValue('*')">x</button>
        <button class="parenthesis" @click="updateInputValue('(')">(</button>
        <button class="parenthesis" @click="updateInputValue(')')">)</button>
        <button id="Reset" class="bottomCalc" @click="inputValue = ''">Reset</button>
        <button id="Equal" class="bottomCalc" @click="calculateResult">=</button>
    </div>
</template>

<style scoped>

input{
    background-color: #d1d1d1;
    color: #252d46;
}

h1{
    margin: auto;
    padding: 1rem;
    text-align: center;
}

.calculator{
    margin-top: 3rem;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
    background-color: #252d46;
    border-radius: 1rem;
    padding: 1rem;
}

.bottomCalc{
    grid-column: span 2;
}

input{
    grid-column: span 4;
    padding: 10px;
    font-size: 1.5em;
}

button{
    padding: 10px;
    font-size: 1.5em;
    border: 1px solid black;
    background-color: #d1d1d1;
    border: none;
    border-radius: 1rem;
}

button:active{
    transform: scale(0.95);
    box-shadow: inset 0 0 0.5rem #000000e3;
}

#DEL, #Reset{
    background-color: #647297;
    color: #d1d1d1;
}

#Equal{
    background-color: #f75353;
    color: #d1d1d1;
}

.parenthesis{
    grid-column: span 2;
}

@media screen and (max-width: 600px)
{

.calculator{
    margin: 1rem;
    padding: 2rem;
}    

}
</style>
