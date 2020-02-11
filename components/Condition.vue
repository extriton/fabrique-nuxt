<template>
  <div class="condition">
    <span class="prefix" v-show="conditionIndex > 1">И</span>
    <div class="condition__label">
        <span>Условие {{ conditionIndex }}</span>
    </div>
    <div class="condition__input">
        <select class="form-control" v-model="selectedValue" @change="onChange">
            <option value="" disabled>Выберите условие</option>
            <option
                v-for="(item, index) in conditionsList"
                :key="'i' + index"
                :value="item.value"
            >
                {{ item.text }}
            </option>
        </select>
    </div>
    <div v-if="conditionObj.value" class="condition__body">
        <div v-if="conditionObj.type == 'range'">
            <ConditionRange
                v-for="(item, index) in conditionObj.items"
                :key="index"
                :range-obj="item"
                :range-index="index + 1"
            />
        </div>
        <div v-if="conditionObj.type == 'type'">
            <ConditionType
                v-for="(item, index) in conditionObj.items"
                :key="index"
                :type-obj="item"
                :type-index="index + 1"
            />
        </div>
        <div v-if="conditionObj.type == 'status'">
            <ConditionStatus
                v-for="(item, index) in conditionObj.items"
                :key="index"
                :status-obj="item"
                :status-index="index + 1"
            />
        </div>
    </div>
    <div class="condition__footer">
        <button
            v-if="conditionObj.value"
            type="button"
            class="btn btn-outline-success button-add"
            @click="onAddItem"
        >
            Добавить {{ conditionObj.title }}
        </button>
        <button
            type="button"
            class="btn btn-danger button-delete"
            @click="onDeleteCondition"
        >
            Удалить условие
        </button>
    </div>
  </div>
</template>

<script>
import conditionsList from '~/constants/condition'

import ConditionRange from '~/components/ConditionRange.vue'
import ConditionType from '~/components/ConditionType.vue'
import ConditionStatus from '~/components/ConditionStatus.vue'

export default {
  components: {
    ConditionRange,
    ConditionType,
    ConditionStatus
  },
  props: {
    conditionObj: {
        type: Object,
        required: true
    },
    conditionIndex: {
        type: Number,
        required: true
    }
  },
  computed: {
    conditionItems () {
        return this.conditionObj.items
    }
  },
  data () {
    return {
        selectedValue: "",
        conditionsList: conditionsList
    }
  },
  methods: {
    onChange () {
        for (let i = 0; i < this.conditionsList.length; i++) {
            if (this.selectedValue == this.conditionsList[i].value) {
                this.conditionObj.value = this.conditionsList[i].value
                this.conditionObj.type = this.conditionsList[i].type
                this.conditionObj.title = this.conditionsList[i].title
                this.conditionObj.items = []
                break
            }
        }
    },
    onDeleteCondition () {
        this.$emit('delete_condition', { index: this.conditionIndex - 1 })
    },
    onAddItem () {
        if (this.conditionObj.type == 'range') {
            this.conditionObj.items.push({ min: 0, max: 0 })
        }
        if (this.conditionObj.type == 'type') {
            this.conditionObj.items.push({ id: 1 })
        }
        if (this.conditionObj.type == 'status') {
            this.conditionObj.items.push({ id: 1 })
        }
    }
  }
}
</script>

<style lang="scss">
.condition {
  width: 100%;
  padding: 20px 20px 30px 20px;
  margin-bottom: 15px;
  position: relative;
  border-bottom: 1px solid #ccc;
  & > .prefix {
    position: absolute;
    top: -32px;
    left: 30px;
    display: inline-block;
    padding: 5px 10px;
    background-color: #E5F0FA;
    border-radius: 3px;
    margin-right: 15px;
    z-index: 5;
  }
  &__label {
    display: inline-block;
    width: 30%;
  }
  &__input {
    display: inline-block;
    width: 50%;
  }
  &__body {
      margin: 20px 0;
  }
  &__footer {
    display: inline-block;
    width: 100%;
    padding-left: 30%;
    margin-top: 40px;
    .button-add {
        float: left;
    }
    .button-delete {
        float: right;
    }
  }
}
</style>
