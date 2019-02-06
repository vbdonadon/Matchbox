<template>
    <section id="ranking">
        <ul class="list">
          <li class="rkg" 
          :class="[{'none': isActive}, {'active': isActive}]" 
          @click="isActive = !isActive" 
          v-for="(item, index) in dados.data" 
          :key="item.__id">
            <div class="rkg__block">
              <img :src="item.picture">
            </div>
            <span class="rkg__index">{{index + 1}}</span>
            <div class="rkg__people">
              <h4 class="rkg__people__name">{{ThreatName(item.name)}}</h4>
              <p class="rkg__people__ocup">{{item.description}}</p>
            </div>
            
            <div class="rkg__rattings" :class="[{'none': isActive}]" >
              <div class="rkg__rattings__head">
                <p class="rkg__rattings__head__title">Gostam</p>
                <p class="rkg__rattings__head__porc">{{ToPositive(item.positive, item.negative)}}</p>
              </div>
              <div class="rkg__rattings__head">
                <p class="rkg__rattings__head__title">Não Gostam</p>
                <p class="rkg__rattings__head__porc">{{ToNegative(item.positive, item.negative)}}</p>
              </div>
            </div>
          </li>
        </ul>
    </section>
</template>

<script>
import { Json } from '@/data/matchboxbrasil.js'

export default {
    data(){
    return {
      isActive: false,
      dados: Json,
    } 
  },
  methods: {
    ThreatName(name){
      let nameToArray = name.split(' ')
      return `${nameToArray[0]} ${nameToArray[1]}`
    },
    ToPositive(positive, negative){
      this.positive = positive;
      this.negative = negative;
      let OnePercent = (this.positive + this.negative)/100;
      let NumPositive = this.positive/OnePercent;
      return `${Math.round(NumPositive)}%`
    },
    ToNegative(positive, negative){
      this.positive = positive;
      this.negative = negative;
      let OnePercent = (this.positive + this.negative)/100;
      let NumNegative = this.negative/OnePercent;
      return `${Math.round(NumNegative)}%`
    },
  },
}
</script>

<style lang="scss">
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
    cursor: pointer;
    
    &.active {
      background-color: #6bbef1;
    }

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
      top: 26px;
      right: -170px;

      &.none {
        display: none;
      }

      &::before {
        content: '';
        display: block;
        width: 10px;
        height: 10px;
        background-color: #fff;
        position: absolute;
        top: 27px;
        left: -5px;
        transform: rotate(45deg)
      }

      &__head {
        width: 45%;

        &:last-child {
          width: 55%;
          border-left: 1px solid #8c8b8b;
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
          color: #909090;
          font-weight: bold;
          padding-top: 7px;
          padding-bottom: 7px;
          text-align: center;
        }
      }
    }
  }
}
</style>
