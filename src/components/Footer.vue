<template>
    <footer>
        <Logo/>
        <a 
          href="hppts://gitup.com/ParkYoungWoong"
          traget="_blank"
        > 
        (c){{new Date().getFullYear()}} Heropy
        </a>
    </footer>
</template>
<script>
import Logo from '~/components/Logo'

export default {
    components:{
        Logo
    }
}
</script>
<style lang="scss" scoped>
 footer{
     padding: 70px 0;
     text-align: center;
     opacity: .3;
     .logo{
         display: block;
         margin-bottom: 4px;
     }
 }
</style>