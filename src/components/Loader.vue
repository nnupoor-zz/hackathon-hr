<template>
  <div>
    <div class="quote">
      <div class="quote-header shell-loading">
        <span class="name"></span>
      </div>
      <div class="quote-body">
        <div class="quote-image shell-loading"></div>
        <div class="quote-text">
          <p class="shell-loading quote-listing" style=""></p>
          <p class="shell-loading quote-listing" style=""></p>
          <p class="shell-loading quote-listing" style=""></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
  }
</script>

<style scoped>
  .quote {
    border-left: 0px solid rgba(0, 0, 0, 0.3);
    padding-left: 0em;
    opacity: 0.8;
    margin: 1em 0;
  }
  .desktop .quote-body {
    padding-bottom: 8px;
  }
  .quote-image {
    width: 3em;
    height: 2.5em;
    margin-right: 1em;
    position: absolute;
  }
  .quote-text {
    display: inline-block;
    vertical-align: top;
    line-height: 1.5;
    word-wrap: break-word;
    position: absolute;
    left: 2em;
    right: 1em;
  }
  .quote-image + .quote-text {
    margin-left: 3em;
    max-width: 70%;
  }
  .quote-header {
    margin-bottom: 0.5em;
    font-weight: bold;
    line-height: 1.27;
    min-height: 1.2rem;
    color: #333333;
  }
  .quote-listing {
    min-height: .5rem;
    margin: 0;
    margin-top: .5rem;
  }
  .quote-listing:first-child{
    min-height: .5rem;
    margin: 0;
  }
  .desktop .quote-header {
    font-size: 15px;
    margin-bottom: 12px;
  }

  @-webkit-keyframes appShellBackground {
    0%{background-position:100% 50%}
    100%{background-position:0% 50%}
  }
  @-moz-keyframes appShellBackground {
      0%{background-position:100% 50%}
      100%{background-position:0% 50%}
  }
  @keyframes appShellBackground {
      0%{background-position:100% 50%}
      100%{background-position:0% 50%}
  }

  .shell-loading {
    background: rgba(179,179,179,1);
    background: -moz-linear-gradient(left, rgba(230,230,230,1) 0%, rgba(230,230,230,1) 36%, rgba(247,247,247,1) 51%, rgba(230,230,230,1) 64%, rgba(230,230,230,1) 100%);
    background: -webkit-gradient(left top, right top, color-stop(0%, rgba(230,230,230,1)), color-stop(36%, rgba(230,230,230,1)), color-stop(51%, rgba(247,247,247,1)), color-stop(64%, rgba(230,230,230,1)), color-stop(100%, rgba(230,230,230,1)));
    background: -webkit-linear-gradient(left, rgba(230,230,230,1) 0%, rgba(230,230,230,1) 36%, rgba(247,247,247,1) 51%, rgba(230,230,230,1) 64%, rgba(230,230,230,1) 100%);
    background: -o-linear-gradient(left, rgba(230,230,230,1) 0%, rgba(230,230,230,1) 36%, rgba(247,247,247,1) 51%, rgba(230,230,230,1) 64%, rgba(230,230,230,1) 100%);
    background: -ms-linear-gradient(left, rgba(230,230,230,1) 0%, rgba(230,230,230,1) 36%, rgba(247,247,247,1) 51%, rgba(230,230,230,1) 64%, rgba(230,230,230,1) 100%);
    background: linear-gradient(to right, rgba(230,230,230,1) 0%, rgba(230,230,230,1) 36%, rgba(247,247,247,1) 51%, rgba(230,230,230,1) 64%, rgba(230,230,230,1) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#b3b3b3', endColorstr='#f5f5f5', GradientType=1 );
    background-size: 600% 600%;
    -webkit-animation: appShellBackground 5s ease infinite;
    -moz-animation: appShellBackground 5s ease infinite;
    animation: appShellBackground 5s ease infinite;
  }

  /*.sk-circle {
    margin: 1em auto;
    width: 10px;
    height: 50px;
    position: relative;
  }
  .sk-circle .sk-child {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
  }
  .sk-circle .sk-child:before {
    content: '';
    display: block;
    margin: 0 auto;
    width: 15%;
    height: 15%;
    background-color: #0abf50;
    border-radius: 100%;
    -webkit-animation: sk-circleBounceDelay 1.2s infinite ease-in-out both;
            animation: sk-circleBounceDelay 1.2s infinite ease-in-out both;
  }
  .sk-circle .sk-circle2 {
    -webkit-transform: rotate(30deg);
        -ms-transform: rotate(30deg);
            transform: rotate(30deg); }
  .sk-circle .sk-circle3 {
    -webkit-transform: rotate(60deg);
        -ms-transform: rotate(60deg);
            transform: rotate(60deg); }
  .sk-circle .sk-circle4 {
    -webkit-transform: rotate(90deg);
        -ms-transform: rotate(90deg);
            transform: rotate(90deg); }
  .sk-circle .sk-circle5 {
    -webkit-transform: rotate(120deg);
        -ms-transform: rotate(120deg);
            transform: rotate(120deg); }
  .sk-circle .sk-circle6 {
    -webkit-transform: rotate(150deg);
        -ms-transform: rotate(150deg);
            transform: rotate(150deg); }
  .sk-circle .sk-circle7 {
    -webkit-transform: rotate(180deg);
        -ms-transform: rotate(180deg);
            transform: rotate(180deg); }
  .sk-circle .sk-circle8 {
    -webkit-transform: rotate(210deg);
        -ms-transform: rotate(210deg);
            transform: rotate(210deg); }
  .sk-circle .sk-circle9 {
    -webkit-transform: rotate(240deg);
        -ms-transform: rotate(240deg);
            transform: rotate(240deg); }
  .sk-circle .sk-circle10 {
    -webkit-transform: rotate(270deg);
        -ms-transform: rotate(270deg);
            transform: rotate(270deg); }
  .sk-circle .sk-circle11 {
    -webkit-transform: rotate(300deg);
        -ms-transform: rotate(300deg);
            transform: rotate(300deg); }
  .sk-circle .sk-circle12 {
    -webkit-transform: rotate(330deg);
        -ms-transform: rotate(330deg);
            transform: rotate(330deg); }
  .sk-circle .sk-circle2:before {
    -webkit-animation-delay: -1.1s;
            animation-delay: -1.1s; }
  .sk-circle .sk-circle3:before {
    -webkit-animation-delay: -1s;
            animation-delay: -1s; }
  .sk-circle .sk-circle4:before {
    -webkit-animation-delay: -0.9s;
            animation-delay: -0.9s; }
  .sk-circle .sk-circle5:before {
    -webkit-animation-delay: -0.8s;
            animation-delay: -0.8s; }
  .sk-circle .sk-circle6:before {
    -webkit-animation-delay: -0.7s;
            animation-delay: -0.7s; }
  .sk-circle .sk-circle7:before {
    -webkit-animation-delay: -0.6s;
            animation-delay: -0.6s; }
  .sk-circle .sk-circle8:before {
    -webkit-animation-delay: -0.5s;
            animation-delay: -0.5s; }
  .sk-circle .sk-circle9:before {
    -webkit-animation-delay: -0.4s;
            animation-delay: -0.4s; }
  .sk-circle .sk-circle10:before {
    -webkit-animation-delay: -0.3s;
            animation-delay: -0.3s; }
  .sk-circle .sk-circle11:before {
    -webkit-animation-delay: -0.2s;
            animation-delay: -0.2s; }
  .sk-circle .sk-circle12:before {
    -webkit-animation-delay: -0.1s;
            animation-delay: -0.1s; }

  @-webkit-keyframes sk-circleBounceDelay {
    0%, 80%, 100% {
      -webkit-transform: scale(0);
              transform: scale(0);
    } 40% {
      -webkit-transform: scale(1);
              transform: scale(1);
    }
  }

  @keyframes sk-circleBounceDelay {
    0%, 80%, 100% {
      -webkit-transform: scale(0);
              transform: scale(0);
    } 40% {
      -webkit-transform: scale(1);
              transform: scale(1);
    }
  }*/
</style>
<!-- <template> -->
  <!-- <div class="sk-circle">
    <div class="sk-circle1 sk-child"></div>
    <div class="sk-circle2 sk-child"></div>
    <div class="sk-circle3 sk-child"></div>
    <div class="sk-circle4 sk-child"></div>
    <div class="sk-circle5 sk-child"></div>
    <div class="sk-circle6 sk-child"></div>
    <div class="sk-circle7 sk-child"></div>
    <div class="sk-circle8 sk-child"></div>
    <div class="sk-circle9 sk-child"></div>
    <div class="sk-circle10 sk-child"></div>
    <div class="sk-circle11 sk-child"></div>
    <div class="sk-circle12 sk-child"></div>
  </div> -->
