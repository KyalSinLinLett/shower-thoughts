<template>
  <div id="app">
    <full-page :options="options" id="fullpage" v-if="isLoaded">
      <div v-for="showerThought in showerThoughts" :key="showerThought.data.id" class="section">
        <div class="container">
          <img class="shower-icon" src="./assets/shower.png" width="25%" alt="shower icon">

          <div class="quote-symbol">"</div>
          <a target="_blank" :href="`${ showerThought.data.url }`" class="quote">{{ showerThought.data.title }}</a>
          <div class="details">
            <div class="details-author">Author: {{ showerThought.data.author }} @ <a style="text-decoration: none; color: white;" target="_blank" :href="`${ showerThought.data.url }`">r/Showerthoughts</a></div>
            <div class="stats">{{ showerThought.data.ups }} Upvotes</div>
          </div>
        </div>

        <div class="cp-div">
          <span class="copyright">© shower-thots @ Kyal 2020 </span>
        </div>
        

      </div>

    </full-page>
    <div v-else class="loading-icon">
      <div class="lds-grid"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
    </div>
  </div>
</template>

<script>

export default {

  name: 'App',

  created() { 
    fetch('https://www.reddit.com/r/Showerthoughts.json?limit=100')
      .then(response => response.json())
      .then(data => {
        this.showerThoughts = data.data.children;
        this.showerThoughts.shift()
        this.showerThoughts.shift()
        this.isLoaded = true;
      })
  },
  
  components: {},

  data() {
    return {

      isLoaded: false,

      showerThoughts: [],

      options: {
        sectionsColor: [
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          '#52ad9c', "#222725", "#a44a3f", "#175676", "#2d3047", 
          '#33658a', "#2f4858", "#744253", "#3a506b", "#003559", 
          
        ]
      }
    }
  },


}
</script>

<style>
  
  @import url('https://fonts.googleapis.com/css2?family=Patrick+Hand&display=swap');

  #app {
    font-family: 'Patrick Hand', cursive;
    color: #2d3748;
  }

  body {
    margin: 0;
    padding: 0;
    background-color: darkgray;
  }

  h3 {
    margin: 0;
  }

  .copyright {
    font-size: 10px;
    color: white;
    position: relative;
    padding-bottom: 30px;
  }

  .shower-icon {
    border-radius: 51%;
    box-shadow: 7px 7px 25px -10px rgba(0,0,0,0.6);
  }

  .container {
    margin: auto;
    max-width: 800px;
    padding: 80px 16px;
  }

  .section {
    text-align: center;
  }

  .quote-symbol {
    font-family: 'Patrick Hand', cursive;
    font-size: 40px;
    line-height: 0;
    margin-top: 58px;
    color: white;
  }

  .quote {
    text-decoration: none;
    font-family: 'Patrick Hand', cursive;
    color: white;
    font-size: 25px;
    line-height: 1.5;
  }

  .details-author {
    font-size: 16px;
    margin-top: 10px;
    color: white;
  }

  .stats {
    font-size: 14px;
    color: white;
  }

  /* Loading icon */

  .lds-grid {
    display: inline-block;
    position: relative;
    width: 80px;
    height: 80px;
  }
  .lds-grid div {
    position: absolute;
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background: white;
    animation: lds-grid 1.2s linear infinite;
  }
  .lds-grid div:nth-child(1) {
    top: 8px;
    left: 8px;
    animation-delay: 0s;
  }
  .lds-grid div:nth-child(2) {
    top: 8px;
    left: 32px;
    animation-delay: -0.4s;
  }
  .lds-grid div:nth-child(3) {
    top: 8px;
    left: 56px;
    animation-delay: -0.8s;
  }
  .lds-grid div:nth-child(4) {
    top: 32px;
    left: 8px;
    animation-delay: -0.4s;
  }
  .lds-grid div:nth-child(5) {
    top: 32px;
    left: 32px;
    animation-delay: -0.8s;
  }
  .lds-grid div:nth-child(6) {
    top: 32px;
    left: 56px;
    animation-delay: -1.2s;
  }
  .lds-grid div:nth-child(7) {
    top: 56px;
    left: 8px;
    animation-delay: -0.8s;
  }
  .lds-grid div:nth-child(8) {
    top: 56px;
    left: 32px;
    animation-delay: -1.2s;
  }
  .lds-grid div:nth-child(9) {
    top: 56px;
    left: 56px;
    animation-delay: -1.6s;
  }
  @keyframes lds-grid {
    0%, 100% {
      opacity: 1;
    }
    50% {
      opacity: 0.5;
    }
  }


</style>
