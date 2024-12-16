<template>
  <div class="about">
    <transition
      appear
      name="fade"
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
      @before-leave="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
    >
      <h1 v-if="showTitle">About</h1>
    </transition>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
  </div>
</template>

<script setup>
  import {ref} from 'vue';

  const showTitle = ref(true);

  // el represents the dom element its inside the transition
  const beforeEnter =  (el) => {
    console.log('beforeEnter', el);
  }

  const enter =  (el) => {
    console.log('enter', el);
  }

  const afterEnter =  (el) => {
    el.style.color = 'green';
    console.log('afterEnter', el);

    setTimeout(()=> showTitle.value = false, 2000)
  }

  const beforeLeave =  (el) => {
    el.style.color = 'red';
    console.log('beforeLeave', el);
  }

  const leave =  (el) => {
    console.log('leave', el);
  }

  const afterLeave =  (el) => {
    console.log('afterLeave', el);
  }

</script>

<style>
  .about {
    max-width: 600px;
    margin: 20px auto;
  }

  .fade-enter-from, .fade-leave-to {
    opacity: 0;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .3s ease;
  }
</style>