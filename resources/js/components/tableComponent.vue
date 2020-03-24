<template>
    <div>
            <vue-element-loading :active="this.data.loading" spinner="spinner" :isFullScreen="true" :color="this.data.color"/>
        <div>
            <table class="table table-bordered table-striped">
                <thead>
                    <th>#</th>
                    <th>Nombre</th>
                </thead>
                <tbody>
                    <tr v-for="(cus, index) in this.data.dataTable.data" v-bind:key="index">
                        <td>{{ index+1 }}</td>
                        <td>{{ cus.name }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <pagination :align="this.data.align" @pagination-change-page="this.getCustomers" :limit="10" :data="this.data.dataTable">
            <span slot="prev-nav">&lt; Previous</span>
            <span slot="next-nav">Next &gt;</span>
        </pagination>
    </div>
</template>

<script>
import VueElementLoading from 'vue-element-loading'
    export default {
         components: {
            //  PulseLoader,
            //  FadeLoader,
             VueElementLoading
        },
        data(){
            return {
                data:{
                    dataTable:{},
                    align:'center',
                    loading:false,
                    color:'#4233FF'
                }
            }
        },
        mounted(){
            this.getCustomers()
            // this.loading = true
            },
        methods: {
            getCustomers(page = 1){
                this.data.loading = true
                
                axios.get('/getCusomers?page=' + page)
                .then(res => {
                    // console.log(res.data.data)
                    this.data.dataTable = res.data
                    this.data.loading = false
            })
                .catch(error => console.log(error))
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>