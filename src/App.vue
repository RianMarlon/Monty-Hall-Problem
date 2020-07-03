<template>
    <div id="app">
        <h1>Monty Hall Problem</h1>

        <div class="form">
            <div v-if="!started">
                <label for="portsAmount">How many doors?</label>
                <input type="number" id="portsAmount" size="13"
                    v-model.number="portsAmount">
            </div>

            <div v-if="!started">
                <label for="selectedPort">Which door has the prize?</label>
                <input type="number" id="selectedPort" size="13"
                    v-model.number="selectedPort">
            </div>
            
            <button @click="started = true" v-if="!started">Start</button>
            <button @click="started = false" v-if="started">Restart</button>
        </div>

        <div class="doors" v-if="started">
            <div v-for="i in portsAmount" :key="i">
                <Door :number="i" :hasGift="i == selectedPort" />
            </div>
        </div>
    </div>
</template>

<script>
    import Door from './components/Door';

    export default {
        name: "App",
        components: { Door },
        data: function() {
            return {
                started: false,
                portsAmount: 3,
                selectedPort: null
            }
        }
    }
</script>

<style>

    * {
        box-sizing: border-box;
        font-family: 'Montserrat', sans-serif;
    }

    body {
        background: linear-gradient(to right, rgb(21, 153, 87), rgb(21, 87, 153));
    }

    #app {
        display: flex;
        flex-direction: column;
        align-items: center;
        color: #FFF;

        font-size: 1.5rem;
    }

    #app h1 {
        font-size: 2.1rem;
        padding: 20px;
        border: 1px solid #000;
        background-color: #0004;
        margin-bottom: 60px;
    }

    .form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-bottom: 40px;
    }

    .form > div, .form button {
        margin-bottom: 1.5rem;
        font-size: 1.5rem;
    }

    .form input {
        margin-left: 1rem;
        font-size: 1.5rem;
    }

    .doors {
        align-self: stretch;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
    }

</style>
