<template>
    <div class="gallery">
        <BigCard :image="images[0]"></BigCard>
        <thumbs :images="images"></thumbs>
    </div>
</template>

<script>
import thumbs from './Thumbs';
import BigCard from './BigCard';
    export default {
        data(){
            return{
                images: [
                    {
                        src:'https://cdn.vox-cdn.com/thumbor/VQizzEYeE7EgYWk9Q2KLdUmtaOo=/0x0:6000x4000/1200x800/filters:focal(1308x1703:2268x2663)/cdn.vox-cdn.com/uploads/chorus_image/image/65944369/TheWitcher_101_Unit_06900_RT.fk3ph4dhp.0.jpg',
                        caption: 'tes1'
                    },
                    {
                        src:'https://static01.nyt.com/images/2019/12/19/arts/19witcher/19witcher-jumbo-v3.jpg?quality=90&auto=webp',
                        caption:'tes2'
                    },
                    {
                        src:'https://anewspost.com/wp-content/uploads/2019/12/netflix-witcher.jpg', 
                        caption: 'tes3'
                    }
                ]
            }
            
        },
        components:{
            thumbs,
            BigCard
        }
    }
</script>

<style scoped>
.gallery{
    max-width: 40rem;
}
</style>