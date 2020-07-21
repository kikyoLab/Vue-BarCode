<template>
  <el-button
    type="primary"
    icon="el-icon-s-ticket"
    size="small"
    @click="CrtQarCode()"
    >二维码
  </el-button>
</template>

<script>
export default {
  name: "CrtQarCode",
  methods: {
    CrtQarCode: function() {
      console.log("qarcode");
    }
  }
};
</script>
