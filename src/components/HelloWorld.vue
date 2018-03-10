<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <transition name="slide-fade">
      <div id="text" v-if="showText">
        <textarea name="main-text" id="main-text" cols="30" rows="10" placeholder="Paste your text here"></textarea>
        <button class="btn txt-center" v-on:click="fetchContext"> Get Context </button>
      </div>
    </transition>
    <!-- <p>
      For guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://github.com/vuejs/vue-cli/tree/dev/docs" target="_blank">vue-cli documentation</a>.
    </p> -->
    <transition name="fade">
      <div id="context-selector" v-if="showContext">
        <h3>Select Context</h3>
        <ul>
          <li><span><input type="radio" id="c1" name="context-select" value="C1" v-model="contextSelected" checked="checked" v-bind:class="{'checked': contextSelected==='C1'}"><label for="c1"> Context 1 </label></span></li>
          <li><span><input type="radio" id="c2" name="context-select" value="C2" v-model="contextSelected" v-bind:class="{'checked': contextSelected==='C2'}"><label for="c2"> Context 2 </label></span></li>
        </ul>
        <button class="btn txt-center" v-on:click="fetchFullSummary">Get Summary</button>
      </div>
    </transition>

    <transition name="fade">
      <div id="output-selector" v-if="showOutput">
        <h3>Select Output Format</h3>
        <ul>
          <li><span><input type="radio" v-bind:class="{'checked': ctextSelected}" id="t" v-on:change="showFormatOptions" value="TEXT" name="output-select" v-model="selectedFormat"> <label for="t"> Text </label> </span></li>
          <li><span><input type="radio" v-bind:class="{'checked': audioSelected}" id="a" v-on:change="showFormatOptions" value="AUDIO" name="output-select" v-model="selectedFormat"> <label for="a"> Audio </label> </span></li>
        </ul>
        <div v-if="textSelected">
          <label class="pull-left" for="line-count">Enter Line Count: </label> <input type="number" v-model="lineCount" min="0" id="line-count" class="output-modes"/>
        </div>

        <div v-if="audioSelected">
          <label class="pull-left" for="time">Enter Audio Time:</label>  <input type="number" v-model="audioTime" min="0" id="time" class="output-modes" />
          <label for="accent" class="pull-left">Select Audio Accent: </label>
          <select id="accent" v-model="accent" class="output-modes">
              <option value="EN-UK">English (UK)</option>
              <option value="EN-IN">English (IN)</option>
              <option value="EN-US">English (US)</option>
              <!-- <option value="EN-UK">English (UK)</option> -->
            </select>
        </div>
      </div>
    </transition>

    
    <!-- <ul>
      <li><a href="https://router.vuejs.org/en/essentials/getting-started.html" target="_blank">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org/en/intro.html" target="_blank">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org/en" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul> -->
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    },
    data: function(){
      return {
        showText: true,
        contextSelected: 'C1',
        showContext: false,
        showOutput: false,
        selectedFormat: 'TEXT',
        textSelected: true,
        audioSelected: false,
        lineCount: 50,
        audioTime: 7,
        accent: 'EN-US' 
      }
    }, 
    methods: {
      fetchContext(){
        this.showText = false;
        this.showContext = true;
      },
      fetchFullSummary() {
        console.log(this.contextSelected);
        this.showOutput = true;
      },
      showFormatOptions() {
        if (this.selectedFormat === 'TEXT') {
          this.textSelected = true;
          this.audioSelected = false;
        } else {
          this.textSelected = false;
          this.audioSelected = true;
        }
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
.output-modes {
  min-height: 30px;
  font-size: 15px;
}
select, input, textarea {
  width: 100%;
  border-radius: 4px;
  border: 1px solid #ddd;
  outline: none;
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
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
