<template>
    <div>
        <div class="search">
            <el-input
                v-model="input"
                placeholder="寻找某种东西"
                prefix-icon="Search"
                style="width:500px;"
                clearable
                
      />
        </div>
        <div>
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
            input:''
        }
    },
}
</script>
