<template>
  <div class="icons-container app-container">

    <el-divider content-position="left"> Icons List </el-divider>
    <el-tabs type="border-card">
      <el-tab-pane :label="`Font-awesome5 Icons( ${faIcons.length} )`">
        <div class="grid">
          <div v-for="item of faIcons" :key="item" @click="handleClipboard(generateFaIconCode(item),$event)">
            <el-tooltip placement="top">
              <div slot="content">
                {{ generateFaIconCode(item) }}
              </div>
              <div class="icon-item">
                <fa-icon :icon="item" size="1x" />
                <span>{{ item }}</span>
              </div>
            </el-tooltip>
          </div>
        </div>
      </el-tab-pane>
      <el-tab-pane :label="`Element-UI Icons( ${elementIcons.length} )`">
        <div class="grid">
          <div v-for="item of elementIcons" :key="item" @click="handleClipboard(generateElementIconCode(item),$event)">
            <el-tooltip placement="top">
              <div slot="content">
                {{ generateElementIconCode(item) }}
              </div>
              <div class="icon-item">
                <i :class="'el-icon-' + item" />
                <span>{{ item }}</span>
              </div>
            </el-tooltip>
          </div>
        </div>
      </el-tab-pane>
      <el-tab-pane :label="`UserIcons( ${svgIcons.length} )`">
        <div class="grid">
          <div v-for="item of svgIcons" :key="item" @click="handleClipboard(generateIconCode(item),$event)">
            <el-tooltip placement="top">
              <div slot="content">
                {{ generateIconCode(item) }}
              </div>
              <div class="icon-item">
                <svg-icon :icon-class="item" class-name="disabled" />
                <span>{{ item }}</span>
              </div>
            </el-tooltip>
          </div>
        </div>
      </el-tab-pane>
      <el-tab-pane label="play ground">
        <el-card>
          <el-button type="success"> <fa-icon icon="coffee" /> Coffee </el-button>
        </el-card>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import clipboard from '@/utils/clipboard'
import svgIcons from './svg-icons'
import elementIcons from './element-icons'
import faIcons from './fa-icons'

export default {
  name: 'Icons',
  data() {
    return {
      svgIcons,
      elementIcons,
      faIcons
    }
  },
  methods: {
    generateIconCode(symbol) {
      return `<svg-icon icon-class="${symbol}" />`
    },
    generateElementIconCode(symbol) {
      return `<i class="el-icon-${symbol}" />`
    },
    generateFaIconCode(symbol) {
      return `<fa-icon icon="${symbol}" />`
    },
    handleClipboard(text, event) {
      if (typeof (text) === 'string') clipboard(text, event)
    }
  }
}
</script>

<style lang="scss" scoped>
.icons-container {
  margin: 10px 20px 0;
  overflow: hidden;

  .grid {
    position: relative;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
  }

  .icon-item {
    margin: 20px;
    height: 85px;
    text-align: center;
    width: 100px;
    float: left;
    font-size: 30px;
    color: #24292e;
    cursor: pointer;
  }

  span {
    display: block;
    font-size: 16px;
    margin-top: 10px;
  }

  .disabled {
    pointer-events: none;
  }
}
</style>
