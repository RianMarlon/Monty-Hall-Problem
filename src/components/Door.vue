<template>
    <div class="door-area">
        <div class="door-frame" :class="{selected: selected && !open}" 
            @click="selected = !selected">
            <Gift v-if="open && hasGift"/>
        </div>
        <div class="door" :class="{open}"  @click="selected = !selected">
            <div class="door-number" :class="{ selected, open }">{{ number }}</div>
            <div class="door-knob" :class="{ selected, open }" 
                @click="open = true"></div>
        </div>
    </div>
</template>

<script>
    import Gift from './Gift';

    export default {
        name: "Door",
        components: { Gift },
        props: {
            number: {},
            hasGift: { type: Boolean }
        },
        data: function() {
            return {
                open: false,
                selected: false
            }
        }
    }
</script>

<style>
    :root {
        --door-border: 5px solid #A52A2A;
        --selected-border: 5px solid #FF0;
    }

    .door-area {
        position: relative;
        width: 250px;
        height: 310px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-bottom: 10px solid #AAA;

        margin-bottom: 60px;
        margin-left: 30px;
        margin-right: 30px;
    }

    .door-frame {
        position: absolute;
        height: 300px;
        width: 220px;
        border-top: var(--door-border);
        border-left: var(--door-border);
        border-right: var(--door-border);

        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        align-self: center;
    }

    .door {
        position: absolute;
        display: flex;
        flex-direction: column;
        justify-self: center;
        align-items: center;
        top: 5px;
        height: 295px;
        width: 210px;
        background-color: #D2691E;
        padding: 20px;
        font-size: 2.5rem;
    }

    .door-frame.selected {
        border-top: var(--selected-border);
        border-left: var(--selected-border);
        border-right: var(--selected-border);
    }

    .door > .door-number {
        margin-top: 20px;
    }

    .door > .door-knob {
        height: 20px;
        width: 20px;
        border-radius: 10px;
        background-color: brown;
        align-self: flex-start;
        margin-top: 60px;
    }

    .door > .door-number.selected {
        color: #FF0;
    }

    .door > .door-knob.selected {
        background-color: #FF0;
    }

    .door.open {
        background-color: #0007;
    }

    .door .door-number.open {
        display: none;
    }

    .door .door-knob.open {
        display: none;
    }

</style>