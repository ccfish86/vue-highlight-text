<template>
  <div id="app">
    <h1>Example Highlight</h1>
    <div>
      <h2>Component with default props</h2>
      <HighlightText :keyword="keyword">{{msg}}</HighlightText>
    </div>
    <div>
      <h2>Directive with default value</h2>
      <span v-highlight="{keyword}">{{msg}}</span>
    </div>
    <div>
      <h2>Component all props</h2>
      <HighlightText :keyword="keyword" :sensitive="sensitive" :overWriteStyle="overWriteStyle">{{msg}}</HighlightText>
    </div>
    <div>
      <h2>Directive all value</h2>
      <span v-highlight="{keyword, sensitive, overWriteStyle}">{{msg}}</span>
    </div>
    <div :key="index" v-highlight={keyword} v-for="(data, index) in loopData">{{data.text}}</div>
    <h2>input</h2>
    <div>
      <b>overWriteStyle</b> {{overWriteStyle}}
    </div>
    <div>
      <!-- <b>Keyword</b>: <input type="text" placeholder="keyword" v-model="keyword"><br> -->
      <b>Keyword</b>:
      <ul :key="index" v-for="(k, index) in keyword">
        <li><b>{{k}}</b></li>
      </ul>
      <input type="checkbox" v-model="sensitive" style="width: 20px; height: 20px">Case Sensitive :
      <b>{{sensitive}}</b>
    </div>
  </div>
</template>

<script>
import HighlightText from './components/VueHighlightText'
import highlight from './components/HighlightText'
import toStyle from 'to-style'

export default {
  name: 'app',
  components: {
    HighlightText
  },
  directives: {
    highlight
  },
  data() {
    return {
      msg: 'Lorem ipsum dolor',
      keyword: ['Lorem', 'ipsum', 'dolor', 'text1'],
      sensitive: false,
      overWriteStyle: {
        color: 'red',
        backgroundColor: 'blue'
      },
      loopData: [{ text: 'text1' }, { text: 'text2' }, { text: 'text3' }]
    }
  }
}
</script>

<style >
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  left: 0;
  right: 0;
  margin: auto;
  margin-top: 60px;
  width: 500px;
}
.highlight {
  color: green !important;
}
</style>
