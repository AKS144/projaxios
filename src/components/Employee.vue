<template>
    <div>
        <h1>Employee</h1>
        <div>
            <table border="1px">
                <tr>                 
                    <td>Name</td>
                    <td>Salary</td>
                    <td>Age</td>
                </tr>
                <tr v-for="item in list" v-bind:key="item.id">                 
                    <td>{{item.employee_name}}</td>
                    <td>{{item.employee_salary}}</td>
                    <td>{{item.employee_age}}</td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import VueAxios from 'vue-axios'
import axios from 'axios';
Vue.use(VueAxios,axios)

export default {
    name:"Employee",
    data(){
        return {
            list:undefined,
        }
    },
    mounted()//lifecycle initialize when document/DOM is ready
    {
         Vue.axios.get('http://dummy.restapiexample.com/api/v1/employees').then(response=>{
               this.list=response.data.data
               console.warn(response.data.data)
         })
    }
}
</script>