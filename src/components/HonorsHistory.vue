<template>
    <div>
        <h2>获奖经历</h2>
        <el-form class="honorsInput" :label-position="labelPosition">
            <div v-for="(honor,index) in HonorsHistory" class="HonorBlock" v-bind:key="(honor,index)">
                <i class="el-icon-circle-cross" v-on:click="removeHonorHistory(index)"></i>
                <el-form-item label="奖项">
                    <el-input v-model="honor.awards" placeholder="奖项"></el-input>
                </el-form-item>
                <el-form-item label="获奖时间">
                    <div class="block">
                        <el-date-picker v-model="honor.honorDate" type="date" placeholder="选择日期" ></el-date-picker>
                    </div>
                </el-form-item>
            </div>
            <el-button class="btn" type="text" v-on:click="addHonorHistory">+ 添加更多</el-button>
        </el-form>
    </div>
</template>
<script>
export default {
    props: ['HonorsHistory'],
    methods: {
        addHonorHistory() {
            this.HonorsHistory.push(
                {
                    awards:'',
                    honorDate:''
                })
        },
        removeHonorHistory(index) {
            this.HonorsHistory.splice(index, 1)
        }
    },
    data() {
        return {
            pickerOptions0: {
                disabledDate(time) {
                    return time.getTime() < Date.now() - 8.64e7;
                }
            },
            labelPosition:'top',
        }
    }
}
</script>
