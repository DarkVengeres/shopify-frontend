<template>
  <div class="home">
    <div class="spacer layer1">
      <div id="headContainer">
        <h1 id="mainTitle">Welcome to OpenAI</h1>
        <div>
          <button id="import" @click="importJSON()">Import</button>
          <button id="export" @click="exportJSON()">Export</button>
        </div>
      </div>
      <prompt-form @submit="submit" @reset="reset"></prompt-form>
    </div>
    <responses :responses="responses"></responses>
  </div>
</template>

<script>
import PromptForm from './../components/prompt-form.vue';
import Responses from './../components/responses.vue';

export default {
  name: "Home",
  data() {
    return {
      responses: [],
      key : `${process.env.VUE_APP_API_KEY}`,
    };
  },
  components: {
    PromptForm,
    Responses,
  },

  methods: {
    reset() {
      this.responses = [];
    },
    async submit(prompt, promptType) {
      const data = {
          prompt: prompt,
          temperature: 0.5,
          max_tokens: 256,
          top_p: 1.0,
          frequency_penalty: 0.0,
          presence_penalty: 0.0,
      };
      
      let response = await fetch("https://api.openai.com/v1/engines/text-curie-001/completions", {
          method: "POST",
          headers: {
              "Content-Type": "application/json",
              Authorization: `Bearer ${this.key}`,
          },
          body: JSON.stringify(data),
      }).then(res => res.json());
      this.responses.unshift(
        {
          id: this.responses.length + 1,
          prompt: prompt,
          promptType: promptType,
          response: response.choices[0].text,
        }
      );
      this.$root.$refs.promptForm.isLoading = false;
    },
    exportJSON() {
      let data = {
        responses: this.responses,
      };
      let blob = new Blob([JSON.stringify(data)], {type: "application/json"});
      let url = URL.createObjectURL(blob);
      let a = document.createElement("a");
      a.href = url;
      a.download = "openai.json";
      a.click();
    },
    importJSON() {
      let input = document.createElement("input");
      input.type = "file";
      input.addEventListener("change", (e) => {
        let file = e.target.files[0];
        let reader = new FileReader();
        reader.onload = (e) => {
          let data = JSON.parse(e.target.result);
          this.responses = data.responses;
        };
        reader.readAsText(file);
      });
      input.click();
    }
  },

  mounted() {
    if(localStorage.responses){
      this.responses = JSON.parse(localStorage.responses);
    }
  },

  watch: {
    responses(newResponses) {
      localStorage.responses = JSON.stringify(newResponses);
    }
  },

};
</script>

<style scoped>
#headContainer {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

#export{
  background-color: var(--primary);
  color: var(--textTitles);
  margin: 20px 20px 20px 10px;
}

#import{
  background-color: var(--wave) ;
  color: var(--primary);
  border : 4px solid var(--primary);
  padding: 5px;
}


.spacer {
  aspect-ratio: 960/100;
  width: 100%;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

.layer1 {
  background-image: url('./../assets/navWave.svg');
}

#mainTitle {
  font-size: 3em;
  font-weight: bold;
  color: var(--mainTitle);
  margin-left: 10px;
}

</style>
