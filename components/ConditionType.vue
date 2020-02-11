<template>
  <div class="condition-type">
    <div class="condition-type__label">
        <span class="prefix" v-show="typeIndex > 1">или</span>
        <span>Тип {{ typeIndex }}</span>
    </div>
    <div class="condition-type__input">
        <select class="form-control" v-model="typeObj.id">
            <option
                v-for="(item, index) in typesList"
                :key="index"
                :value="item.value"
            >
                {{ item.text }}
            </option>
        </select>
    </div>
  </div>
</template>

<script>
import typesList from '~/constants/type'

export default {
  props: {
    typeObj: {
        type: Object,
        required: true
    },
    typeIndex: {
        type: Number,
        required: true
    }
  },
  data () {
    return {
        typesList: typesList
    }
  }
}
</script>

<style lang="scss">
.condition-type {
  width: 100%;
  padding: 0 20px;
  margin-bottom: 15px;
  &__label {
    display: inline-block;
    width: 30%;
    .prefix {
        display: inline-block;
        padding: 5px 10px;
        background-color: rgba(0, 0, 0, 0.1);
        border-radius: 3px;
        margin-right: 15px;
    }
  }
  &__input {
    display: inline-block;
    width: 50%;
  }
}
</style>
