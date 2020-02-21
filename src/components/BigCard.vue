<template>
    <section>

        <div ref="img" class="container" ></div>
        <imgCaption :text="image.caption"></imgCaption>

    </section>
    
</template>

<script>
import {eventBus} from '../main'
import imgCaption from './Caption'
    export default {
        props:['image'],
        components:{
            imgCaption
        },
        methods:{
            background(img){
                let div =this.$refs.img
                div.style.backgroundImage = "url('"+img.src+"')";
            },
            
        },
        mounted(){
            this.$nextTick(()=>{
                this.background(this.image);
                
            })
            eventBus.$on('showImage',(img)=>{
                    this.background(img);
                    
            })
            
            
        }
    }
</script>

<style scoped>
.container{
    width: 100%;
    height:500px;
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
}
</style>