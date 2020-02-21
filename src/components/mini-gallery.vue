<template>
    <div class="gallery">
        
        <div class="container">
            <span class="btn" @click="prev()"> ⏪ </span>
            <span class="btn right" @click="next()"> ⏩ </span>
            <div class="wide" :style="{ 'background-image': 'url(' + active.src + ')' }"></div>
            <imgCaption :text="active.caption"></imgCaption>
        </div>
        
        <thumbs :images="images"></thumbs>
    </div>
</template>

<script>
import thumbs from './Thumbs';
import imgCaption from './Caption'
import {eventBus} from '../main'
    export default {
        data(){
            return{
                images: [
                    {
                        src:'https://images.unsplash.com/photo-1459262838948-3e2de6c1ec80?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=80',
                        caption: 'tes1'
                    },
                    {
                        src:'https://static01.nyt.com/images/2019/12/19/arts/19witcher/19witcher-jumbo-v3.jpg?quality=90&auto=webp',
                        caption:'tes2'
                    },
                    {
                        src:'https://anewspost.com/wp-content/uploads/2019/12/netflix-witcher.jpg', 
                        caption: 'tes3'
                    },
                    {
                        src:'https://www.geek.com/wp-content/uploads/2020/01/YenneferOne1620-600x352.jpg', 
                        caption: 'tes4'
                    },
                    {
                        src:'https://bi.im-g.pl/im/a5/59/18/z25531813V,-Wiedzmin----serial-Netflixa--Joey-Batey-w-roli-Ja.jpg', 
                        caption: 'tes5'
                    }
                ],
                active: '',
                key: 0

            }
            
        },
        mounted(){
           eventBus.$on('showImage',((img)=>{
               this.active = img
           }))
            this.init(this.key)
        },
        methods:{
            init(key){
                console.log(this.images.length)
                console.log(key)
                if (key === this.images.length || key < 0) {
                    this.key = 0
                   this.init(0)
                   
                   return
                }
                this.active = this.images[key]
                this.key = key
            },
            next(){
                this.key = this.key + 1
                this.init(this.key)
            },  
            prev(){
                this.key = this.key - 1
                this.init(this.key)
            }
        },

        components:{
            thumbs,
            imgCaption
        }
    }
</script>

<style scoped>
.gallery{
    margin: 0 auto;
    max-width: 40rem;
    
}
.container{
    position: relative;
    background: white;
    box-shadow: 0px 1px 4px #888;
    margin-bottom: 10px;
}
img{
    width: 100%;
}
.btn{
    cursor: pointer;
    position: absolute;
    background: white;
    padding: 4px;
    border-radius: 2px;
    top: 50%;
}
.btn.right{
    right:0;
}
.wide{
    
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    padding-bottom: 56.66%
}
</style>