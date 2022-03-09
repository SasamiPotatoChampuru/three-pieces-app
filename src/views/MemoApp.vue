<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
  
  <div id="all">
    <div class="main-container">
      <h1>Memo App</h1>
      <p>メモを記入してください</p>
      <input type="text" v-model="input" placeholder="入力してください">
      <button v-on:click="addButton" type="button" class="btn btn-primary">追加</button>

      <p>オプション</p>
      <input class="input_2" type="text" v-model="number">番目
      <button v-on:click="resetButton" type="button" class="btn btn-dark">削除</button>
      <button v-on:click="insertButton" type="button" class="btn btn-dark">挿入</button>
      <button v-on:click="changeButton" type="button" class="btn btn-dark">変更</button>
      <button v-on:click="allResetButton" type="button" class="btn btn-danger">全削除</button>
    </div>

    <div class="list">
      <h2>メモリスト</h2>
      <ol>
        <li v-for="(memo,key) in memoLists" :key="key">
          {{memo}}
        </li>
      </ol>
    </div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      memoLists: [],
    }
  },
  methods: {
    addButton: function () {
      this.memoLists.push(this.input)
      this.input = ""
    },
    resetButton: function () {
      this.memoLists.splice(this.number-1,1)
    },
    insertButton: function() {
      this.memoLists.splice(this.number-1,0,this.input)
    },
    changeButton: function() {
      this.memoLists.splice(this.number-1,1,this.input)
    },
    allResetButton: function() {
      this.memoLists.splice(0,this.memoLists.length)
    }
  },
}
</script>

<style>
@charset "UTF-8";

#all {
  background-color: #dddddd;
  min-height: 100vh;
  padding: 40px 30px;
}

.main-container {
  width: 50%;
  margin: 0 auto 20px;
  padding: 20px 30px;
  border-style: double;
  text-align: center;
  background-color: #3c3f3f3a
}

.input_2 {
  width: 6%;
}

h1,p,h2{
  font-family: serif;
}

.list {
  background-color: white;
  height: 250px;
  width: 40%;
  margin: 0 auto;
};

ol {
  margin: 0 auto;
}

h2 {
  border: 1px solid black;
}

li {
  text-align: center;
  padding-right: 35px;
}


h2 {
  text-align: center;
}


</style>
