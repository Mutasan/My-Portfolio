<template>
  <div id="background" class="background">
    <div>
      <span class="title">
        <span>Welcome to</span>
        <span>My Portfolio</span>
      </span>
    </div>
    <div>
      <span id="content" class="content">
        <img src="https://placehold.jp/480x360.png" />
      </span>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

type Data = {
  isShowContents: Boolean
}

export default Vue.extend({
  data(): Data {
    return {
      isShowContents: false,
    }
  },
  mounted() {
    const VISIBLE_CLASSNAME = '-visible'
    const INVISIBLE_CLASSNAME = '-invisible'
    const TIMEOUT = 1000
    const background = document.getElementById('background')
    const content = document.getElementById('content')

    setTimeout(() => {
      background!.classList.add(VISIBLE_CLASSNAME)
      setTimeout(() => {
        background!.classList.add(INVISIBLE_CLASSNAME)
        background!.classList.remove(VISIBLE_CLASSNAME)
        setTimeout(() => {
          background!.classList.remove('background')
          content!.classList.add(VISIBLE_CLASSNAME)
        }, TIMEOUT * 2)
      }, TIMEOUT * 2)
    }, TIMEOUT)
  },
})
</script>
<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans&display=swap');

.background {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;
  width: 100%;
  height: calc(100vh - 80px);
  color: #fff;
}

.background.-visible:before {
  transform: translate(0, 0);
}

.background.-invisible:before {
  transition: 1.5s;
  transform: translate(0, -100%);
}

.background:before {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(190, 180, 72);
  transform: translate(0, 100%);
  transition: transform cubic-bezier(0.215, 0.61, 0.355, 1) 0.6s;
  content: '';
}

@keyframes tooltipShow {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

.content {
  display: none;
}

.content.-visible {
  display: block;
  animation: tooltipShow 0.3s;
  color: black;
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

.background.-visible .title span {
  opacity: 1;
  transform: translate(0, 0);
}

.background.-invisible .title span {
  transform: translate(0, 0);
  transition: 1s;
  visibility: hidden;
}
</style>
