<template>
   <div v-if="project">
            <h1 >{{ project.title }}</h1>
            <img :src="`${store.imgPath}${project.image}`" :alt="project.title">
        </div>
   
</template>

<script>
import axios from 'axios';
import { store } from '../store';
    export default {
        name: 'SingleProject',
        data(){
            return{
                store,
                project: null
            }
        },
        methods:{
            getProjectData(){
                axios.get(`${this.store.apiBaseUrl}/projects/${this.$route.params.slug}`).then((res)=>{
                    console.log(res.data)
                    if(res.data.results){
                        this.project = res.data.results
                    }else{
                        this.$router.push({ name: 'not-found'})
                    }
                    
                })
            }
        },
        created(){
            this.getProjectData()
        }
    }
</script>

<style lang="scss" scoped>

</style>