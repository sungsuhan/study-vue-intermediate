<template>
  <div>
    <select name="" id="" @change="changeCity($event)" v-model="selectedCity">
      <option value="">==도시선택==</option>
      <option :value="city.code" :key="city.code" v-for="city in cityList">
        {{city.title}}
      </option>
    </select>
    <select name="" id="">
      <option :value="dong.dongCode" :key="dong.dongCode" v-for="dong in selectedDongList">
        {{dong.dongTitle}}
      </option>
    </select>
    <select name="" id="">
      <option :value="dong.dongCode" :key="dong.dongCode" v-for="dong in selectedDongList = dongList.filter(
        (dong) => dong.cityCode === selectedCity)">
        {{dong.dongTitle}}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      selectedCity: '',
      cityList: [
        { code: '02', title: '서울' },
        { code: '031', title: '경기' },
        { code: '064', title: '제주' }
      ],
      dongList: [
        { cityCode: '02', dongCode: '1', dongTitle: '서초 1동' },
        { cityCode: '02', dongCode: '2', dongTitle: '서초 2동' },
        { cityCode: '02', dongCode: '3', dongTitle: '서초 3동' },
        { cityCode: '02', dongCode: '4', dongTitle: '서초 4동' },
        { cityCode: '031', dongCode: '1', dongTitle: '판교 1동' },
        { cityCode: '031', dongCode: '2', dongTitle: '판교 2동' },
        { cityCode: '031', dongCode: '3', dongTitle: '판교 3동' },
        { cityCode: '064', dongCode: '1', dongTitle: '애월 1동' },
        { cityCode: '064', dongCode: '2', dongTitle: '애월 2동' }
      ],
      selectedDongList: [

      ]
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {
    changeCity(event) {
      console.log(event.target.tagName)
      this.selectedDongList = this.dongList.filter(
        (dong) => dong.cityCode === this.selectedCity)
    }
  }
}
</script>

<style>
</style>
