<template>
  <div class="condition-range">
    <div class="condition-range__label">
        <span class="prefix" v-show="rangeIndex > 1">или</span>
        <span>Диапазон {{ rangeIndex }}</span>
    </div>
    <div class="condition-range__input">
        от
        <input
        class="form-control"
            type="number"
            min="0"
            max="100"
            step="1"
            v-model="rangeObj.min"
        />
        до
        <input
            class="form-control"
            type="number"
            min="0"
            max="100"
            step="1"
            v-model="rangeObj.max"
        />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    rangeObj: {
        type: Object,
        required: true
    },
    rangeIndex: {
        type: Number,
        required: true
    }
  }
}
</script>

<style lang="scss">
.condition-range {
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
    & > input {
        display: inline-block;
        margin-right: 15px;
        width: 100px;
    }
  }
}
</style>
