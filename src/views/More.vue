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
        <div class="search">
            <div class="input">
            <el-input
                v-model="input"
                placeholder="寻找某种东西"
                prefix-icon="Search"
                style="width:500px;"
                clearable
            >
            <template #append>
        <el-button>搜索</el-button>
      </template>
        </el-input>
            </div>
            <div>
            <el-radio-group v-model="radio" :border="false" size="large">
                <el-radio-button  @click.prevent="clickRadio('1')" label="1" />
                <el-radio-button  @click.prevent="clickRadio('2')" label="2" />
                <el-radio-button  @click.prevent="clickRadio('3')" label="3" />
            </el-radio-group>
            </div>
        </div>
        <div class="image">
            <el-image v-for="item in urls" :key="item" :src="item.url" style="width:20%;height:20%;border-radius: 5%;box-shadow: 2px 2px 10px #909090;" />
        </div>
    </div>
</template>

<script>
import { Search } from '@element-plus/icons-vue';

export default{
    comments: {
        Search
    },

    data() {
        return {
            urls:[
                    {url:require('E:/pixiv/1/pixiv1/illust_5290131_20181029_003330.jpg')},
                 ],
            input:'',
            radio:''
        }
    },

    methods:{
        clickRadio(e){
            e === this.radio ? this.radio = '' : this.radio = e
        }
    }
}
</script>

<style>
.search {
  position: absolute;
  top: 10%;
  width: 100%;
}
.input {
  color: blue;
}
.el-input__inner {
  background-color: #e6e6e6;
}
.el-input__wrapper {
  background-color: #e6e6e6;
}
.el-input__prefix-inner {
  color: black;
}
.el-input-group__append button.el-button {
  background: linear-gradient(to right, #4facfe 0%, #00f2fe 100%);
  color: white;
}
.image {
  position: absolute;
  top: 30%;
}
</style>
