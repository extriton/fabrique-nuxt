<template>
  <div class="condition-status">
    <div class="condition-status__label">
        <span class="prefix" v-show="statusIndex > 1">или</span>
        <span>Статус {{ statusIndex }}</span>
    </div>
    <div class="condition-status__input">
        <select class="form-control" v-model="statusObj.id">
            <option
                v-for="(item, index) in statusesList"
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
import statusesList from '~/constants/status'

export default {
  props: {
    statusObj: {
        type: Object,
        required: true
    },
    statusIndex: {
        type: Number,
        required: true
    }
  },
  data () {
    return {
        statusesList: statusesList
    }
  }
}
</script>

<style lang="scss">
.condition-status {
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
