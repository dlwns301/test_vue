<template>
  <div class="card">
    <div class="card-body">
      {{ classes }}
      <h5 class="card-title red" >Card title</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">Card subtitle</h6>
      <p class="card-text" :class="classes.red">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
      <a href="#" class="card-link">Card link</a>
      <a href="#" class="card-link">Another link</a>
    </div>
  </div>
</template>

<script>
export default {
  setup () {
  
    return {}
  }
}
</script>

<!-- scoped 는 내부에서만 사용 원할때 사용한다. -->
<!-- <style scoped> 
.red {
  color : red;
}
</style> -->

<!-- module 속성을 붙이면 style의 내장객체가 된다 -->
<style module="classes">
.red {
  color: blue;
}
</style>