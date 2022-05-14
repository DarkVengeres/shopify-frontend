<template>
    <form @submit.prevent="submitForm" id="promptForm">
        <textarea type="text" id="promptText" required v-model="prompt" placeholder="Enter your prompt here..."></textarea>
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
        font-weight: bold;
        background-color: var(--consoleBackground);
        resize: none;
        margin : 10px;
        padding: 10px;
        color : var(--textTitles);
    }

    #promptForm {
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #promptForm button {
        width: 100px;
        height: 40px;
        border-radius: 4px;
        border: 1px solid black;
        background-color: var(--primary);
        color: var(--textTitles);
        font-size: 1.2em;
        font-weight: bold;
        margin: 10px;
        padding: 10px;
        cursor: pointer;
    }

    #promptForm button:hover {
        background-color: var(--secondary);
        color : var(--textSubtitles);
        box-shadow: 0 8px 16px 0 rgba(0,0,0,0.5);
    }

    ::placeholder {
        color: var(--textArea);
    }
    
</style>