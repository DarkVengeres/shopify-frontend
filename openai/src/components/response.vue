<template>
    <div>
        <div class="promptHead">
            <h2>Prompt :</h2>
            <p class="type" :id="response.id"> {{response.promptType }} </p>
        </div>
        <p class="card">{{ response.prompt }}</p>
        <div class="promptHead">
            <h2>Response :</h2>
            <button id="download" @click="exportTxt()"> Download </button>
        </div>
        <p class="card">{{ response.response }}</p>
    </div>
</template>

<script>
export default {
    name: "Response",
    props: {
        response : Object,
    },
    methods :{
        exportTxt () {
            let text = `${this.response.response}`;
            let element = document.createElement('a');
            element.setAttribute('href', 'data:text/plain;charset=utf-8,' + encodeURIComponent(text));
            element.setAttribute('download', `${this.response.id}.txt`);
            element.style.display = 'none';
            document.body.appendChild(element);
            element.click();
            document.body.removeChild(element);
        },
    }
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

#download {
    background-color: var(--secondary);
    color: var(--textTag);
    border: none;
    border-radius: 4px;
    padding: 5px;
    margin: 10px;
    font-family: "M PLUS Code Latin";
}


</style>