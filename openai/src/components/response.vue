<template>
    <div>
        <div class="promptHead">
            <h2>Prompt :</h2>
            <p class="type" :id="response.id"> {{response.promptType }} </p>
        </div>
        <p class="card">{{ response.prompt }}</p>
        <h2>Response :</h2>
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
    font-family: "M PLUS Code Latin";
}

.type {
    font-weight: bold;
    border: 3px solid;
    box-sizing: border-box;
    border-radius: 4px;
    padding: 5px;
    height: 30px;
    margin: 10px;
    color: var(--textTag);
}

.promptHead {
    display: flex;
    justify-content: space-between;
}


</style>