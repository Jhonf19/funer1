<template>
    <div>
        <h2>components 15q</h2>
        <pulse-loader :loading="this.loading" :color="this.color" ></pulse-loader>
        <fade-loader :loading="this.loading" ></fade-loader>
        <vue-element-loading :active="this.loading" spinner="spinner" :isFullScreen="true" :color="this.color"/>
    </div>
</template>

<script>
        import PulseLoader from 'vue-spinner/src/PulseLoader.vue'
        import FadeLoader from 'vue-spinner/src/FadeLoader.vue'
        import VueElementLoading from 'vue-element-loading'
    export default {
        
        components: {
             PulseLoader,
             FadeLoader,
             VueElementLoading
        },
        data(){
            
            return {
                loading:false,
                color:'#4233FF'

            }
        },
        mounted(){
            // console.log('ok vue');
            
            
        }
    }
</script>

<style lang="css" scoped>

</style>