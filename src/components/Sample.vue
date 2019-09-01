<template>
  <div>
    <h1>Hello Vue !! </h1>
    <div>
      count:{{count}}
    </div>
    <div>
      <h3>v-ifとv-showを使用した表示制御</h3>
      <div v-if="showFlg">v-ifでの表示</div>
      <div v-show="showFlg">v-showでの表示</div>
    </div>
    <div>
      <h1>配列のLoop</h1>
      <ul v-for="(item, index) in arrayItems" :key="index">
        <li>
          {{item}} - {{index}}
        </li>
      </ul>
    </div>
    <div>
      <h1>ObjectのLoop</h1>
      <ul v-for="(val, key, index) in objects" :key="key">
        <li>
          {{key}} - {{val}} - {{index}}
        </li>
      </ul>
    </div>
    <div>
      <h1> 数字のLoop </h1>
      <ul v-for="(num, index) in number" :key="index">
        <li>
          {{ num }} - {{index}}
        </li>
      </ul>
    </div>
    <div>
      <h1>文字列のLoop</h1>
      <ul v-for="(str, index) in string" :key="index" >
        <li>{{str}} - {{index}} </li>
      </ul>
    </div>
    <div>
      <h1>アクションイベント</h1>
      <button v-on:click="viewDialog('click1')">v-on:click記述のイベント</button>
      <button @click="viewDialog('click2')">@click記述のイベント</button>
      <button @click="countup()">数値カウントアップ</button>
    </div>
    <div>
      <h1>テキスト</h1>
      <input v-model="text">
      <p>入力文字：{{ text }}</p>
    </div>
    <div>
      <h1>テキストエリア</h1>
      <textarea v-model="textarea"></textarea>
      <p>入力文字：{{ textarea }}</p>
    </div>
    <div>
      <h1>チェックボックス</h1>
      <input type="checkbox" id="checkbox" v-model="checked">
      <label for="checkbox">{{checked}}</label>
    </div>
    <div>
      <h1>複数チェックボックス</h1>
      <input type="checkbox" id="rin" value="rin" v-model="checkedNames">
      <label for="rin">りん</label>
      <input type="checkbox" id="rina" value="rina" v-model="checkedNames">
      <label for="rina">りな</label>
      <input type="checkbox" id="ritsu" value="ritsu" v-model="checkedNames">
      <label for="ritsu">りつ</label>
      <input type="checkbox" id="riku" value="riku" v-model="checkedNames">
      <label for="riku">りく</label>
      <input type="checkbox" id="ryou" value="ryou" v-model="checkedNames">
      <label for="ryou">りょう</label>
      <input type="checkbox" id="ryoku" value="ryoku" v-model="checkedNames">
      <label for="ryoku">りょく</label>
      <br>
      <span>{{checkedNames}}</span>
    </div>
    <div>
      <h1>ラジオボタン</h1>
      <input type="radio" id="fm" value="FM" v-model="modulation">
      <label for="fm">FM</label>
      <input type="radio" id="am" value="AM" v-model="modulation">
      <label for="am">AM</label>
      <br>
      <span>Modulation: {{modulation}}</span>
    </div>
    <div>
      <h1>リストボックス</h1>
      <select v-model="selected">
        <option disabled value="0"> 選択してください</option>
        <option>ほしのこえ</option>
        <option>秒速５センチメートル</option>
        <option>言の葉の庭</option>
        <option>君の名は。</option>
        <option>天気の子</option>
      </select>
    </div>
    <div>
      <h1>リストボックス(複数)</h1>
      <select v-model="selectedMulti" multiple>
        <option disabled value="0"> 選択してください</option>
        <option>時をかける少女</option>
        <option>サマーウォーズ</option>
        <option>おおかみこどもの雨と雪</option>
        <option>バケモノの子</option>
        <option>未来のミライ</option>
      </select>
      <br>
      <span>{{selectedMulti}}</span>
    </div>
    <div>
      <h1>算出プロパティ</h1>
      <h2>奇数</h2>
      <ul v-for="(num_odd, index) of odd" :key="index">
        <li>{{num_odd}}</li>
      </ul>
      <h2>偶数</h2>
      <ul v-for="(num_even, index) of even" :key="index">
        <li>{{num_even}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sample',
  data() {
    return {
      count: 0,
      showFlg: false,
      arrayItems: ["ピチュー","ピカチュウ","ライチュウ"],
      objects: {
        "hoge" : "hogehoge",
        "fuga" : "fugafuga"
      },
      number: 10,
      string: "パンケーキたべたい",
      text: '',
      textarea: '',
      checked: false,
      checkedNames: [],
      modulation: '',
      selected: '',
      selectedMulti: [],
      numArray: [1,2,3,4,5,6,7,8,9,10]
    }
  },
  methods: {
    countup () {
      this.count++
    },
    outputConsole () {
      /* eslint-disable no-console */
      console.log("created")
    },
    viewDialog (msg) {
      alert(msg)
    }
  },
  created () {
    this.outputConsole()
  },
  computed: {
    odd () {
      return this.numArray.filter(num => {return num % 2 !== 0})
    },
    even () {
      return this.numArray.filter(num => {return num % 2 === 0})
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
