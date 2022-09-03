<template>
  <div>
    <input type="checkbox" v-model="val" value="A" />
    <input type="checkbox" v-model="val" value="B" />
    <input type="checkbox" v-model="val" value="C" />
    <p>{{ val }}</p>
    <div>
      <input type="radio" v-model="radio_val" value="RADIO1" />
      <input type="radio" v-model="radio_val" value="RADIO2" />
      <input type="radio" v-model="radio_val" value="RADIO3" />
      <p>{{ radio_val }}</p>
    </div>
    <div>
      <select
        v-for="n in selectCnt"
        :key="n"
        v-model="selectExcludes[n - 1]"
        class="select"
      >
        <option value="undefined">선택 안함</option>
        <option
          v-for="(item, index) in selectList"
          :key="index"
          :disabled="isVisible(item.id)"
          :value="item.id"
        >
          {{ item.name }}
        </option>
      </select>
      <br /><br />
      <input type="button" value="현재 데이터 확인" @click="dataCheck" />
      <br /><br />
      <input
        type="button"
        value="첫번째 select data 111"
        @click="setFirstData"
      />
      {{ selectExcludes }}
    </div>
  </div>
</template>

<script>
export default {
  name: "CheckBoxTest",
  components: {},
  data() {
    return {
      val: ["A"],
      radio_val: "RADIO1",
      selectCnt: 2,
      selectList: [
        {
          id: "111",
          name: "name111",
        },
        {
          id: "222",
          name: "name222",
        },
        {
          id: "333",
          name: "name333",
        },
      ],
      selectExcludes: [],
    };
  },
  methods: {
    isVisible(data) {
      let returnFlag = false;
      for (const i in this.selectExcludes) {
        if (this.selectExcludes[i] === data) {
          returnFlag = true;
        }
      }
      return returnFlag;
    },
    dataCheck() {
      console.log(this.selectExcludes);
    },
    setFirstData() {
      this.$set(this.selectExcludes, 0, "111");
    },
  },
};
</script>

<style></style>
