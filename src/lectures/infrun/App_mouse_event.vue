<template>
  <div>
    <div id="modifiers">
      <div @click="clickDiv">
        DIV영역
        <p @click="clickP">
          P 영역
          <span @click.stop="clickSpan">
            SPAN 영역
          </span>
          
        </p>
      </div>
      <a href="https://www.naver.com" @click.prevent.stop="clickA">a 영역</a>
    </div>
  </div>
</template>

<script>
export default {
  setup () {
    const clickDiv = () => {
      console.log('clickDiv');
      location.href = 'https://www.naver.com';
    }
    const clickP = () => {
      console.log('clickP');
      alert('p태그 클릭');
    }
    const clickSpan = (e) => {
      console.log('clickSpan');
      //e.stopPropagation(); => @click.stop과 같다.
      alert('좋아요');
    }
    const clickA = () => {
      console.log('clickA');
      alert('네이버로 이동');
    }

    return {clickDiv,clickP,clickSpan,clickA}
  }
}
</script>

<style scoped>
#modifiers div,
#modifiers p,
#modifiers span {
  padding: 40px;
}

#modifiers div {
  background-color: yellow
}

#modifiers p {
  background-color: blue
}

#modifiers span {
  background-color: green
}
</style>