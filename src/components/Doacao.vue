<script setup>
import Botao from './Botao.vue';
import BolaNatal from "../assets/illustration.png";
let buttonLabel = "Fazer uma doação";
</script>
<template>
    <section>
        <img :src="BolaNatal" alt="Ilustração de mãos segurando uma bola de Natal">
        <div>
            <h2>Conectando generosidade ao redor dos mundos</h2>
            <p>Celebre a mágia do Natal de uma maneira especial! Descubra a plataforma que permite a doação de presentes
                significativos para aqueles que mais precisam. Faça parte do movimento e compartilhe o verdadeiro
                espírito da generosidade.</p>
            <Botao :label="buttonLabel" />
        </div>
    </section>
</template>

<style lang="scss" scoped>
section {
    display: flex;
    justify-content: space-around;
    align-items: center;
    gap: 2rem;
    margin: clamp(0rem, 3vw, 10rem);
    margin-block: 2rem;
    text-align: center;
    color: #121214;

    @media (max-width: 1023px) {
        flex-direction: column;
        padding: 0.5em;
        margin: clamp(0rem, 2vw, 4rem);
    }

}

div {
    text-align: left;
    max-width: 600px;
    width: 100%;

    button {
        margin: 0.5em 0;

        @media (max-width: 1023px) {
            margin: 0 auto;
        }
    }

    @media (max-width: 1023px) {
        max-width: 500px;
        width: 100%;
        text-align: center;
        padding: 0.5em;
    }


}

img {
    width: 25%;

    @media (max-width: 480px) {
        width: 70%;
    }
}

h2 {
    font-size: clamp(2rem, 3vw, 2.5rem);
    font-weight: 600;
    margin-block-end: 1.5rem;
}

p {
    font-size: clamp(1.125rem, 2vw, 1.5rem);
    line-height: 1.6;
    margin-block-end: 1.2em;
}
</style>