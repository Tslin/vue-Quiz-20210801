<template>
  <table class="table table-striped">
    <thead>
      <tr>
        <th>#</th>
        <th>場站名稱</th>
        <th>場站區域</th>
        <th>
          <div @click="passSort('sbi')">
            目前可用車輛
            <i
              v-if="isSort === 'sbi'"
              :class="{
                'fa-sort-asc': !isDesc,
                'fa-sort-desc': isDesc,
              }"
              class="fa"
              aria-hidden="true"
            ></i>
            <i v-else class="fa fa-sort" aria-hidden="true"></i>
          </div>
        </th>
        <th>
          <div @click="passSort('tot')">
            總停車格
            <i
              v-if="isSort === 'tot'"
              :class="{
                'fa-sort-asc': !isDesc,
                'fa-sort-desc': isDesc,
              }"
              class="fa"
              aria-hidden="true"
            ></i>
            <i v-else class="fa fa-sort" aria-hidden="true"></i>
          </div>
        </th>
        <th>資料更新時間</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="s in uBikeData" :key="s.sno">
        <td>{{ s.sno }}</td>
        <td>{{ s.sna }}</td>
        <td>{{ s.sarea }}</td>
        <td>{{ s.sbi }}</td>
        <td>{{ s.tot }}</td>
        <td>{{ timeFormat(s.mday) }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["uBikeData", "isSort", "isDesc"],
  methods: {
    timeFormat(val) {
      // 時間格式
      const pattern = /(\d{4})(\d{2})(\d{2})(\d{2})(\d{2})(\d{2})/;
      return val.replace(pattern, "$1/$2/$3 $4:$5:$6");
    },
    passSort(option) {
      this.$emit("passSort", option);
    },
  },
};
</script>

<style>
.fa-sort {
  color: #aaa;
}
</style>
