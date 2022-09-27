<template>
  <div>
    <select>
      <option value="">По умолчанию</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "MySelect",
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>
select {
  width: 121.49px;
  height: 36px;
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  font-family: 'Source Sans Pro';
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
  text-align: center;
  position: relative;
  display: flex;
  left: 1025px;
  bottom: 10px;
}
</style>