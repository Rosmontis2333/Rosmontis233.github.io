<script lang="ts">
import links from '@/data/links.json'
import { Link } from '@/logic/data'
import { Component, Vue } from 'vue-facing-decorator'


@Component({})
export default class Avatar extends Vue {
  li = [] as Link[]

  mounted() {
    this.li = links as Link[]
  }
}
</script>

<template>
  <div class="avatar">
    <div class="left">
      <img alt="avatar" src="/img/ros.jpg" />
    </div>
    <div class="right">
      <h1>Rosmontis Here!</h1>
      <div class="links">
        <router-link v-for="l of li" :to="l.url" :key="l.name">{{ l.name }}</router-link>
      </div>
    </div>
  </div>
  <hr />
</template>

<style lang="scss">
@import '@/css/mocha';
@import '@/css/motion';

.avatar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: row;
  flex-wrap: nowrap;

  .left {
    flex: 1;
    display: block;
    width: 200px;
    height: 200px;
    border-radius: 100px;
    margin: 0.5rem auto;
    padding: 2rem;

    img {
      object-fit: contain;
      width: 200px;
      height: 200px;
      margin: auto;
      border-radius: 100px;
    }
  }

  .right {
    flex: 2;
    display: flex;
    width: fit-content;
    height: 200px;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;

    h1 {
      font-size: 2rem;
      text-align: start;
      flex: 1;
      padding-top: 1.5rem;
      transition: all 0.5s $ease-in-out-cric;

      &:hover {
        filter: drop-shadow(0px 0px 5px $lavender);
      }
    }

    .links {
      flex: 1;
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: space-around;
      align-items: center;
      width: 60%;

      a {
        transition: all 0.5s $ease-in-out-cric;
        margin: auto 1rem;

        &:hover {
          filter: drop-shadow(0px 0px 2px $flamingo);
        }
      }
    }
  }
}

@media screen and (max-width: 552px) {
  .avatar {
    flex-direction: column;
    margin-bottom: 2rem;
  }
}
</style>
