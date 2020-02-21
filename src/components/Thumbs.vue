<template>
    <section>
        <div v-for="(img,i) in images" :key="i" class="img" @click="select(img)">
            <img :src="img.src" alt="" >
            
            <imgCaption :text="img.caption"></imgCaption>
        </div>
    </section>
</template>

<script>
import {eventBus} from '../main'
import imgCaption from './Caption'
    export default {
        props: ['images'],
        methods:{
            select(img){
                console.log('click')
                eventBus.$emit('showImage',img)
            }
        },
        components:{
            imgCaption
        },
        mounted(){
            console.log(this.images)
        }
    }
</script>

<style scoped>
img{
    height: 100%;
    width: 100%
}
section{
    display: flex;
}
.img{
max-width: 100px;
padding: 10px;
}
</style>