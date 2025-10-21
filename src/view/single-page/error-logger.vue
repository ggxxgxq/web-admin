<template></template>

<script>
import dayjs from "dayjs";
import { mapMutations } from "vuex";
export default {
  name: "error_logger_page",
  data() {
    return {
      columns: [
        {
          type: "index",
          title: "序号",
          width: 100,
        },
        {
          key: "mes",
          title: "信息",
        },
        {
          key: "url",
          title: "URL",
        },
        {
          key: "time",
          title: "时间",
          sortable: true,
          sortType: "desc",
        },
      ],
    };
  },
  computed: {
    errorList() {
      return this.$store.state.app.errorList;
    },
  },
  methods: {
    ...mapMutations(["setHasReadErrorLoggerStatus"]),
    exportData() {
      this.$refs.table.exportCsv({
        filename: "错误日志.csv",
      });
    },
  },
  activated() {
    this.setHasReadErrorLoggerStatus();
  },
  mounted() {
    this.setHasReadErrorLoggerStatus();
  },
};
</script>

<style>
</style>
