<template>
  <div>
    <ul class="city-selector">
      <li
        @click="selectCity(city)"
        v-for="city in cities"
        :key="city.code"
        :class="{ isSelected: city.selected }"
      >
        {{ city.label }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CitySelector",
  data() {
    return {
      cities: [
        { code: "Seoul", label: "서울", selected: false },
        { code: "Tokyo", label: "도쿄", selected: false },
        { code: "Busan", label: "부산", selected: false },
        { code: "DaeGu", label: "대구", selected: false },
        { code: "Fukuoka", label: "후쿠오카", selected: false },
        { code: "Beijing", label: "베이징", selected: false },
      ],
    };
  },
  methods: {
    selectCity(city) {
      city.selected = !city.selected;
      this.$emit("selectCity", city);
    },
  },
};
</script>

<style scoped>
.city-selector {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
.city-selector li {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 0.05em solid #efefef;
  padding: 0.3em;
  cursor: pointer;
}
.isSelected {
  background: #fd1d1d;
  color: #fff;
}
</style>
