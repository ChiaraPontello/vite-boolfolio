<template>
   <h1>Single Project</h1>
   {{ project.title }}
</template>

<script>
import axios from 'axios';
import { store } from '../store';
    export default {
        name: 'SingleProject',
        data(){
            return{
                project: null
            }
        },
        methods:{
            getProjecData(){
                axios.get(`${this.store.apiBaseUrl}/projects/${this.$route.params.slug}`).then((res)=>{

                })
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>