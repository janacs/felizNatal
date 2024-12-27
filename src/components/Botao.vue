<script setup>
defineProps({
    label: String
})

</script>

<template>
    <button type="button">{{ label }}</button>
</template>

<style scoped lang="scss">
button {
    font-family: 'Roboto', sans-serif;
    font-size: clamp(1rem, 2vw, 1.125rem);
    text-transform: uppercase;
    text-align: center;
    background-color: #CD3C32;
    color: #fff;
    border-radius: 0.25rem;
    border: none;
    padding: 0.5em 1.5em;
    transition: background-color ease 0.5s, transform ease 0.3s;
    cursor: pointer;

    &:active {
        transform: scale(0.98);
    }

    &:focus-visible {
        outline: 2px solid #CD3C32;
        outline-offset: 2px;
    }

    @media (max-width: 480px) {
        padding: 0.5em 3em;
    }

    @media (min-width: 1024px) {
        &:hover {
            background-color: #fff;
            color: #CD3C32;
            border: 2px solid #CD3C32;
        }

    }
}
</style>