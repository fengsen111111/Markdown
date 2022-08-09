## 安装  and  使用
    地址：https://www.wangeditor.com/v5/for-frame.html#%E4%BD%BF%E7%94%A8
    yarn add @wangeditor/editor  或者  npm install @wangeditor/editor --save

##  安装：npm install wangeditor --save

### 文档链接 
     https://segmentfault.com/a/1190000040078101

## 配置文件
#### 在component 目录中创建 wangEditor文件夹
#### 在 wangEditor 文件夹中创建 index.js 文件
### index.js中的内容
            <template>
            <div ref="editor"></div>
            </template>

            <script>
            import E from 'wangeditor'
            export default {
            props: {
                value: {
                type: String,
                default: ''
                },
                meanArray: {
                // 自定义菜单
                type: Array,
                default: null
                }
            },
            model: {
                prop: 'value',
                event: 'change'
            },
            watch: {
                value: function (value) {
                if (value !== this.editor.txt.html()) {
                    this.editor.txt.html(this.value)
                }
                }
                // value为编辑框输入的内容，这里我监听了一下值，当父组件调用得时候，如果给value赋值了，子组件将会显示父组件赋给的值
            },
            data () {
                return {
                // 默认有这么多菜单，meanArray有值以meanArray为准
                defaultMeanus: [
                    'head',
                    'bold',
                    'fontSize',
                    'fontName',
                    'italic',
                    'underline',
                    'strikeThrough',
                    'indent',
                    'lineHeight',
                    'foreColor',
                    'backColor',
                    'link',
                    'list',
                    'justify',
                    'quote',
                    'emoticon',
                    'image',
                    'video',
                    'table',
                    'code',
                    'splitLine',
                    'undo',
                    'redo'
                ],
                editor: ''
                }
            },
            methods: {
                init () {
                const _this = this
                this.editor = new E(this.$refs.editor)
                this.editor.config.uploadImgShowBase64 = true // 使用 base64 保存图片
                this.setMenus() // 设置菜单
                this.editor.config.onchange = (html) => {
                    _this.$emit('change', html) // 将内容同步到父组件中
                }
                this.editor.create() // 创建编辑器
                },
                setMenus () {
                // 设置菜单
                if (this.meanArray) {
                    this.editor.config.menus = this.meanArray
                } else {
                    this.editor.config.menus = this.defaultMeanus
                }
                },
                getHtml () {
                // 得到文本内容
                return this.editor.txt.html()
                },
                setHtml (txt) {
                // 设置富文本里面的值
                this.editor.txt.html(txt)
                }
            },
            mounted () {
                const that = this
                that.$nextTick(function () {
                that.init()
                })
            }
            }
            </script>
### 在父组件中调用
            <template>
            <!-- 富文本编辑器 -->
            <!-- ref 不同可以实现多个富文本编辑器 -->
            <editor ref="editorOne" v-model="detail" @change="change"></editor>
            </template>

            <script>
            import Editor from '@/components/wangEditor'

            export default {
            data () {
                return {
                // 文章内容
                detail: ''
                }
            }
            methods: {
                change (val) {
                // console.log(val)
                // console.log(this.detail)
                }
            components: { Editor }
            }
            </script>
