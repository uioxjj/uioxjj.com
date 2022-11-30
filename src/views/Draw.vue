<template>
    <div>
        <div class="bg">
			<css-doodle>
              @grid: 13 / 100% 100%;
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
        <div class="shuzi">
                    <div style="font-size:20px; font-weight: bold;">数字抽签</div>
                    <div style="font-size:50px; color:cadetblue; margin-top:10%">
                      {{ tweened.toFixed(0) }}
                    </div>
                    <div style="font-weight:bold">
                      <span v-if="isRandom">恭喜这个数数😸</span>
                      <span v-else >会是多少呢🙂</span>
                    </div>
                    <div style="margin-top:10%">
                      <el-button type="success" @click="start">开抽😋</el-button>
                    </div>
                    <div style="margin-top:10%">
                      <el-button type="warning" @click="edit">设置数字</el-button>
                    </div>
                    <div style="font-weight:bold">
                      请先设置数字喵🐹
                    </div>
        </div>
        <div class="diy">
                    <div style="font-size:20px; font-weight: bold;">自定义抽签</div>
                    <div style="font-size:50px; color:cadetblue" v-for="item in zdy" :key="item">
                      {{ item.value }}
                    </div>
                    <div style="font-weight:bold">
                      会是哪个呢🙂
                    </div>
                    <div>
                      <el-button type="success" @click="start2">开抽😋</el-button>
                    </div>
                    <div>
                      <el-button type="warning" @click="edit2">自定义内容</el-button>
                    </div>
                    <div style="font-weight:bold">
                      请先设置内容喵🐭
                    </div>
        </div>
    </div>
</template>

<script>
import { ElMessage, ElMessageBox } from 'element-plus'
import gsap from 'gsap'
  export default{
    data(){
      return{
        number:'',
        tweened:0,
        random:'',
        random2:'',
        isRandom:false,
        zdy:[1,2,{'value':'1'}]
      }
    },

    watch: {
      number(n) {
      gsap.to(this, { duration: 0.5, tweened: Number(n) || 0 })
    }
    },

    methods:{
      edit(){
        ElMessageBox.prompt('请输入数字喵🦝', '', {
        confirmButtonText: 'OK',
        cancelButtonText: '取消',
        inputPattern:/^[1-9]\d*$/,
        inputErrorMessage: '要大于0整数哦',
        })
        .then(({ value }) => {
        this.number=value
        this.random=value
        this.isRandom=false
        })
        .catch(() => {
        })
      },

      edit2(){
        ElMessageBox.prompt('请输入数字喵🦝', '', {
        confirmButtonText: 'OK',
        cancelButtonText: '取消',
        })
        .then(({ value }) => {
        this.zdy.push({value})
        this.isRandom=false
        })
        .catch(() => {
        })
      },
      start(){
        if(this.random==''){
          ElMessage({
            message:'还没输入数字喵！',
            type:'warning'
          })
          return
        }
        this.number=Math.ceil(Math.random()*this.random) 
        setTimeout(this.isRandom=true,1000)
      }
    }
  }
</script>

<style>
.shuzi {
  width: 20%;
  position: absolute;
  top: 20%;
  left: 20%;
  background: linear-gradient(to top, #fbc2eb 0%, #a6c1ee 100%);
  box-shadow: 2px 2px 10px #909090;
}
.diy {
  width: 20%;
  position: absolute;
  top: 20%;
  right: 20%;
  background: linear-gradient(to top, #fbc2eb 0%, #a6c1ee 100%);
  box-shadow: 2px 2px 10px #909090;
}
</style>
