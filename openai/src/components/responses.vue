<template>
    <div>
        <h1>Responses :</h1>
        <loading></loading>
        <ul v-for="response in responses" v-bind:key="response.date" class="cardResponses">
            <response :response="response"></response>
        </ul>
    </div>
</template>

<script>
import Response from './response.vue';
import loading from './loading.vue';

export default {
    name: "Responses",
    data() {
        return {
            isLoading: false,
        };
    },
    components: {
        Response,
        loading
    },
    props: {
        responses : Array,
    },
}
</script>

<style scoped>
.cardResponses {
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.5);
    background-color: var(--primary);
    margin: 20px;
    padding: 10px;
    border-radius: 4px;
}
</style>
