<template>
  <div id="bg" class="bg">
    <span class="title">
      <span>Welcome to</span>
      <span>My Portfolio</span>
    </span>
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  components: {},
  mounted() {
    const CLASSNAME = '-visible'
    const TIMEOUT = 1000
    const target = document.getElementById('bg')

    setTimeout(() => {
      target.classList.add(CLASSNAME)
    }, TIMEOUT)
  },
})
</script>
<style lang='scss' scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans&display=swap');

.bg {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;
  width: 100%;
  height: calc(100vh - 80px);
  color: #fff;
}

.bg.-visible:before {
  transform: translate(0, 0);
}

.bg:before {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #a33e46;
  transform: translate(0, 100%);
  transition: transform cubic-bezier(0.215, 0.61, 0.355, 1) 0.6s;
  content: '';
}

/* テキストのスタイル */
.title {
  display: block;
  color: #fff;
  font-family: 'Josefin Sans', sans-serif;
  text-align: center;
}

.title span {
  display: block;
  opacity: 0;
  transition: transform cubic-bezier(0.215, 0.61, 0.355, 1) 1s,
    opacity linear 0.7s;
}

.title span:first-child {
  transform: translate(0, 40px);
  font-size: 20px;
  transition-delay: 0.25s;
}

.title span:last-child {
  margin-top: 18px;
  transform: translate(0, 30px);
  font-size: 48px;
  transition-delay: 0.45s;
}

.bg.-visible .title span {
  opacity: 1;
  transform: translate(0, 0);
}
</style>
