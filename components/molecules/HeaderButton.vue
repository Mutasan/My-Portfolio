<template>
  <div>
    <div class="section-area">
      <ul class="navi-area">
        <a href=""><li>Profile</li></a>
        <a href=""><li>Posts</li></a>
        <a href=""><li>Career</li></a>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class HeaderButton extends Vue {}
</script>

<style lang="scss" scoped>
* {
  padding-inline-start: 0px;
}

ol,
ul,
li {
  list-style: none;
}

ul {
  list-style-type: none;
  margin-block-start: 0em;
  margin-block-end: 0em;
  padding-inline-start: 0px;
  height: 100%;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}

a {
  text-decoration: none;
  width: 260px;
  height: 100%;
  line-height: 70px;
  position: relative;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  text-align: center;

  &::before {
    content: '';
    width: 2px;
    height: 32px;
    background-color: #c3ccd5;
    border-radius: 8px;
    position: absolute;
    right: 0;
    top: 50%;
    -webkit-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  &:last-child::before {
    content: none;
  }
}

.navi-area {
  background-color: #fff;
  width: 800px;
  height: 72px;
  margin: 0 auto;
  border: solid 1px #000;
  border-radius: 4px;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  position: relative;
  z-index: 10;
}

.section-area {
  position: relative;
  width: 1040px;
  height: 100%;
  margin: 0 auto;
}
</style>
