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
        <div class="image">
            <div class="tu">
            <el-image            
                style="width: 100% ; height: 100%;  box-shadow: 5px 5px 10px #909090;"
                :src="url"
                :preview-src-list="Curls"
                fit="cover"
                 />
            </div>
            <div class="info">
                <p><el-icon size="large"><EditPen></EditPen></el-icon>画师：</p>
                <p><el-icon size="large"><Monitor></Monitor></el-icon>分辨率：</p>
                <p><el-button type="success" icon="Download" round>下载喵</el-button></p>
            </div>
        </div>
        
    </div>
</template>

<script>
import { Download, EditPen } from '@element-plus/icons-vue';

    export default{
    data() {
        return {
            url: require("E:/pixiv/1/pixiv1/illust_5290131_20181029_003330.jpg"),
            Curls: [
                require("E:/pixiv/1/pixiv1/illust_5290131_20181029_003330.jpg"),
            ],
        };
    },
    components: { EditPen }
}
</script>

<style>
.tu {
  position: absolute;
  width: 60%;
  height: 60%;
  top: 20%;
  left: 2.5%;
}
.info {
  position: absolute;
  width: 30%;
  height: 60%;
  background-color: #455a64;
  right: 2.5%;
  top: 20%;
  box-shadow: 5px 5px 10px #909090;
}
.info p {
  font-size: 20px;
  display: flex;
  align-items: center;
  color: white;
}
</style>
