<template>
  <div class="wrapper">
    <div id="background" class="background">
      <div>
        <span id="title" class="title">
          <span>Welcome to</span>
          <span>My Portfolio</span>
        </span>
      </div>
      <div>
        <span id="content" class="content">
          <div>
            <v-img height="100vh" src="bike.jpg" class="content__back" />
            <h1 class="content__title">Takumi Kitamura's Portfolio</h1>
            <v-img src="me.png" class="content__me" />
            <!-- 矢印 -->
            <span class="content__scroll">SCROLL</span>
            <div class="content__arrow" />
          </div>
          <div></div>
        </span>
      </div>
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
    const title = document.getElementById('title')

    setTimeout(() => {
      background!.classList.add(VISIBLE_CLASSNAME)
      setTimeout(() => {
        background!.classList.add(INVISIBLE_CLASSNAME)
        background!.classList.remove(VISIBLE_CLASSNAME)
        setTimeout(() => {
          title!.classList.add(INVISIBLE_CLASSNAME)
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
  height: 100vh;
  color: #fff;
}

.background.-visible:before {
  transform: translate(0, 0);
}

.background.-invisible:before {
  transition: 1.5s;
  transform: translate(0, -100%);
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

@keyframes fuwafuwa {
  0% {
    transform: translateY(-50px);
  }
  50% {
    transform: translateY(-30px);
  }
  100% {
    transform: translateY(-50px);
  }
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
  position: relative;
  &__back {
    width: 100vw;
    margin: 0 auto;
    filter: brightness(30%);
  }
  &__me {
    position: absolute;
    border-radius: 50%;
    width: 320px;
    height: 320px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    -webkit-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
  }
  &__scroll {
    position: absolute;
    animation: fuwafuwa 2s infinite;
    backface-visibility: hidden;
    color: #eee;
    font-size: 36px;
    bottom: 10%;
    left: 50%;
    transform: translate(-50%, -50%);
    -webkit-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
  }
  &__title {
    position: absolute;
    color: #eee;
    font-size: 48px;
    top: 25%;
    left: 50%;
    transform: translate(-50%, -50%);
    -webkit-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
  }
  // 矢印
  &__arrow {
    position: absolute;
    bottom: 5%;
    left: 49%;
    transform: translate(-50%, -50%);
    -webkit-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    width: 30px;
    height: 30px;
    border: 5px solid;
    border-color: transparent transparent #fff #fff;
    transform: rotate(-45deg);
  }
}

.content.-visible {
  display: block;
  animation: tooltipShow 0.8s;
  color: black;
}

/* テキストのスタイル */
.title {
  display: block;
  color: #fff;
  font-family: 'Josefin Sans', sans-serif;
  text-align: center;
}

.title.-invisible {
  display: none;
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
// @media screen and (min-width: 768px) {
//   .wrapper {
//     margin: 0 80px;
//   }
// }
</style>
