<template>
  <div class="toolbar">
    <div class="left">
      <!--<el-checkbox class="edge-enabled" title="连线模式" @change="$parent.enableEdgeHandler"></el-checkbox>-->
      <cc-dropdown
        class="edge-shape"
        :dropdown-items="$parent.edgeShapeList"
        @change="$parent.changeEdgeShapeHandler"
      >
      </cc-dropdown>
    </div>
    <div class="center">
      <div class="graph-ops">
        <i class="iconfont icon-undo" title="撤销" :class="$parent.disableUndo ? 'disabled':''"
           @click="$parent.undoHandler"></i>
        <i class="iconfont icon-redo" title="重做" :class="$parent.disableRedo ? 'disabled':''"
           @click="$parent.redoHandler"></i>
        <span class="separator"></span>
        <i class="iconfont icon-copy" title="复制" :class="$parent.disableCopy ? 'disabled':''"
           @click="$parent.copyHandler"></i>
        <i class="iconfont icon-paste" title="粘贴" :class="$parent.disablePaste ? 'disabled':''"
           @click="$parent.pasteHandler"></i>
        <i class="iconfont icon-clear" title="删除" :class="$parent.disableDelete ? 'disabled':''"
           @click="$parent.deleteHandler"></i>
        <span class="separator"></span>
        <i class="iconfont icon-zoom-in" id="zoom-in" title="放大" @click="$parent.zoomInHandler"></i>
        <i class="iconfont icon-zoom-out" title="缩小" @click="$parent.zoomOutHandler"></i>
        <i class="iconfont icon-fit" title="适应画布" @click="$parent.autoZoomHandler"></i>
        <i class="iconfont icon-actualsize" title="实际尺寸" @click="$parent.resetZoomHandler"></i>
        <span class="separator"></span>
        <i class="iconfont icon-roi-select" id="multi-select" title="框选" @click="$parent.multiSelectHandler"></i>
      </div>
    </div>
    <div class="right">
      <cc-button size="mini" @click="$parent.forceLayoutHandler">自动布局</cc-button>
      <!--<el-button size="mini" @click="$parent.circularLayoutHandler">环形布局</el-button>-->
      <!--<el-button size="mini" @click="$parent.radialLayoutHandler">辐射</el-button>-->
      <!--<el-button size="mini" @click="$parent.mdsLayoutHandler">MDS</el-button>-->
      <!--<el-button size="mini" @click="$parent.dagreLayoutHandler">层次</el-button>-->
      <!--<el-button size="mini" @click="$parent.autoLayoutHandler">自动（old）</el-button>-->
      <cc-button size="mini" @click="$parent.changeModeHandler('preview')">返回</cc-button>
      <cc-button size="mini" @click="$parent.saveDataHandler">保存</cc-button>
    </div>
  </div>
</template>

<script>
import { Button, Dropdown } from '../../cc-elements'

export default {
  name: 'ToolbarEdit',
  components: {
    'cc-button': Button,
    'cc-dropdown': Dropdown
  }
}
</script>

<style lang="scss" scoped>
.toolbar {
  /*z-index: 3;*/
  /*width: 100%;*/
  /*height: 42px;*/
  color: #333;
  text-align: left;
  vertical-align: middle;
  line-height: 42px;
  background-color: #ffffff;
  border: 1px solid #E9E9E9;
  box-shadow: 0 8px 12px 0 rgba(0, 52, 107, 0.04);
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;

  .left {
    display: inline-block;
    width: 12%;
  }

  .center {
    display: inline-block;
    width: 58%;
  }

  .right {
    display: inline-block;
    width: 30%;
    text-align: right;
  }

  .edge-enabled {
    width: 40%;
    text-align: center;
  }

  .edge-shape {
    width: 100%;
    /*margin-right: 20px;*/
    line-height: 25px;
    text-align: center;
    /*border-right: 1px solid #E6E9ED;*/
  }

  .graph-ops {
    display: inline-block;
    vertical-align: middle;
    margin-left: 20px;

    i {
      width: 20px;
      height: 20px;
      margin: 0 6px;
      line-height: 20px;
      color: #a8a8a8;
      text-align: center;
      border-radius: 2px;
      display: inline-block;
      border: 1px solid rgba(2, 2, 2, 0);
    }

    i:hover {
      cursor: pointer;
      border: 1px solid #E9E9E9;
    }

    .disabled {
      color: rgba(0, 0, 0, 0.25);
    }

    .disabled:hover {
      cursor: not-allowed;
      border: 1px solid rgba(2, 2, 2, 0);
    }

    .icon-select {
      background-color: #EEEEEE;
    }

    .separator {
      margin: 4px;
      border-left: 1px solid #E9E9E9;
    }
  }

  .cc-button {
    margin: 0 5px;
  }
}
</style>