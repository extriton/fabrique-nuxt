<template>
  <section class="page-container">
    <main-navbar/>
    <div class="page-container__body">
      <div class="page-container__caption">Добавить опрос</div>
      <Condition
        v-for="(item, index) in conditions"
        :key="index"
        :condition-obj="item"
        :condition-index="index + 1"
        @delete_condition="deleteCondition"
      />
      <button
        type="button"
        class="page-container__add-button"
        @click="addCondition"
      >
        <p class="icon">+</p>
        <p class="desc">
          Нажмите, чтобы добавить новое условие выборки.<br />
          Все условия связываются между собой логическим "И"
        </p>
      </button>
    </div>
    <div class="page-container__footer">
      <div class="left-column">
        <button
          type="button"
          class="btn btn-outline-dark button-test"
          @click="onTest"
        >
          Протестировать опрос
        </button>
      </div>
      <div class="right-column">
        <button
          type="button"
          class="btn btn-success button-next"
        >
          Далее
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import MainNavbar from '~/components/MainNavbar.vue'
import Condition from '~/components/Condition.vue'

export default {
  components: {
    MainNavbar,
    Condition
  },
  data () {
    return {
      conditions: []
    }
  },
  methods: {
    addCondition () {
      this.conditions.push({ value: '', type: '', title: '', status: '', items: [] })
    },
    deleteCondition (data) {
      this.conditions.splice(data.index, 1)
    },
    onTest () {
      console.log('Test')
    }
  }
}
</script>

<style lang="scss">
.page-container {
  width: 60%;
  margin: 0 auto;
  &__body {
    border-top: 1px solid #E3F5A4;
  }
  &__caption {
    font-size: 22px;
    color: #AEAEAE;
    padding: 10px 20px;
  }
  &__add-button {
    display: block;
    width: calc(100% - 40px);
    margin: 20px auto;
    padding: 0 20px;
    border: 2px solid #E5ECF0;
    border-radius: 4px;
    background-color: transparent;
    color: #28AF44;
    .icon {
      font-size: 72px;
      line-height: 72px;
      margin: 0;
    }
  }
  &__footer {
    padding: 20px;
    background-color: #aaa;
    .left-column {
      display: inline-block;
      width: 50%;
      text-align: left;
    }
    .right-column {
      display: inline-block;
      width: 50%;
      text-align: right;
    }
  }
}
</style>
