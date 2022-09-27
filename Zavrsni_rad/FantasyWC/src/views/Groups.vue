<template>
    <div class="container">
        <h1>Groups</h1>
        <div class="groups-content">
            <table v-for="item in groups">
                <tr><td>{{item.group_name}}</td></tr>
                <tr><td><span :class="`fi fi-${item.team1_code}`"></span>{{item.team1}}</td></tr>
                <tr><td><span :class="`fi fi-${item.team2_code}`"></span>{{item.team2}}</td></tr>
                <tr><td><span :class="`fi fi-${item.team3_code}`"></span>{{item.team3}}</td></tr>
                <tr><td><span :class="`fi fi-${item.team4_code}`"></span>{{item.team4}}</td></tr>
            </table>
        </div>
    </div>
</template>

<script setup>    
    import {ref} from 'vue'

    let groups = ref([]);

    fetch('http://localhost:3000/groups')
    .then(response=>response.json())
    .then(data=>groups.value = data.slice())

    // let groups = [
    //     {name: 'A', teams: [{team:'Qatar', code:'qa'},{team:'Ecuador', code:'ec'},{team:'Netherlands', code:'nl'},{team:'Senegal', code:'sn'}]},
    //     {name: 'B', teams: [{team:'England', code:'gb-eng'},{team:'IR Iran', code:'ir'},{team:'United States', code:'us'},{team:'Wales', code:'gb-wls'}]},
    //     {name: 'C', teams: [{team:'Argentina', code:'ar'},{team:'Mexico', code:'mx'},{team:'Poland', code:'pl'},{team:'Saudi Arabia', code:'sa'}]},
    //     {name: 'D', teams: [{team:'Argentina', code:'ar'},{team:'Mexico', code:'mx'},{team:'Poland', code:'pl'},{team:'Saudi Arabia', code:'sa'}]},
    //     {name: 'E', teams: [{team:'Argentina', code:'ar'},{team:'Mexico', code:'mx'},{team:'Poland', code:'pl'},{team:'Saudi Arabia', code:'sa'}]},
    //     {name: 'F', teams: [{team:'Argentina', code:'ar'},{team:'Mexico', code:'mx'},{team:'Poland', code:'pl'},{team:'Saudi Arabia', code:'sa'}]},
    //     {name: 'G', teams: [{team:'Brazil', code:'br'},{team:'Serbia', code:'rs'},{team:'Switzerland', code:'ch'},{team:'Cameroon', code:'cm'}]},
    //     {name: 'H', teams: [{team:'Argentina', code:'ar'},{team:'Mexico', code:'mx'},{team:'Poland', code:'pl'},{team:'Saudi Arabia', code:'sa'}]}
    // ]


</script>

<style lang="scss">
    .groups-content{
        display: flex;
        flex-direction: row;

        table{
            width: 24%;
        }
    }
</style>