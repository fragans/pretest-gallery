<template>
    <section>

        <div v-for="(img,i) in images" :key="i"  @click.stop="select(img)" class="thumb">
            <div class="img">
                <div class="wide" :style="{ backgroundImage: 'url(' + img.src + ')' }"></div>
                <imgCaption :text="img.caption"></imgCaption>    
            </div>
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
                console.log('seleet')
                eventBus.$emit('showImage',img)
            }
        },
        components:{
            imgCaption
        },
        mounted(){
            
        }
    }
</script>

<style scoped>

section{
    display: flex;
}
.img{
    max-width: 200px;
    
    padding-right: 10px;
    
}
.thumb{
    width: 20%;
}
.wide{
    cursor: pointer;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    padding-bottom: 56.66%
}
</style>