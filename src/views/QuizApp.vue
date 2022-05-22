<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2>Q. {{ "クイズタイトル" }}</h2>
    <img
      class="quiz-image"
      src="https://via.placeholder.com/300x300"
      alt="クイズタイトル"
    />
    <div class="container">
      <button>
        {{ "選択肢1" }}
      </button>
      <button>
        {{ "選択肢2" }}
      </button>
      <button>
        {{ "選択肢3" }}
      </button>
    </div>
    <div>{{ "答え" }}</div>
  </div>
</template>

<script>
data() {

  return{
    quiz:{
      text: "この星の名前は何でしょう？",
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
