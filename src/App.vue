<template>
<div class="app">
  <header>
    <div class="title">
      <img src="./assets/heart.svg" alt="logo">
      <h1>Hyrule Jobs</h1>
    </div>
    <div class="order">
      <button @click="handleClick('title')">Order by Title</button>
      <button @click="handleClick('salary')">Order by Salary</button>
      <button @click="handleClick('location')">Order by Location</button>  
    </div>
  </header>
  <JobsList :jobs="jobs" :order="order"></JobsList>
</div>
</template>

<script lang="ts">
import Vue from 'vue';

// components
import JobsList from './components/JobsList.vue';
// types
import Job from './types/Job';
import OrderTerm from './types/OrderTerm';
// local types
interface Data {
  jobs: Job[],
  order: OrderTerm
}

export default Vue.extend({
  name: 'App',
  components: {
    JobsList
  },
  data(): Data {
    return {
      jobs: [
        { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
        { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
        { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
        { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
        { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
      ],
      order: 'title'
    }
  },
  methods: {
    handleClick(term: OrderTerm) {
      this.order = term
    }
  },
  });
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600;700&display=swap');
  
  @font-face {
    font-family: HyliaSerif;
    src: url('assets/fonts/HyliaSerifBeta-Regular.otf') format('opentype');
  }
  
  body {
    font-family: 'Open Sans';
    background-color: #ece6d9;
  }
  h1 {
    font-family: HyliaSerif;
    letter-spacing: 4px;
  }
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  header .title {
    display: flex;
    justify-content: center;
  }
  header h1 {
    font-size: 3em;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>
