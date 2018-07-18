<template>
  <div class="v-content-menu__contain" :ref="data.menuName">
    <div class="v-content-menu__item" 
    v-for="item in data.menulists" 
    :key="item.id"
    @click.stop="click(item.fnHandler, data.menuData)"
    v-html="item.btnName"
    ></div>
  </div>
</template>
<script>
export default {
  name: 'v-content-menu',

  props: {
    data: Object
  },

  watch: {
    'data.position' (val) {
      const menu = this.$refs[this.data.menuName]
      const clientWidth = document.body.clientWidth
      const clientHeight= document.body.clientHeight
      let x = val.x
      let y = val.y

      menu.style.display = 'flex'
      const height = menu.clientHeight
      const width = menu.clientWidth

      if((x + width) > clientWidth) {
        x = clientWidth - width - 10
      }

      if((y + height) > clientHeight) {
        y = clientHeight - height - 10
      }

      menu.style.left = x + 'px'
      menu.style.top = y + 'px'

      document.addEventListener('mouseup', function () {
        menu.style.display = 'none'
      }, false)
    }
  },
  methods: {
    click (fnHandler, menuData) {
      fnHandler(menuData)
    }
  }
}
</script>

<style>
  .v-content-menu__contain {
    display: none;
    flex-direction: column;
    position: fixed;
    left: 0;
    top: 0;
    width: 130px;
    box-shadow: 0 0 15px #c5c5c3;
    background-color: #fff;
    pointer-events: visiblepainted;
    z-index: 9999;
  }

  .v-content-menu__item {
    padding: 8% 15%;
    font-size: 12px;
    cursor: default;
  }
      
  .v-content-menu__item:hover {
    background-color: #e7e7e7;
  }
</style>
