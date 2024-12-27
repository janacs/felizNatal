<script setup>
import logo from '../assets/feliz-Natal.png';
import loja from '../assets/shop.png';
import Botao from './Botao.vue';
let buttonLabel = "Fazer doação"
</script>

<template>
    <header>
        <div>
            <img class="logo" :src="logo" alt="Logo com Papai Noel com os dizeres 'Feliz Natal'">
            <h1>Uma <strong>plataforma de doação</strong> para espalhar alegria</h1>
            <p>Nessas festas de fim de ano mande um presente para a pessoa amada e compartilhe a alegria do Natal.</p>
            <Botao :label="buttonLabel" />
        </div>
        <img :src="loja" alt="ilustração da frente uma loja em época de Natal ">
    </header>
</template>

<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-around;
    align-items: center;
    gap: 2rem;
    margin-block-end: 2rem;
    padding: clamp(0rem, 3vw, 10rem);
    text-align: center;
    color: #121214;
    background-color: #FFE9E8;

    @media (max-width: 1023px) {
        flex-direction: column;
        padding: 0.5em;
    }
}

div {
    text-align: left;
    max-width: 550px;
    width: 100%;
    padding: 0.5em;

    @media (max-width: 1023px) {
        text-align: center;
    }
}

.logo {
    width: 30%;
}

h1 {
    font-size: clamp(2rem, 3vw, 2.5rem);
    margin-block: 1.125rem;

    strong {
        color: #CD3C32;
    }
}

p {
    font-size: clamp(1.125rem, 2vw, 1.5rem);
    line-height: 1.6;
    margin-block-end: 1.2em;
}

img {
    width: 30%;

    @media (max-width: 1023px) {
        width: 60%;
    }
}
</style>