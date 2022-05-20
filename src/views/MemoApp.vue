<template>
  <div>
    <h1>Vue メモ</h1>
    <div class="memo-list">
      <ul class="memo-list__container">
        <li class="memo">
          <div class="memo__checkbox">
            <input type="checkbox" />
          </div>
          <div class="memo__text">ひき肉を300g買う</div>
          <button class="memo__delete" v-on:click="deleteItem">削除</button>
        </li>
        <li class="memo">
          <div class="memo__checkbox">
            <input type="checkbox" />
          </div>
          <div class="memo__text">ホウレンソウを1束買う</div>
          <button class="memo__delete" v-on:click="deleteItem">削除</button>
        </li>
        <li class="memo">
          <div class="memo__checkbox">
            <input type="checkbox" />
          </div>
          <div class="memo__text">ピーマンを2個買う</div>
          <button class="memo__delete" v-on:click="deleteItem">削除</button>
        </li>
      </ul>
      <div class="add-memo-field">
        <form>
          <input class="add-memo-field__input" type="text" v-model="newItem" />
          <button class="add-memo-field__button" v-on:click="addItem">
            追加
          </button>
        </form>
        <li v-for="(memo, index) in memos" :key="index">
          <input type="checkbox" v-model="memo.isDone" />
          <span v-bind:class="{ done: memo.isDOne }">
            {{ memo.item }}
          </span>
          <!-- indexによってどこのdeleteが消されているのかを取得する -->
          <button v-on:click="deleteItem(index)">Delete</button>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
      todos: [],
    }
  },
  methods: {
    addItem: function () {
      //console.log("Clicked!")
      //未入力状態で追加ボタンを押しても追加されないようにする
      if (this.newItem === "") return

      let memo = {
        item: this.newItem,
        isdone: false,
      }
      this.todos.push(memo)
      this.newItem = ""
    },
    deleteItem: function (index) {
      //   console.log("Delete!")
      //   console.log(index)
      //第一引数が削除を始める配列、第二引数が削除する長さ
      this.memos.splice(index, 1)
    },
  },
}
</script>

<style scoped>
.memo-list {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
}

.memo-list__container {
  padding: 0;
}

.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #b23b61;
}

.memo__text {
  margin-left: 2rem;
  text-align: left;
}

.memo__text--done {
  text-decoration-line: line-through;
}

.memo__delete {
  margin-left: 1rem;
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.memo__delete:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}

.add-memo-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.add-memo-field__input {
  padding: 10px;
}
.add-memo-field__button {
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.add-memo-field__button:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}
</style>
