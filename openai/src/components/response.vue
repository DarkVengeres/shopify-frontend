<template>
    <div>
        <h1>Prompt :</h1>
        <p>{{ response.prompt }}</p>
        <h1>Response :</h1>
        <p>{{ response.response }}</p>
    </div>
</template>

<script>
export default {
    name: "Response",
    props: {
        response : Object,
    },
    created() {
        console.log(this.response);
    },
}
</script>