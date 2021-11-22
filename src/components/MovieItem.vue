<template>
    <div class="movie" :style="{ backgroundImage:`url(${movie.Poster})`}">
       <div class="info">
           <div class="year">
               {{movie.Year}}
           </div>
           <div class="title">
               {{movie.Title}}
           </div>
       </div>
    </div>
</template>
<script>
export default {
   props:{
       movie:{
           type:Object,
           defaults:()=>({

           })
       }
   }
}
</script>
<style lang="scss" scoped>
@import "~/scss/main";

 .movie{
     $width:200px;
     width:$width;
     height:$width*3 /2;
     margin:10px;
     border-radius: 4px;
     background-color: $gray-400;
     background-size:cover;
     overflow: hidden;
     position: relative;
     box-sizing: border-box;
     .info {
         background-color:rgba($black,.3);
         width:100%;
         padding:14px;
         position:absolute;
         text-align:center;
         left:0;
         bottom:0;
         backdrop-filter: blur(10px);
         .year{
               color:$primary;
           }           
         .title{
           color:$white;
           white-space: nowrap;
           text-overflow: ellipsis;
           overflow: hidden;         
         }        
     }
     &:hover::after{
         content:"";
         position:absolute;
         top:0;
         left:0;
         right:0;
         bottom:0;
         border:6px solid $primary
     }
 }
</style>