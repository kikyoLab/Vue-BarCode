<template>
  <span class="btnClass">
    <el-button
      type="primary"
      icon="el-icon-s-ticket"
      size="small"
      @click="dialogFormVisible = true"
      >一维码
    </el-button>
    <el-dialog title="一维码生成" :visible.sync="dialogFormVisible">
      <el-form :model="form">
        <el-form-item label="条码ID" :label-width="formLabelWidth">
          <el-input v-model="form.barcodeId" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="条码类型" :label-width="formLabelWidth">
          <el-select v-model="form.barcodeType" placeholder="请选择条码类型">
            <el-option label="CODE128" value="CODE128"></el-option>
            <el-option label="CODE128A" value="CODE128A"></el-option>
            <el-option label="CODE128B" value="CODE128B"></el-option>
            <el-option label="CODE128C" value="CODE128C"></el-option>
            <el-option label="EAN13" value="EAN13"></el-option>
            <el-option label="EAN8" value="EAN8"></el-option>
            <el-option label="EAN5" value="EAN5"></el-option>
            <el-option label="EAN2" value="EAN2"></el-option>
            <el-option label="UPC" value="UPC"></el-option>
            <el-option label="CODE39" value="CODE39"></el-option>
            <el-option label="ITF" value="ITF"></el-option>
            <el-option label="ITF14" value="ITF14"></el-option>
            <el-option label="MSI10" value="MSI10"></el-option>
            <el-option label="MSI11" value="MSI11"></el-option>
            <el-option label="MSI1010" value="MSI1010"></el-option>
            <el-option label="MSI1110" value="MSI1110"></el-option>
            <el-option label="pharmacode" value="pharmacode"></el-option>
            <el-option label="codabar" value="codabar"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="条码宽度" :label-width="formLabelWidth">
          <el-slider v-model="barcodeWidth" show-input> </el-slider>
        </el-form-item>
        <el-form-item label="条码高度" :label-width="formLabelWidth">
          <el-slider v-model="barcodeHeight" show-input> </el-slider>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="CrtBarCode()">确 定</el-button>
      </div>
    </el-dialog>
    <VueDragResize
      v-for="(i, index) in num"
      :key="index"
      :w="150"
      :h="100"
      @resizing="resize"
      @dragging="resize"
      @clicked="onActivated"
      @deactivated="onDeactivated"
    >
      <svg
        class="barcode"
        :jsbarcode-format="form.barcodeType"
        :jsbarcode-value="form.barcodeId"
        jsbarcode-textmargin="0"
        jsbarcode-fontoptions="bold"
        jsbarcode-width="1"
        jsbarcode-height="50"
        @dblclick="formEdit()"
      ></svg>
    </VueDragResize>
  </span>
</template>

<script>
import JsBarcode from "jsbarcode";
import VueDragResize from "vue-drag-resize";

export default {
  name: "CrtBarCode",
  components: {
    VueDragResize
  },
  data() {
    return {
      dialogFormVisible: false,
      form: {
        barcodeId: "",
        barcodeType: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: ""
      },
      formLabelWidth: "120px",
      barcodeWidth: 0,
      barcodeHeight: 0,
      num: 0,
      width: 0,
      height: 0,
      top: 0,
      left: 0
    };
  },
  methods: {
    resize(newRect) {
      this.width = newRect.width;
      this.height = newRect.height;
      this.top = newRect.top;
      this.left = newRect.left;
    },

    CrtBarCode: function() {
      this.dialogFormVisible = false;
      this.num++;
      setTimeout(() => {
        JsBarcode(".barcode").init();
      }, 100);
    },

    formEdit: function() {
      this.dialogFormVisible = true;
    }
  }
};
</script>

<style lang="stylus" scoped>
.btnClass {
  margin: 0 5px 0 5px;
}

.el-slider {
  margin: 0 0 0 10px;
}
</style>
