<template>
    <section class="container">
        <div class="caption"> {{ textCaption(text) }}</div>
    </section>
</template>

<script>
import {eventBus} from '../main'
    export default {
        props:['text'],
        methods:{
            textCaption(text){
                return text;
            }
        },
        mounted(){
            this.$nextTick(()=>{
               this.textCaption(this.text);
            })
             eventBus.$on('showImage',(img)=>{
                this.textCaption(img.caption)
            })
        }
    }

</script>

<style scoped>
.caption{
    padding:10px ;
}
.container{
    background: white
}
</style>