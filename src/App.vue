<script >
import HeaderComp from './components/HeaderComp.vue';


  export default{
    components:{
      HeaderComp    
    },
    data() {
        return {};
    },
    mounted() {
    },
    methods: {},
    components: { HeaderComp }
}
</script>

<template>
  <HeaderComp></HeaderComp>

  <RouterView></RouterView>
</template>

<style lang="scss">
@use './style/main.scss';
</style>
