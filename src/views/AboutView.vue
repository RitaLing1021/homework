<template>
  <div class="about">
    <h1>This is an about page</h1>
    <Board></Board>
  </div>
</template>

<script>
  import Board from '@/components/MessageBoard.vue';

  export default {

  components: {
      Board,
    },
  };
</script>
