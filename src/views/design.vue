<template>
  <el-container>
    <el-header>
      <span class="hiddenText">正在操作XXX模板</span>
      <CrtText />
      <CrtBarCode :num="num" @success="success()" />
      <CrtQarCode />
      <el-button
        type="primary"
        icon="el-icon-picture"
        size="small"
        @click="CrtPic()"
        >图片
      </el-button>
      <el-button
        type="primary"
        icon="el-icon-minus"
        size="small"
        @click="CrtLine()"
        >线条
      </el-button>
      <el-button
        type="primary"
        icon="el-icon-full-screen"
        size="small"
        @click="CrtBox()"
        >边框
      </el-button>
      <el-button
        type="primary"
        icon="el-icon-printer"
        size="small"
        @click="print()"
        >打印
      </el-button>
      <Tmpl />
      <el-button
        type="primary"
        icon="el-icon-folder-checked"
        size="small"
        @click="tmplSave()"
        >模板保存
      </el-button>
      <el-button
        type="primary"
        icon="el-icon-folder-add"
        size="small"
        @click="tmplSaveAs()"
        >模板另存
      </el-button>
      <el-button type="primary" icon="el-icon-close" size="small" @click="del()"
        >删除
      </el-button>
      <el-button
        type="primary"
        icon="el-icon-magic-stick"
        size="small"
        @click="delAll()"
        >清空
      </el-button>
    </el-header>
    <el-container>
      <el-main>
        <div id="printMain">
          <div
            v-for="(i, index) in num"
            :id="'code' + i"
            :key="index"
            style="position: fixed; margin: 0;display：inline; overflow: hidden;z-index:2"
            class="BarCodedbclick refbox"
          >
            div
            <svg
              :id="'BarCode' + i"
              class="barcode"
              jsbarcode-format="upc"
              jsbarcode-value="123456789012"
              jsbarcode-textmargin="0"
              jsbarcode-fontoptions="bold"
            ></svg>
          </div>
        </div>
      </el-main>
      <el-aside width="240px">
        <el-form
          :label-position="labelPosition"
          label-width="80px"
          :model="formLabelAlign"
        >
          <el-form-item label="模板框长">
            <el-input v-model="formLabelAlign.modalHeight"></el-input>
          </el-form-item>
          <el-form-item label="模板库宽">
            <el-input v-model="formLabelAlign.modalWidth"></el-input>
          </el-form-item>
          <el-form-item label="标签列数">
            <el-input v-model="formLabelAlign.labelRow"></el-input>
          </el-form-item>
          <el-form-item label="标签间距">
            <el-input v-model="formLabelAlign.labelLR"></el-input>
          </el-form-item>
          <el-form-item label="标签边距">
            <el-input v-model="formLabelAlign.labelTB"></el-input>
          </el-form-item>
          <el-form-item label="页面边距">
            <el-input v-model="formLabelAlign.pageTB"></el-input>
          </el-form-item>
          <el-form-item label="页面间距">
            <el-input v-model="formLabelAlign.pageLR"></el-input>
          </el-form-item>
        </el-form>
        <el-button type="primary" round>保存打印格式</el-button>
      </el-aside>
    </el-container>
  </el-container>
</template>

<script>
import CrtBarCode from "../components/barcode";
import CrtText from "../components/text";
import CrtQarCode from "../components/qarcode";
import Tmpl from "../components/template";
import JsBarcode from "jsbarcode";

export default {
  name: "Design",
  components: {
    CrtBarCode,
    CrtText,
    CrtQarCode,
    Tmpl
  },
  data() {
    return {
      labelPosition: "left",
      formLabelAlign: {
        modalHeight: "250",
        modalWidth: "300",
        labelRow: "1",
        labelLR: "0",
        labelTB: "0",
        pageLR: "0",
        pageTB: "0"
      },
      num: 0
    };
  },
  methods: {
    success: function() {
      this.num++;
      JsBarcode(".barcode").init();
    },

    CrtPic: function() {},

    CrtLine: function() {},

    CrtBox: function() {},

    print: function() {},

    tmplSave: function() {},

    tmplSaveAs: function() {},

    del: function() {},

    delAll: function() {}
  }
};
</script>

<style lang="stylus" scoped>
.el-aside {
  background-color: #8EB5C4;
  color: #333;
  text-align: center;
  line-height: 100px;
  margin: 0 20px 0 20px;
}

.el-aside .el-form-item {
  margin: 35px 10px 5px 10px;
}

.hiddenText {
  margin: 0 30px 0 0;
}

.el-header {
  background-color: #8EB5C4;
  text-align: left;
  margin: 20px 0 0 0;
}

.el-main {
  background-color: white;
  color: #333;
  text-align: center;
  line-height: 160px;
  height: 600px;
  padding: 0;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside, .el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}

.el-row {
  margin-bottom: 20px;

  &:last-child {
    margin-bottom: 0;
  }
}

.el-col {
  border-radius: 4px;
}

.bg-purple-dark {
  background: #99a9bf;
}

.bg-purple {
  background: #d3dce6;
}

.bg-purple-light {
  background: #e5e9f2;
}

.grid-content {
  border-radius: 4px;
  min-height: 36px;
}

.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>
