<template>
    <button :class="mode">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        props: ['mode']
    }
</script>

<style scoped>
   button {
        padding: 0.6rem 0.7rem;
        border-radius: 3px;
        border: none;
        background: #830041;
        color: white;
        font-family: 'Roboto', sans-serif;
        font-weight: 500;
    }

   button:hover {
        cursor: pointer;
        background: #6b0036;
    }

    button:focus {
        outline-style: none;
    }

   .flat {
        border: 1px solid  #830041;
        background-color: transparent;
        color: #830041;
    }

    .flat:hover {
        background-color:  #fdeff7;
    }
</style>