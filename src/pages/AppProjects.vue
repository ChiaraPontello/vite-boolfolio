<template>
    <h1>Project List</h1>
    <div class="row">
        <div class="col-12 col-md-4 col-lg-3" v-for="project in store.projects" :key="project.id">
            <AppCard :project="project"/>
        </div>
    </div>


   
</template>

<script>
import {store} from "../store";
import axios from "axios";
import AppCard from "../components/AppCard.vue"
    export default {
        name: 'AppProjects',
        components: {
            AppCard
        },
        data(){
            return {
                store,
            }
        },
        methods: {
            getAllProjects(){
                axios.get(`${this.store.apiBaseUrl}/projects`).then((res) => {
                    console.log(res.data);
                    this.store.projects = res.data.results.data;
                }).catch((err)=>{

                })
                    
                }
            },
            created(){
                this.getAllProjects();
            }
        }
    
</script>

<style lang="scss" scoped>

</style>