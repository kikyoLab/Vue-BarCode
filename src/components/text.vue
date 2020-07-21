<template>
  <el-button type="primary" icon="el-icon-edit" size="small" @click="CrtText()"
    >文本
  </el-button>
</template>

<script>
export default {
  name: "CrtText",
  methods: {
    CrtText: function() {
      console.log("text");
    }
  }
};
</script>
