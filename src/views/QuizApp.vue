<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2>Q. {{ quiz.title }}</h2>
    <img
      class="quiz-image"
      src="https://via.placeholder.com/300x300"
      alt="クイズタイトル"
    />
    <div class="container">
      <button v-for="choice in choices">
        {{ choice[0].text }}
      </button>
      <button v-for="choice in choices">
        {{ choice[1].text }}
      </button>
      <button v-for="choice in choices">
        {{ choice[2].text }}
      </button>
    </div>
    <div>{{ quiz.feedback }}</div>
  </div>
</template>

<script>
data() {

  return{
    feedback:"",
    quiz:{
      title: "この星の名前は何でしょう？",
      image:"Ganymede.jpg",
      choices:[
        {
          text:"ゴリアテ",
          iscorrect: false,
          feedback: "残念！ゴリアテは、旧約聖書に登場するダビデに石で殺される巨人だよ。",

          },

        {
          text:"ゼニガメ",
          iscorrect: false,
          feedback:"残念！ゼニガメは、クサガメまたはニホンイシガメの幼体だよ。",

        },

        {
          text:"ガニメデ",
          iscorrect: true,
          feedback:"正解！ガニメデは、木星の第三惑星だよ！",

        },
      ],
    },
   }
},

methods: {
 choiceclick = function(choiceNumber) {

   const choice = this.quiz.choices[chiceNumber]

   this.choice.feedback

   },

},
Vue.createApp(Quiz).mount("#app")
</script>
<style>
.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.quiz-image {
  height: 300px;
  width: 300px;
  object-fit: contain;
}

.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>
