<template>
    <div>
      <head-top go-back="true" :head-title="Readme"></head-top>
      <div style="padding:55px 5px 5px;">
        <div v-for="(item,index) in listReadme">
          <span>{{index+1}}、{{item.q}}</span>

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
    export default {
        name: "readme",
      data(){
          return{
            Readme:'项目学习、记录',
            listReadme:[{"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"测试账号？","a":"  账号：testele 密码：testele"},
              {"q":"项目大量使用了section标签，而不是div？","a":"section和div的区别 ",url:"https://blog.csdn.net/sunshine940326/article/details/52606038"},
              {"q":"网络请求模块使用的fetch，和ajax、axios区别？","a":"ajax和axios、fetch的区别",url:"https://www.jianshu.com/p/8bc48f8fde75"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
              {"q":"如何运行项目？","a":"  Terminal -> (首次运行 npm install --save) Local: npm run dev"},
            ],
          }
      },
      components:{
        headTop,
      },
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
</style>
