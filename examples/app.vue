<style lang="less">
    @import "../src/styles/index.less";
    .container-nav{
        &>span{
            display: inline-block;
            margin-right: 12px;
        }
    }
</style>
<template>
    <div style="margin: 50px" id="app" class="container">
        <Title :level="1" style="margin: 0;">View UI <Gradient colors="#28c0ff #047af8">Plus</Gradient></Title>
        <Title :level="1" class="mg-top" style="margin: 0;">开源项目实践成果演示</Title>
        <Divider>新增组件</Divider>
        <Title :level="3" class="mg-top">渐变字体</Title>
        <a class="mg-top" href="https://github.com/view-design/ViewUIPlus/pull/213"><Button>Pull Request</Button></a>
        <Text code class="mg-top">{{'<Title :level="1"><Gradient colors="#40E0D0 #FF8C00 #FF0080">多彩人生，由你掌握</Gradient></Title>'}}</Text>
        <Title :level="1" style="margin-top:0.6rem" class="mg-top"><Gradient colors="#40E0D0 #FF8C00 #FF0080">多彩人生，由你掌握</Gradient></Title>
        
        <Divider>组件修改</Divider>

        <Title :level="3" class="mg-top">为poptip添加右键触发方式</Title>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/pull/219"><Button>Pull Request</Button></a>
        
        <Title :level="3" class="mg-top">为Scroll更改滚动条样式</Title>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/pull/214"><Button>Pull Request</Button></a>

        <Scroll :on-reach-edge="handleReachEdge">
            <Card dis-hover v-for="(item, index) in list" :key="index" style="margin: 32px 0">
                Content {{ item }}
            </Card>
        </Scroll>

        <Divider>Bug修复</Divider>
        <Title :level="3" class="mg-top">Modal组件可拖拽状态下设置宽度为百分比时窗口显示异常</Title>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/issues/208"><Button>Issue</Button></a>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/pull/218"><Button>Pull Request</Button></a>
        <a class="mg-right" href="https://run.iviewui.com/"><Button>Playground</Button></a>

        <Title :level="3" class="mg-top">禁用的树节点被父节点影响</Title>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/issues/199"><Button>Issue</Button></a>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/pull/217"><Button>Pull Request</Button></a>
        <a class="mg-right" href="https://run.iviewui.com/"><Button>Playground</Button></a>
        <Tree :data="data" show-checkbox multiple></Tree>

        <Card style="white-space: pre-line;" class="mg-top">
            {{`<template>
                <Tree :data="data" show-checkbox multiple></Tree>
            </template>
            <script>
                export default {
                    data () {
                        return {
                            data: [
                                {
                                    title: 'parent 1',
                                    expand: true,
                                    selected: true,
                                    children: [
                                        {
                                            title: 'parent 1-1',
                                            expand: true,
                                            children: [
                                                {
                                                    title: 'leaf 1-1-1',
                                                    disabled: true
                                                },
                                                {
                                                    title: 'leaf 1-1-2'
                                                }
                                            ]
                                        },
                                        {
                                            title: 'parent 1-2',
                                            expand: true,
                                            children: [
                                                {
                                                    title: 'leaf 1-2-1',
                                                    disableCheckbox: true
                                                },
                                                {
                                                    title: 'leaf 1-2-1'
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                }
            </script>
            `}}
        </Card>

        <Title :level="3" class="mg-top">树组件箭头间距缺失</Title>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/issues/211"><Button>Issue</Button></a>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/pull/216"><Button>Pull Request</Button></a>
        <a class="mg-right" href="https://run.iviewui.com/"><Button>Playground</Button></a>

        <Title :level="3" class="mg-top">ellipsis组件由于缺少小数而导致的部分字号(如2.7rem)缺行</Title>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/issues/207"><Button>Issue</Button></a>
        <a class="mg-right" href="https://github.com/view-design/ViewUIPlus/pull/210"><Button>Pull Request</Button></a>
        <a class="mg-right" href="https://run.iviewui.com/"><Button>Playground</Button></a>

        <div style="width:720px;margin: 0 auto;">
            <Ellipsis  style="font-size:2.7rem" :text="text" :lines="4" tooltip />
        </div>

        <Card style="white-space: pre-line;" class="mg-top">{{`<template>
            <div style="width:400px;margin: 0 auto;">
                <Ellipsis style="font-size:2.7rem" :text="text" :lines="4" tooltip />
            </div>
        </template>
        <script>
            export default {
                data () {
                    return {
                        text: '史蒂夫·乔布斯（英语：Steve Jobs），是一名美国企业家、营销家和发明家，苹果公司的联合创始人之一，曾任董事长及首席执行官职位，NeXT创办人及首席执行官，也是皮克斯动画的创办人并曾任首席执行官，2006年为华特迪士尼公司的董事会成员。2017年9月苹果发布会举行的地方，以他命名为 Steve Jobs Theater 。'
                    }
                }
            }
        </script>`}}</Card>
        <div style="margin: 50px">
            <router-view></router-view>
        </div>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                data: [
                    {
                        title: 'parent 1',
                        expand: true,
                        selected: true,
                        children: [
                            {
                                title: 'parent 1-1',
                                expand: true,
                                children: [
                                    {
                                        title: 'leaf 1-1-1',
                                        disabled: true
                                    },
                                    {
                                        title: 'leaf 1-1-2'
                                    }
                                ]
                            },
                            {
                                title: 'parent 1-2',
                                expand: true,
                                children: [
                                    {
                                        title: 'leaf 1-2-1',
                                        disableCheckbox: true
                                    },
                                    {
                                        title: 'leaf 1-2-1'
                                    }
                                ]
                            }
                        ]
                    }
                ],
                text: '史蒂夫·乔布斯（英语：Steve Jobs），是一名美国企业家、营销家和发明家，苹果公司的联合创始人之一，曾任董事长及首席执行官职位，NeXT创办人及首席执行官，也是皮克斯动画的创办人并曾任首席执行官，2006年为华特迪士尼公司的董事会成员。2017年9月苹果发布会举行的地方，以他命名为 Steve Jobs Theater 。',
                list: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
            }
        },
        methods: {
            handleReachEdge (dir) {
                return new Promise(resolve => {
                    setTimeout(() => {
                        if (dir > 0) {
                            const first = this.list[0];
                            for (let i = 1; i < 11; i++) {
                                this.list.unshift(first - i);
                            }
                        } else {
                            const last = this.list[this.list.length - 1];
                            for (let i = 1; i < 11; i++) {
                                this.list.push(last + i);
                            }
                        }
                        resolve();
                    }, 2000);
                });
            }
        }
    }
</script>
<style scoped>
.mg-top{
    margin-top:0.6rem;
    display:block;
}
.mg-right{
    margin-top:0.6rem;
    margin-right: 0.6rem;
}
</style>