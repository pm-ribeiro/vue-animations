<template>
  <div class="about">
    <transition
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
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
    console.log('beforeEnter - set initial state');
    el.style.transform = 'translateY(-60px)';
    el.style.opacity = 0;
  }

  const enter =  (el, done) => {
    console.log('starting to enter - make transition');
    gsap.to(el, {
      y: 0,
      opacity: 1,
      duration: 3,
      ease: 'bounce.out',
      onComplete: done
    })
  }

  const afterEnter = () => {
    console.log('after enter', );

  }

</script>

<style>
  .about {
    max-width: 600px;
    margin: 20px auto;
  }

</style>