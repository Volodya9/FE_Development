<template>
    <h1>Teams</h1>
    <table v-for="item in groups">
        <tr><td>{{item.group_name}}</td></tr>
        <tr><td><span :class="`fi fi-${item.team1_code}`"></span>{{item.team1}}</td></tr>
        <tr><td><span :class="`fi fi-${item.team2_code}`"></span>{{item.team2}}</td></tr>
        <tr><td><span :class="`fi fi-${item.team3_code}`"></span>{{item.team3}}</td></tr>
        <tr><td><span :class="`fi fi-${item.team4_code}`"></span>{{item.team4}}</td></tr>
    </table>
    <button @click="klikniMe">klikni me</button>
</template>

<script setup>
    import {ref} from 'vue'
import GroupStage from '../components/GroupStage.vue'

    let groups = ref([]);

    fetch('http://localhost:3000/groups')
    .then(response=>response.json())
    .then(data=>groups.value = data.slice())

    function klikniMe(){
        console.log(groups.value[0])
    }
</script>