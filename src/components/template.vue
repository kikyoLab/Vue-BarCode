<template>
  <el-button type="primary" icon="el-icon-star-on" size="small" @click="tmpl()"
    >模板
  </el-button>
</template>

<script>
export default {
  name: "Template",
  methods: {
    tmpl: function() {
      console.log("see tmpl");
    }
  }
};
</script>
