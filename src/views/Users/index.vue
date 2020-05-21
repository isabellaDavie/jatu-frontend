<template>
  <div class="users-view">
      <h3>Users</h3>
      <hr class="w-100">
      <users-table :users='users' ></users-table>
  </div>
</template>

<script>
import UsersAPI from '@/api/users.api.js'
import UsersTable from '@/components/tables/UsersTable.vue'

export default {

    name:'users',

    components:{
        UsersTable
    },

    data(){
        return{
            users:null,
            loading:false
        }
    },



    async created(){
        await this.fetchData()
        console.log('this.users :', this.users);
    }, 

    methods:{

        async fetchData(){
            this.loading = !this.loading
            const results = await UsersAPI.get()
            this.users = results.users
            this.loading = !this.loading
        }
    }

}
</script>

<style lang="scss" scoped>

</style>