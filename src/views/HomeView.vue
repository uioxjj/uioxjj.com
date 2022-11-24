<template>
  <div class="home">
    <div>
    <topHead/>
    </div>
    <div>
      <div>
        <el-carousel indicator-position="outside" height="500px">
      <el-carousel-item v-for="item in Curls" :key="item">
        <img alt="background" :src='item.url' style="width:100%;height: 100%;">
      </el-carousel-item>
       </el-carousel>
      </div>
    </div>
    <div class="head">
      <div class="zi"><el-icon><Lollipop></Lollipop></el-icon>1</div>
      <div class="more"><el-link icon="More">更多</el-link></div>
    </div>
    <div></div>
    <div class="bg">
			<css-doodle>
        @grid: 10 / 100% 100vmin;
        @size: 50px;
			  background-color: hsla( calc(3.5 * @i() + 180), 80%, 70%, @r(.8) );
			  animation: float 15s infinite linear alternate-reverse;
			  @even {
			    @shape: circle;
			  }
			  @odd {
			    @shape: diamond;
			  }
			  @keyframes float {
			    0% { transform: scale(@rand(0.15, 0.4))  rotate(@rand(0deg, 100deg)) translate3d(
			      @rand(-500%, 500%), @rand(-1000%, 500%), 1px) }
			    100% { transform: scale(@rand(0.2, 0.4))  rotate(@rand(0deg, 180deg)) translate3d(
			      @rand(-100%, 100%), @rand(-500%, 100%), 1px) }
			  }
			</css-doodle>
		</div>
    <div class="img">
      <el-image v-for="item in urls" :key="item" :src="item.url" style="width:20%;height:20%;border-radius: 5%;box-shadow: 2px 2px 10px #909090;" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import { Lollipop, More } from '@element-plus/icons-vue';

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Lollipop,
    More
},
  data() {
    return {
      Curls:[
        {url:require('../assets/carousel/1.jpg')},
        {url:require('../assets/carousel/2.png')},
        {url:require('../assets/carousel/3.png')},
        {url:require('../assets/carousel/4.png')},
    ],
    urls:[
        {url:require('E:/pixiv/1/pixiv1/illust_5290131_20181029_003330.jpg')},
    ]
    }
  },
}
</script>

<style>
body {
  margin: 0px;
}
.bg {
  z-index: 1;
}
.img {
  margin-top: -40%;
}
.zi {
  font-size: 35px;
  float: left;
  margin-top: 5%;
}
.more {
  float: right;
  margin-top: 5%;
  margin-right: 5%;
}
</style>
