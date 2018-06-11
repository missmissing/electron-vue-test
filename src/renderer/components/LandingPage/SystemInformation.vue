<template>
  <div>
    <div class="title">Information</div>
    <div class="items">
      <div class="item">
        <div class="name">Path:</div>
        <div class="value">{{ path }}</div>
      </div>
      <div class="item">
        <div class="name">Route Name:</div>
        <div class="value">{{ name }}</div>
      </div>
      <div class="item">
        <div class="name">Vue.js:</div>
        <div class="value">{{ vue }}</div>
      </div>
      <div class="item">
        <div class="name">Electron:</div>
        <div class="value">{{ electron }}</div>
      </div>
      <div class="item">
        <div class="name">Node:</div>
        <div class="value">{{ node }}</div>
      </div>
      <div class="item">
        <div class="name">Platform:</div>
        <div class="value">{{ platform }}</div>
      </div>
      <div class="item">
        <div class="name">dirname:</div>
        <div class="value">{{ dirname }}</div>
      </div>
      <div class="item">
        <div class="name">static:</div>
        <div class="value">{{ static }}</div>
      </div>
    </div>
  </div>
</template>

<script>
    import os from 'os'
    import fs from 'fs'

    const root = fs.readdirSync('/')
    // 这会打印出磁盘根级别的所有文件
    // 同时包含'/'和'C:\'。
    console.log(root);
    let path = os.homedir() + '\\holo\\';
    fs.readdirSync(path).forEach((item) => {
        let stat = fs.statSync(path + item);
        if (stat.isDirectory()) {
            console.log("dir: " + item);
        } else {
            console.log("file: " + item)
        }
    })

  export default {
    data () {
      return {
        electron: process.versions['atom-shell'],
        name: this.$route.name,
        node: process.versions.node,
        path: this.$route.path,
        platform: require('os').platform(),
        vue: require('vue/package.json').version,
          dirname : __dirname,
          static : __static
      }
    }
  }
</script>

<style scoped>
  .title {
    color: #888;
    font-size: 18px;
    font-weight: initial;
    letter-spacing: .25px;
    margin-top: 10px;
  }

  .items { margin-top: 8px; }

  .item {
    display: flex;
    margin-bottom: 6px;
  }

  .item .name {
    color: #6a6a6a;
    margin-right: 6px;
  }

  .item .value {
    color: #35495e;
    font-weight: bold;
  }
</style>
