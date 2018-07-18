<template>
  <div id="app">
    <div class="contextmenu__contain">
      <div class="contextmenu__colors">
        <div v-for="i in colors" :key="i.value" 
        class="contextmenu__color_item" 
        :style="{backgroundColor: i.color}"
        @contextmenu.prevent="open(i.value)"
        >
        </div>
      </div>
      <div ref="textarea" contenteditable="true" class="contextmenu__textarea"></div>
    </div>
    <div class="contextmenu__content" @contextmenu.prevent="open('Test Area')">
      <div>Test Area</div>
    </div>
    <v-context-menu :data="contextMenuData"></v-context-menu>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      colors: [
        {
          color: 'brown',
          value: 'brown'
        },
        {
          color: 'aquamarine',
          value: 'aquamarine'
        },
        {
          color: 'red',
          value: 'red'
        },
        {
          color: 'blueviolet',
          value: 'blueviolet'
        },
        {
          color: 'darkgray',
          value: 'darkgray'
        }
      ],
      contextMenuData: {
        menuData: {},
        menuName: 'content-menu',
        position: {
          x: null,
          y: null
        },
        menulists: [
          {
            fnHandler: this.test1, // Binding events(绑定事件)
            btnName: 'Test Class 1' // The name of the menu option (菜单名称)
          },
          {
            fnHandler: this.test2,
            btnName: 'Test Class 2'
          },
          {
            fnHandler: this.test3,
            btnName: 'Test Class 3'
          },
          {
            fnHandler: this.test4,
            btnName: 'Test Class 4'
          },
          {
            fnHandler: this.test5,
            btnName: 'Test Class 5'
          }
        ]
      }
    }
  },
  methods: {
    open (val) {
      event.preventDefault()
      const x = event.clientX
      const y = event.clientY
      this.contextMenuData.position = { x, y }
      this.contextMenuData.menuData = val
    },
    test1 (val) {
      this.$refs.textarea.innerHTML += `test1: ${val}<br />`
      console.log('test1: ', val)
    },
    test2( val) {
      this.$refs.textarea.innerHTML += `test2: ${val}<br />`
      console.log('test2: ', val)
    },
    test3 (val) {
      this.$refs.textarea.innerHTML += `test3: ${val}<br />`
      console.log('test3: ', val)
    },
    test4 (val) {
      this.$refs.textarea.innerHTML += `test4: ${val}<br />`
      console.log('test4: ', val)
    },
    test5 (val) {
      this.$refs.textarea.innerHTML += `test5: ${val}<br />`
      console.log('test5: ', val)
    }
  }
}
</script>

<style lang="less">
html,
body {
  height: 100%;
  margin: 0;
  padding: 0;
  font-family: Microsoft Yahei;
  overflow: hidden;
}
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-size: cover;
  background-position: center;
}
.contextmenu__contain {
  padding: 10%;
}

.contextmenu__colors {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100%;
}

.contextmenu__color_item {
  height: 80px;
  width: 80px;
}

.contextmenu__content {
  height: 250px;
  width: 100%;
  background-color: cadetblue;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 10em;
}

.contextmenu__textarea {
  margin-top: 4%;
  width: 100%;
  height: 150px;
  border: #d2d3d6 1px solid;
  overflow: auto;
}
</style>
