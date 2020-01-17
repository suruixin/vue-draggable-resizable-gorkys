<template>
<div id="app">
  <Button @click="resize">变化</Button>
  <button @click="divSize">改变div大小</button>
  <div style="border: 1px solid red; position: relative;margin: 0 auto"
       :style="{
    width: size.width + 'px',
    height: size.height + 'px'
  }">
    <vue-draggable-resizable
      :w="item.w"
      :h="item.h"
      :parent="true"
      :debug="false"
      :x="item.x"
      :y="item.y"
      :isConflictCheck="true"
      :snap="true"
      :snapTolerance="10"
      @refLineParams="getRefLineParams"
      class="test1" :resizeCount="resizeCount">
    </vue-draggable-resizable>
    <vue-draggable-resizable
      :w="200"
      :h="200"
      :parent="true"
      :x="210"
      :debug="false"
      :min-width="200"
      :min-height="200"
      :isConflictCheck="true"
      :snap="true"
      :snapTolerance="10"
      @refLineParams="getRefLineParams"
      class="test2" :resizeCount="resizeCount">
    </vue-draggable-resizable>
    <vue-draggable-resizable
      :w="200"
      :h="200"
      :parent="true"
      :x="420"
      :debug="false"
      :min-width="2"
      :min-height="2"
      :isConflictCheck="true"
      :snap="true"
      :snapTolerance="10"
      @refLineParams="getRefLineParams"
      class="test3" :resizeCount="resizeCount">
    </vue-draggable-resizable>
    <!--辅助线-->
    <!--辅助线END-->
  </div>
</div>
</template>

<script>
  import VueDraggableResizable from './components/vue-draggable-resizable'
  import './components/vue-draggable-resizable.css'

  export default {
    name: 'app',
    components: {
      VueDraggableResizable
    },
    data() {
      return {
        vLine: [],
        hLine: [],
        item: {
          w: 200,
          h: 200,
          x: 0,
          y: 0
        },
        size: {
          width: 800,
          height: 600
        },
        resizeCount: 0
      }
    },
    methods: {
      // 辅助线回调事件
      getRefLineParams(params) {
        const {vLine, hLine} = params
        this.vLine = vLine
        this.hLine = hLine
      },
      resize() {
        this.size.width = 900
        this.size.height = 800
        this.resizeCount++
        this.item.w = 250
        this.item.h = 250
      },
      divSize() {
        this.item.w = 250
        this.item.h = 250
      }
    }
  }
</script>

<style>
  .test1 {
    background-color: rgb(239, 154, 154);
  }

  .test2 {
    background-color: rgb(129, 212, 250);
  }

  .test3 {
    background-color: rgb(174, 213, 129);
  }
</style>
