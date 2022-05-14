<template>
    <div>
        <h1>Prompt :</h1>
        <p class="card">{{ response.prompt }}</p>
        <h1>Response :</h1>
        <p class="card">{{ response.response }}</p>
    </div>
</template>

<script>
export default {
    name: "Response",
    props: {
        response : Object,
    },
}
</script>

<style scoped>
.card {
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.5);
    background-color: var(--secondary);
    margin: 10px;
    padding: 10px;
    text-align: left;
}
</style>