<template>
  <div class="about">
    <transition
      appear
      @before-enter="beforeEnter"
      @enter="enter"
    >
      <h1 v-if="showTitle">About</h1>
    </transition>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit.
      Cum aperiam officia possimus delectus inventore quod quisquam
      culpa voluptas iusto, quae maiores quo dolorum, corporis
      laboriosam a dolore consequatur assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit.
      Cum aperiam officia possimus delectus inventore quod quisquam 
      culpa voluptas iusto, quae maiores quo dolorum, corporis
      laboriosam a dolore consequatur assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. 
      Cum aperiam officia possimus delectus inventore quod quisquam 
      culpa voluptas iusto, quae maiores quo dolorum, corporis 
      laboriosam a dolore consequatur assumenda nam!
    </p>
  </div>
</template>

<script setup>
  import {ref} from 'vue';
  import gsap from 'gsap';

  const showTitle = ref(true);

  // el represents the dom element its inside the transition
  const beforeEnter =  (el) => {
    console.log('beforeEnter', el);
  }

  const enter =  (el) => {
    console.log('enter', el);
  }

</script>

<style>
  .about {
    max-width: 600px;
    margin: 20px auto;
  }

</style>