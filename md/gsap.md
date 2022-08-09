## 安装 
    npm install gsap
## 使用 
   组件内引入：
      import gsap from "gsap";
## 属性
     gsap.to('#one',{
        x: 300, //横坐标向右偏移100
        y: 300, //纵坐标向下偏移100
        scaleX:1.1,  //scale大小变化  scaleX就是在X轴方向扩大原来几倍
        fill:'green',  //填充颜色，变成红色
        stroke:'pink',    //边框颜色，变成粉色
        strokeWidth:5,  //边框宽度5，
        rotation:30,   //角度的旋转    默认是以元素左下角为中心
        duration: 0.5,//动画持续时间  默认单位秒
        repeat:-1,//  重复次数，参数为1，重复一次，参数-1，重复无数次
        yoyo:true,//镜像效果，出去=>回来
        delay:1,//动画延时
      })
## 函数 
    gsap.set('#two',{transformOrigin:'center'})//将轴心设置为整个图形的重心，解决上面以左下角为轴心的问题

    let tl = gsap.timeline();  //支持链式调用   from 开始动画  to 结束动画
## 示例
      <template>
        <div id="app">
            <div id="one"></div>
            <div id="two"></div>
        </div>
      </template>

        <script>
        import gsap from "gsap";

        export default {
        name: 'App',
        created(){
            console.log("开始");
            setTimeout(() => {
            gsap.to('#one',{
            x: 300, //横坐标向右偏移100
            y: 300, //纵坐标向下偏移100
            scaleX:1.1,  //scale大小变化  scaleX就是在X轴方向扩大原来几倍
            fill:'green',  //填充颜色，变成红色
            stroke:'pink',    //边框颜色，变成粉色
            strokeWidth:5,  //边框宽度5，
            rotation:30,   //角度的旋转    默认是以元素左下角为中心
            duration: 0.5,//动画持续时间  默认单位秒
            repeat:-1,//  重复次数，参数为1，重复一次，参数-1，重复无数次
            yoyo:true,//镜像效果，出去=>回来
            delay:1,//动画延时
            })
            }, 2000);
            gsap.set('#two',{transformOrigin:'center'})//将轴心设置为整个图形的重心，解决上面以左下角为轴心的问题
            setTimeout(() => {
            gsap.to('#two',{
                rotation:360,
                x:200,
                yoyo:true,
                repeat:-1,
                duration:1
            })
            }, 2000);
            // let tl = gsap.timeline();  //支持链式调用   from 开始动画  to 结束动画
        }
        }
        </script>

        <style>
        #one{
        width: 100px;
        height: 100px;
        background-color: aqua;
        }
        #app{
        width: 100%;
        height: 100vh;
        background-color:burlywood;
        }
        #two{
        width: 100px;
        height: 100px;
        background-color: pink;
        }
        </style>
