<template>
    <div>
        <transition-group name="slide-down">
            <li v-for="response in responses" v-bind:key="response.id" class="cardResponses">
                <response :response="response"></response>
            </li>
        </transition-group>
    </div>
</template>

<script>
import Response from './response.vue';

export default {
    name: "Responses",
    components: {
        Response,
    },
    props: {
        responses : Array,
    },

    created() {
        this.$root.$refs.responses = this;
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

.slide-down-enter-active,
.slide-down-move{
  transition: all 0.5s;
}
.slide-down-enter {
  transform: translateY(-10px);
  opacity: 0;
}
li {
    list-style: none;
}

/* Make animation when responses is deleted */
.slide-down-leave-active {
  transition: all 0.5s;
}
.slide-down-leave {
  transform: translateY(10px);
  opacity: 0;
}


</style>
