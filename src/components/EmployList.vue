<template>
<div>
<h1>Employe List</h1>   
<div>
    <table border='3px solid grey'>
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
    name:"EmployList",
    data()
    {
        return{
            list:undefined
        }
    },
    mounted()
    {
        Vue.axios.get('http://dummy.restapiexample.com/api/v1/employees')
        .then(resp =>{

            this.list=resp.data.data
            console.warn(resp.data.data)


        })
    }
  }

</script>
<style>
.table
{
    width: 700px;
}
</style>

