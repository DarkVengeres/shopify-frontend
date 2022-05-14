<template>
  <div class="home">
    <prompt-form @submit="submit"></prompt-form>
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
    Responses
  },

  methods: {
    async submit(prompt){
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
          response: response.choices[0].text,
        }
      );
    }
    
  },
};
</script>

<style scoped>

</style>
