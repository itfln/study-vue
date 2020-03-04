<template>
    <div>
        <!--条件渲染-->
        <p v-if="courses.length == 0">没有任何课程信息</p>
        <!--列表渲染-->
        <!--
        <div v-for="c in courses" :key="c" @click="selectedCourse = c" 
        :class="{active:selectedCourse === c}">
            {{ c}}
        </div>>
        -->
        <!--style-->
        <div class="course-list" v-else>
            <div v-for="c in courses" :key="c.name" @click="selectedCourse = c" 
            :style="{backgroundColor:selectedCourse===c?'#ddd':'transparent'}">
            {{ c.name }} - ¥{{c.price}}
            </div>
        </div>    
    </div>
</template>

<script>
    export default {
            data(){
                return {
                    selectedCourse:''
                }
            },
            props:{
                courses:{
                    type:Array,
                    default:function(){
                        return []
                    }
                }
            },
            filters:{
                currency(value,symbol="¥"){
                    return symbol + value;
                }
            }
        }
</script>

<style scoped>
.active{
    background-color: #ddd;
}
</style>