<template>
    <h1>Projects List</h1>
    <ul>
        <li v-for="project in $store.projects" :key="project.id">{{ project.title }}</li>
    </ul>
</template>

<script>
import {store} from "../store";
import axios from "axios";
    export default {
        name: 'AppProjects',
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