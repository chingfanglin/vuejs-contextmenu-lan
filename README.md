# vuejs-contextmenu-lan

> Contextmenu component for vue2

## install vuejs-contextmenu-lan

  npm install vuejs-contextmenu-lan -s
  yarn add vuejs-contextmenu-lan
  
 ## 預覽 Preview
![Alt text](https://raw.githubusercontent.com/chingfanglin/vuejs-contextmenu-lan/master/docs/image/contextmenu1.png)
![Alt text](https://raw.githubusercontent.com/chingfanglin/vuejs-contextmenu-lan/master/docs/image/contextmenu2.png)

[Demo](https://chingfanglin.github.io/vuejs-contextmenu-lan/)

## Vue mount
    // mount with global
    import ContextMenu from 'vuejs-contextmenu-lan'
    Vue.use(ContextMenu)


## Use
    <template>
      <div>
        <div @contextmenu.prevent="open('Test Area')">
          Test Area
        </div>
        <v-context-menu :data="contextMenuData"></v-context-menu>
      </div>
    </template>

    <script>
      export default {
        name: 'app',
        data () {
          return {
            contextMenuData: {
              menuData: {},
              menuName: 'content-menu',
              position: {
                x: null,
                y: null
              },
              menulists: [
                {
                  fnHandler: this.test1,  // Binding events
                  btnName: 'Test Class 1' // The name of the menu option
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
            console.log('test1: ', val)
          },
          test2( val) {
            console.log('test2: ', val)
          },
          test3 (val) {
            console.log('test3: ', val)
          },
          test4 (val) {
            console.log('test4: ', val)
          },
          test5 (val) {
            console.log('test5: ', val)
          }
        }
      }
      </script>

## 許可協議 License
The MIT License (MIT)

Copyright (c) 2018 林慶芳

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
