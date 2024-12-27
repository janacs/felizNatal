<script setup>
import { computed, reactive, ref } from "vue";
import NumberFlow, { NumberFlowGroup } from '@number-flow/vue';
import Presents from "../assets/presents.png";

let currentTime = ref(new Date());
const christmasTime = new Date("2024-12-25T00:00:00");
let difference = computed(() => christmasTime - currentTime.value);

const second = 1000;
const minute = second * 60;
const hour = minute * 60;
const day = hour * 24;

const remaining = reactive({
    Days: 0,
    Hours: 0,
    Minutes: 0,
    Seconds: 0,
});

let message = ref("");

const countdown = () => {
    if (difference.value > 0) {
        (remaining.Days = Math.floor(difference.value / day));
        (remaining.Hours = Math.floor((difference.value % day) / hour));
        (remaining.Minutes = Math.floor((difference.value % hour) / minute));
        (remaining.Seconds = Math.floor((difference.value % minute) / second));
    } else {
        message.value = "Feliz Natal";
    }
};


let updating = setInterval(() => {
    currentTime.value = new Date();
    countdown();

    if (Math.abs(difference.value) <= 1000) {
        difference.value = 0;
    }

    if (difference.value <= 0) {
        clearInterval(updating);
    }
}, 1000);
</script>

<template>
    <section>
        <h2>Tempo limitado</h2>
        <p>Nessa festas de fim de ano mande um presente para a pessoa amada e compartilhe a alegria do Natal.</p>
        <div>
            <NumberFlowGroup>
                <NumberFlow :trend="-1" suffix="d - " :value="remaining.Days" :format="{ minimumIntegerDigits: 1 }" />

                <NumberFlow :trend="-1" suffix="h - " :value="remaining.Hours" :format="{ minimumIntegerDigits: 1 }" />

                <NumberFlow :trend="-1" suffix="m - " :value="remaining.Minutes"
                    :format="{ minimumIntegerDigits: 2 }" />

                <NumberFlow :trend="-1" suffix="s" :value="remaining.Seconds" :format="{ minimumIntegerDigits: 1 }" />
            </NumberFlowGroup>
            <p v-if="message">{{ message }}</p>
        </div>
        <img :src="Presents" alt="">
    </section>
</template>

<style scoped lang="scss">
section {

    margin: clamp(0rem, 2vw, 10rem);
    padding: 0.5em;
    text-align: center;
}

h2 {
    font-size: clamp(2rem, 3vw, 2.5rem);
    font-weight: 600;
    margin-block-end: 1.5rem;
}

p {
    font-size: clamp(1.125rem, 2vw, 1.25rem);
    font-weight: 400;
    line-height: 1.4;
    margin-block-end: 1.125rem;
    width: fit-content;
    max-width: clamp(350px, 60vw, 500px);
    margin: auto;


    @media (min-width: 767px) {
        margin: auto;
        line-height: 1.5;
    }
}

div {
    padding: 0.25em;
    text-align: center;

}

number-flow-vue::part(number),
number-flow-vue::part(suffix) {
    color: #CD3C32;
    font-size: clamp(1.8rem, 5vw, 4rem);
    font-weight: 600;
    line-height: 1.7;

}

img {
    width: 40%;

    @media (max-width: 480px) {
        width: 100%;
    }

}
</style>