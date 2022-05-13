<template>
    <form @submit.prevent="submitForm" id="promptForm">
        Prompt
        <textarea type="text" id="promptText" required v-model="prompt"></textarea>
        <button type="submit">Submit</button>
    </form>
</template>

<script>
// import API from '@/utility/API.js';

export default {
    name: 'PromptForm',
    data() {
        return {
            prompt: "",
            
            // api: new API(),
        }
    },
    methods: {
        submitForm() {
            this.$emit('submit', this.prompt);
        }
    }
}
</script>


<style scoped>
    #promptText {
        width: 100%;
        height: 150px;
        padding: 10px;
        border-radius: 4px;
        border: 1px solid black;
        box-sizing: border-box;
    }

    #promptForm {
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    
</style>