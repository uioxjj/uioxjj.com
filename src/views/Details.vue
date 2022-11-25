<template>
    <div>
        <div class="image">
            <el-image       
                class="tu"
                style="width: 100% ; height: 100%;"
                :src="url"
                :preview-src-list="Curls"
                fit="cover"
                 />
        </div>
        <div></div>
    </div>
</template>

<script>
    export default{
        data() {
            return {
                url:require('E:/pixiv/1/pixiv1/illust_5290131_20181029_003330.jpg'),
                Curls:[
                require('E:/pixiv/1/pixiv1/illust_5290131_20181029_003330.jpg'),
    ],
            }
        },
    }
</script>

<style>
.image {
  width: 50%;
  height: 50%;
  position: relative;
}
.tuq {
  position: absolute;
  top: 50%;
  margin-top: -50px;
}
</style>
