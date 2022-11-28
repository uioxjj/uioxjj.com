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
        <div class="emoji">
            <span>抽签哦😎</span>
            <el-tabs v-model="activeName" class="demo-tabs" @tab-click="handleClick">
                 <el-tab-pane label="数字" name="first">User</el-tab-pane>
                 <el-tab-pane label="自定义添加" name="second">Config</el-tab-pane>
            </el-tabs>
        </div>
    </div>
</template>

<script>

</script>

<style>
.emoji {
  position: absolute;
  top: 10%;
  left: 40%;
}
</style>
