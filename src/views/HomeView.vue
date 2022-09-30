<template>
  <div class="home">
    <h1>這是一個留言板作業顆顆</h1>
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
