<template>
    <section>
        <div> {{ text() }}</div>
    </section>
</template>

<script>
    export default {
        methods:{
            text(text){
                return text;
            }
        },
        mounted(){
            this.nextTick(()=>{
               
            })
             eventBus.$on('showImage',(img)=>{
                this.text(img.caption)
                // this.caption(img);
            })
        }
    }

</script>

<style scoped>

</style>