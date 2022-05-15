<template>
    <form @submit.prevent="submitForm" id="promptForm">
        <textarea v-on:keyup.enter="submitForm" type="text" id="promptText" required v-model="prompt" placeholder="Enter a phrase here..."></textarea>
        <div class="buttonLoader">
            <button type="submit" id="submit"> Submit </button>
            <button @click.prevent="resetResponses()" id="reset"> Reset </button>
            <loading v-if="isLoading" ></loading>
        </div>
    </form>
</template>

<script>
import loading from './../loading.vue';

export default {
    data() {
        return {
            prompt: "",
            isLoading: false,
            promptType: "Analogy Maker"
        }
    },
    methods: {
        submitForm() {
            this.isLoading = true;
            this.$root.$refs.home.submit("Create an analogy for this phrase :" + this.prompt, this.promptType);
            this.prompt = "";
        },
        loadingFinished() {
            this.isLoading = false;
        },
        resetResponses() {
            this.$root.$refs.home.reset();
        }
    },
    components: {
        loading,
    },
    created () {
        this.$root.$refs.promptForm = this;
    },
}
</script>


<style scoped>

    #promptForm {
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #promptText {
        opacity: 0.97;
        height: 150px;
        padding: 20px;
        border-radius: 4px;
        border: 1px solid var(--primary);
        box-sizing: border-box;
        font-family: "M PLUS Code Latin";
        font-size: 1.2em;
        background-color: var(--consoleBackground);
        resize: none;
        margin : 20px;
        padding: 10px;
        color : var(--textTitles);
        outline : none;
        box-shadow: 0 8px 16px 0 rgba(0,0,0,0.5);
    }

    ::placeholder {
        color: var(--textArea);
    }

    #submit {
        background-color: var(--primary);
        color: var(--textTitles);
    }

    #reset {
        margin: 0 10px;
        background-color: var(--secondary);
        color: var(--textSubtitles);
    }

    .buttonLoader {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: center;
        margin-left: 20px;
        margin-bottom: 20px;
        
    }
    
</style>