<template>
    <div>
      <head-top go-back="true" :head-title="Readme"></head-top>
      <div style="padding:55px 5px 5px;">
        <div class="rtab">
          <span @click="changeTab(1)" :class="tabIndex==1?'tab-active':''">记录</span>
          <span @click="changeTab(2)" :class="tabIndex==2?'tab-active':''">学习</span>

        </div>

        <div v-for="(item,index) in listItem">
          <span v-show="tabIndex==1">{{index+1}}、{{item.q}}</span>

          <p v-if="item.url">
            <a :href="item.url">{{item.a}}</a>
          </p>
          <p v-else>{{item.a}}</p>
        </div>


      </div>
    </div>
</template>

<script>
  import headTop from 'src/components/header/head'
  import footGuide from "../../components/footer/footGuide";
  import {testBd} from "../../service/getData";
    export default {
        name: "readme",
      data(){
          return{
            Readme:'项目学习、记录',
            listReadme:[{"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"测试账号？","a":"  账号：testele 密码：testele"},
              {"q":"项目大量使用了section标签，而不是div？","a":"section和div的区别 ",url:"https://blog.csdn.net/sunshine940326/article/details/52606038"},
              {"q":"网络请求模块使用的fetch，和ajax、axios区别？","a":"ajax和axios、fetch的区别",url:"https://www.jianshu.com/p/8bc48f8fde75"},
              {"q":"need beyond？ vuex  是否可以用cookie替代？不可以，项目太大？","a":"  vuex "},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"vuex和localstorage存储数据有什么区别？","a":"完全就是两个东西，vuex是vue中的状态管理机制，是方便组件之间通信的；而localstorage是本地存储，是将数据存储到浏览器的方法，一般是在跨页面传递数据时使用。",url:"https://segmentfault.com/q/1010000009396002?utm_source=sf-similar-question"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"其他相关 vue-cli？","a":"静态文件css或自己的工具类：都是在 rootProject/src/ 目录下创建静态或业务需要文件夹文件；创建在外面（根目录），打包的时候容易出问题" +
                  "/n axios在普通页面使用的封装"},
            ],
            listLearn:[
              {q:"",a:"彻底搞清楚javascript中的require、import和export",url:"https://www.cnblogs.com/libin-1/p/7127481.html"},
              {q:"",a:"vuex和localstorage存储数据有什么区别？",url:"https://segmentfault.com/q/1010000009396002?utm_source=sf-similar-question"},


              {q:"",a:"vuex和localstorage存储数据有什么区别？",url:"https://segmentfault.com/q/1010000009396002?utm_source=sf-similar-question"},
              {q:"",a:"vuex和localstorage存储数据有什么区别？",url:"https://segmentfault.com/q/1010000009396002?utm_source=sf-similar-question"},
              {q:"",a:"vuex和localstorage存储数据有什么区别？",url:"https://segmentfault.com/q/1010000009396002?utm_source=sf-similar-question"},
            ],

            listItem:[],
            testBd:null,

            tabIndex:1,
          }
      },
      components:{
        headTop,
      },
      mounted() {

          this.initData();

          this.getReferrer();
      },
      methods:{
        //初始化时获取基本数据
        async initData(){
          this.listItem = this.listReadme;

          //详情
          this.testBd = await testBd();
        },

          getReferrer:function () {
            //需要放到服务器中，在本地的话返回空
            // document.setR referrer  ='www.baidu.com';
            let mReferrer = document.referrer;
            console.log("document.referrer"+mReferrer);
          },
        changeTab:function (index) {
          if (this.tabIndex != index){
            this.tabIndex = index;
            this.listItem = (index==1 ? this.listReadme : this.listLearn );
          }
        }
      }
    }
</script>

<style scoped>
  span{
    color: #343434;
    font-size: 14px;
  }
  p{
    color: #999;
    font-size: 14px;
    margin: 0;
    padding: 0;
  }
  a{
    color: #3399ea;
  }
  .rtab{
    margin: 5px;
    background: #ffffff;
    border-radius: 7px;
    display: flex;

    box-shadow: 0px 5px 5px #F1F2F4;
  }
  .rtab span{
    flex: 1;
    color: #232323;
    font-size: 14px;
    text-align: center;

    height: 35px;
    line-height: 35px;
  }
  .rtab .tab-active{
    background: #3190e8;
    color: #ffffff;
    border-radius: 7px;
  }

</style>
