<template>
  <div class="hello">
    <transition name="">
      <div id="text" v-if="showText">
        <textarea name="main-text" id="main-text" v-model="inputText" cols="30" rows="10" placeholder="Paste your text here"></textarea>
        <button class="btn txt-center" v-on:click="fetchContext"> Get Context </button>
      </div>
    </transition>
    <loader v-if="showLoader"></loader>
    <transition name="fade">
      <div id="context-selector" v-if="showContext">
        <p class="head-back" v-on:click="backToText"><img src="./back.svg">Back</p>
        <div v-if="showContext && showContextSelector">
          <h3 class="header-sec">Select Context</h3>
          <ul v-if="contexts && contexts.length">
            <li v-for="(context, index) of contexts"><span><input type="radio" :id="index" name="context-select" :value="index" v-model="contextSelected"><label :for="index"> {{context}} </label></span></li>
          </ul>
          <div>
            <!-- <button class="btn txt-center" v-on:click="backToText">New Summary</button> -->
            <button class="btn txt-center" v-on:click="fetchFullSummary">Get Summary</button>
          </div>
        </div>
        <div v-if="showSummary">
            {{summary}}
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
  import axios from 'axios';
  import Loader from './Loader.vue'

  export default {
    name: 'HelloWorld',
    components: {
      Loader
    },
    props: {
      msg: String
    },
    data: function(){
      return {
        showText: true,
        inputText: '',
        contextSelected: 'C1',
        showContext: false,
        showOutput: false,
        selectedFormat: 'TEXT',
        textSelected: true,
        audioSelected: false,
        lineCount: 50,
        audioTime: 7,
        accent: 'EN-US',
        contexts: [],
        errors: [],
        topics: [],
        summary: "",
        showLoader: false,
        showSummary: false,
        showContextSelector: true
      }
    }, 
    methods: {
      fetchContext(){
        this.showText = false;
        this.showLoader = true;
        axios.post('http://localhost:5000/api/contexts', {
          text: this.inputText
        })
        .then(response => {
          this.showLoader = false
          this.contexts = response.data.contexts
          this.topics = response.data.topics
          this.inputText = response.data.inputText
          this.showContextSelector = true
        })
        .catch(e => {
          this.showLoader = false
          this.showContext = true
          this.showContextSelector = true
          this.errors.push(e)
        })
      },
      fetchFullSummary() {
        this.summary = ""
        this.showContext = false
        this.showContextSelector = false
        this.showLoader = true
        
        axios.post('http://localhost:5000/api/summary', {
          topic: this.topics[this.contextSelected],
          text: this.inputText
        })
        .then(response => {
          this.showLoader = false
          this.summary = response.data.summary
          this.showSummary = true
          this.showContext = true
        })
        .catch(e => {
          this.showLoader = false
          this.errors.push(e)
          this.summary = 'Some error happened! Try again!'
          this.showSummary = true
          this.showContext = true
        })
      },
      showFormatOptions() {
        if (this.selectedFormat === 'TEXT') {
          this.textSelected = true;
          this.audioSelected = false;
        } else {
          this.textSelected = false;
          this.audioSelected = true;
        }
      },
      backToText() {
        this.inputText = ""
        this.summary = ""
        this.showText = true;
        this.showContext = false
        this.showContextSelector = false
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pull-left {
  float: left;
}
.hello {
  padding: 1em;
}
h3 {
  margin: 40px 0 0;
  text-align: left;
}
.header-sec {
  margin-top: 0;
}
.head-back {
  margin-top: 0;
  text-align: left;
}
.head-back > img {
  margin-right: 8px;
  position: relative;
  top: 3px;
}

.output-modes {
  min-height: 30px;
  font-size: 15px;
}
select, input, textarea {
  width: 100%;
  border-radius: 4px;
  border: 1px solid #ddd;
  outline: none;
  font-size: 1em;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
input[type="radio"] {
  float: left;
}
.txt-center {
  text-align: center;
}
.btn {
  font-size: 16px;
  /* display: block; */
  background: #499AF8;
  color: #fff;
  font-weight: 600;
  border: none;
  border-radius: 4px;
  padding: 1em 2em;
  margin-top: 1em;
  outline: none;
}
li {
  text-align: left;
  margin: 1em 0;
}



[type="radio"]:checked,
[type="radio"]:not(:checked) {
    position: absolute;
    left: -9999px;
}
[type="radio"]:checked + label,
[type="radio"]:not(:checked) + label
{
    position: relative;
    padding-left: 28px;
    cursor: pointer;
    line-height: 20px;
    display: inline-block;
    color: #666;
}
[type="radio"]:checked + label:before,
[type="radio"]:not(:checked) + label:before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 18px;
    height: 18px;
    border: 1px solid #ddd;
    border-radius: 100%;
    background: #fff;
}
[type="radio"]:checked + label:after,
[type="radio"]:not(:checked) + label:after {
    content: '';
    width: 12px;
    height: 12px;
    background: #F87DA9;
    position: absolute;
    top: 4px;
    left: 4px;
    border-radius: 100%;
    -webkit-transition: all 0.2s ease;
    transition: all 0.2s ease;
}
[type="radio"]:not(:checked) + label:after {
    opacity: 0;
    -webkit-transform: scale(0);
    transform: scale(0);
}
[type="radio"]:checked + label:after {
    opacity: 1;
    -webkit-transform: scale(1);
    transform: scale(1);
}

</style>
