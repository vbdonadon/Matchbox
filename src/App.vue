<template>
    <div style="width: 100%; height: 100%;">
      <header id="header">
        <div class="hdr">
          <img src="./assets/logo.png" class="hdr__logo" alt="Matchbox">  
          <div class="hdr__whitebox">
            <h1 class="hdr__whitebox__title">ranking</h1>
          </div>
        </div>
      </header>

      <section id="ranking">
        <ul class="list">
          <li class="rkg" v-for="(item, index) in dados.data" :key="item.__id">
            <div class="rkg__block">
              <img :src="item.picture" alt="">
            </div>
            <span class="rkg__index">{{index + 1}}</span>
            <div class="rkg__people">
              <h4 class="rkg__people__name">Marcel Vecelic</h4>
              <p class="rkg__people__ocup">Product Designer</p>
            </div>
            
            <div class="rkg__rattings">
              <div class="rkg__rattings__head">
                <p class="rkg__rattings__head__title">Gostam</p>
                <p class="rkg__rattings__head__porc">45%</p>
              </div>
              <div class="rkg__rattings__head">
                <p class="rkg__rattings__head__title">Não Gostam</p>
                <p class="rkg__rattings__head__porc">55%</p>
              </div>
            </div>
          </li>
        </ul>
      </section>
    </div>

</template>

<script>
import { json } from '@/data/matchboxbrasil.js'

export default {
  data(){
    return {
      dados: json,
    } 
  },
  methods: {
    console(){
      console.log(json)
    }
  },
  mounted(){
    this.console();
  }
};
</script>

<style lang="scss">
* {
  margin: 0px;
  padding: 0px;
  font-family: Arial;
}

html {
  height: 100vh;
}

body {
  background-color: #453995;
  display: flex;
  align-items: center;
  height: 100vh;
}

#header {
  @include mainContainer(342px);

  .hdr {
    &__logo {
      margin-bottom: 25px;
      display: block;
    }

    &__whitebox {
      background-color: #fff;
      max-width: 342px;
      height: 52px;
      border-radius: 3px;
      display: flex;
      justify-content: center;
      align-items: center;

      &__title {
        font-family: Arial;
        color: #272727;
        font-weight: bold;
        font-size: 28px;
      }
    }
  }
}

#ranking {
  @include mainContainer(342px);
  margin-top: 10px;

  .list {
    border-radius: 3px;
    // overflow: hidden;
  }

  .rkg {
    background-color: #fff;
    padding: 15px;
    display: flex;
    flex-direction: row;
    transition: 0.4s all ease;
    position: relative;

    &:hover {
      background-color: #f2f1f1;
    }

    &__block {
      display: block;
      width: 66px;
      height: 66px;
      border: 2px solid #6bbef1;
      border-radius: 33px;
      overflow: hidden;
    }

    &__index {
      position: relative;
      top: 50px;
      right: 23px;
      border: 1px solid #777575;
      border-radius: 11px;
      background-color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      width: 20px;
      height: 20px;
      font-size: 12px;
      color: #707070;
    }

    &__people {
      display: flex;
      justify-content: center;
      flex-direction: column;

      &__name {
        display: block;
        font-size: 18px;
        color: #272727;
      }

      &__ocup {
        font-size: 12px;
        color: #909090;
      }
    }

    &__rattings {
      background-color: #fff;
      display: flex;
      align-items: flex-start;
      position: absolute;
      border-radius: 6px;
      width: 149px;
      height: 49px;
      top: 26px;
      right: -170px;

      &__head {
        width: 45%;

        &:last-child {
          width: 55%;
        }

        &__title {
          background-color: #df595d;
          color: #fff;
          padding-top: 3px;
          padding-bottom: 3px;
          font-weight: bold;
          font-size: 10px;
          text-transform: uppercase;
          text-align: center;
        }

        &__porc {

          padding-top: 7px;
          text-align: center;
        }
      }
    }
  }
}
</style>
