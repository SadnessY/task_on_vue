<template>
  <div>
    <div class="product">
      <div class="icons">
        <img @click="$emit('edit', product)" v-show="isHovered" @mouseover="isHovered = true" @mouseleave="isHovered = false" src="data:image/png;base64,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">
        <img @click="$emit('remove', product)" v-show="isHovered" @mouseover="isHovered = true" @mouseleave="isHovered = false" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAABmJLR0QA/wD/AP+gvaeTAAAC60lEQVRYhbWXy2sTURSHvzOJrcVm16Q+QSjowgfiwsYm7kVNdu4s2E0R/AMUClKQ/AmC3VgfS1capQru+rBd6M6NWlxYpCYFxfpMmxwXc5NMbmbITNucTTJnzj3nm9859w4jRLBjXO5J8Oe2IKMK+6zbX4BH6+y+9Y7HlbA5Y1EAhhgqgNwAEj63E0C2l82eFd6/CpszHgUAGAUQnMxrnix4bwyTywrMmpibYRM6EQH2A9jFAZYoznljwpp4L86Qv+igU8CBiGBhy62Aji9SnKl7WhRw4G73igPoQWDK64n7BLBIUeiCpckpcMjrizoDO272LlgGhgxpt+yz96JFgRqMAxvdLC7IuNfR1us0uU/AYUWPLPHsQxdhAP8Z+Or+yGC3i/sCCKy6/3TvThUZJn8yTa6U5tK1jgA0FKChwL3C2sJ0YW3eDpwurM3fL5Rnbb8bX66fjAhkgCRwOjSA42mBwClg5M5kqd+KHVEk63XcmSz1C5wFaRRTo6Ygqx0BamibAkAZIBHrSfoAt1hfr6bM35LHPWjlDgagSdkGsBnbTLXHW6ur8RSAmDVWrjAAbpB6ABQ1T6MdFYBaEkBVGgoImIEO0QLHVwExT+N0BpB6jPooEKIFTlMmzzZ0AUS1YwsQNS0QL4BZV+0MMM/TdeAX0Jchn3CTuU+jSIgWmDY57hqTYw/wd4mZHx0BjJUAakY6FQk/AzUxM9Cag8YBFw7AGsRaOTSAiWmqFrwDAgG0SWsWmxlAQsyAGyMqBqB+pLcPYCAA1nEcr8brWyqEAm5MLRarrxkE/1MwEECsrbherdQnOgzAAMDvfxtr3hxEaQGWAtcnUz+Bl4K+aQXVORDrZaRvUX1h1jRy+B3DEPxhYoaw+Uoemxg4bwddnUies31jE8ms5dq+Atux+jGsUYZQ4SOgAicy5I9utbhZexzQXcSWAwD9LU3uOXBhq8Utm1mk6Jsr8LtAqIwCD4BvW62q8F2Rh0LlSlDMfxEs6jg72VFDAAAAAElFTkSuQmCC">
      </div>
      <div class="image" :style="product.imageUrl"  @mouseover="isHovered = true" @mouseleave="isHovered = false"></div>
      <div class="title">{{ product.title }}</div>
      <div class="body">{{ product.body }}</div>
      <div class="price">{{ product.price }}</div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "ProdItem",
  data() {
    return {
      isHovered: false
    }
  },
  props: {
    product: {
      type: Object,
      required: true
    }
  },
  methods: {
    async getImage() {
      try {
        let response = await axios.get(this.product.imageUrl)
      } catch (e){
        alert('Ощибка')
      }
    }
  }
}
</script>

<style scoped>
.image {
  background-image: url("https://i.simpalsmedia.com/999.md/BoardImages/320x240/f3467ca2c4fe64f792206ca2ab476979.jpg?metadata=%7B%22image_type%22%3A+%22regular%22%2C+%22width%22%3A+1280%2C+%22signature%22%3A+%225322cbe0036eef3aef9900fdb44afa93a356ee3a%22%2C+%22metadata_version%22%3A+1%2C+%22height%22%3A+720%7D");
  width: 332px;
  height: 200px;
}
.title {
  font-family: 'Source Sans Pro';
  font-style: normal;
  font-weight: 600;
  font-size: 20px;
  line-height: 25px;
  color: #3F3F3F;
  margin-top: 20px;
  margin-bottom: 20px;
}
.icons {
  position: relative;
  right: 35px;
}
.body {
  font-family: 'Source Sans Pro';
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #3F3F3F;
  width: 300px;
  margin-bottom: 30px;
}
.price {
  font-family: 'Source Sans Pro';
  font-style: normal;
  font-weight: 600;
  font-size: 24px;
  line-height: 30px;
  color: #3F3F3F;
}
.product {
  width: 332px;
  height: 423px;
  justify-content: flex-start;
  flex-flow: column;
  text-align: left;
  margin-right: 20px;
}
img {
  width: 32px;
  height: 32px;
  position: relative;
  top: 25px;
  left: 300px;
}
</style>