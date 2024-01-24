<template>
    <div class="card">
        <img :src="`${store.imgPath}${project.image}`" class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{ truncateTitle }}</h5>
            <p class="card-text">{{ truncateBody }}</p>
            <router-link :to="{ name: 'single-project', params: { slug: project.slug } }" class="btn btn-primary">
    View detail
</router-link>
        
        </div>
        
    </div>
</template>

<script>
import { store } from "../store";
export default {
        name: 'AppCard',
        props: ['project'],
        data(){
            return {
                store,
                titleMaxLen: 25,
                bodyMaxLen: 100,
            }
        },
        computed:{
            truncateTitle(){
                if(this.project.title.length > this.titleMaxLen){
                    return this.project.title.substr(0,this.titleMaxLen) + '...';
                }
                return this.project.title;            
            },
            truncateBody(){
                if(this.project.body.length > this.bodyMaxLen){
                    return this.project.body.substr(0,this.bodyMaxLen) + '...';
                }
                return this.project.body;            
            }
        }
        
}
</script>

<style lang="scss" scoped>

</style>