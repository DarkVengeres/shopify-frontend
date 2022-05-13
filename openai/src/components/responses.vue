<template>
    <div>
        <h1>Responses :</h1>
        <div>
            <ul v-for="response in responses" v-bind:key="response.date">
                <response :response="response"></response>
            </ul>
        </div>
    </div>
</template>

<script>
import Response from './response.vue';

export default {
    name: "Responses",
    components: {
        Response
    },
    props: {
        responses : Array,
    },
}
</script>
