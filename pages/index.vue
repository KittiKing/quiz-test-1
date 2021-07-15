<template>
  <Row type="flex" justify="space-between">
    <Col class="height-column border-right" style="width: 200px">
      <InputNumber
        v-model="inputValue"
        :min="1"
        @on-change="handleSelectType"
      />
    </Col>
    <Col class="height-column" style="margin-right: auto">
      <Select
        v-model="selectedType"
        style="width: 200px"
        @on-change="handleSelectType"
      >
        <Option
          v-for="(type, index) in typeOfNumber"
          :key="index"
          :value="type"
          :label="type"
        >
        </Option>
      </Select>
    </Col>
    <Col class="height-column border-left" style="width: 300px">
      <span v-if="inputValue">
        {{ answer }}
      </span>
    </Col>
  </Row>
</template>
<script>
export default {
  data() {
    return {
      inputValue: null,
      selectedType: null,
      typeOfNumber: ['isPrime', 'isFibonacci'],
      answer: null
    }
  },
  methods: {
    handleSelectType() {
      if (this.selectedType === 'isPrime') {
        this.answer = this.inputValue % 2 === 0
      } else if (this.selectedType === 'isFibonacci') {
        const a = 5 * Math.pow(this.inputValue, 2) + 4
        const b = 5 * Math.pow(this.inputValue, 2) - 4
        const result = Math.sqrt(a) % 1 === 0
        const res = Math.sqrt(b) % 1 === 0
        this.answer = result || res === true
      }
    }
  }
}
</script>

<style>
.height-column {
  min-height: 100vh;
}
.border-right {
  border-right: groove;
}
.border-left {
  border-left: groove;
}
</style>
