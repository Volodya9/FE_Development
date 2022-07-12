<template>
    <li>
        <div class="itemContainer">
            <span>{{item}}</span>
            <button class="removeBtn" @click="$emit('removeItem', index)">Remove</button>
        </div>
    </li>
</template>

<script setup>
    defineProps({
        item: String
    })
</script>

<style>
    li{
        list-style-type: none;
    }    

    .itemContainer{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        border: 2px solid hsla(0,0%,100%,.35);    
        border-radius: 6px;
        padding: 12px 20px;    
        margin-bottom: 10px;
    }

    span{
        margin-left: 10px;    
        color: #fff;
        font-size: 14px;
    }

    .removeBtn{
        background-color: #a0a4d9;
        border: 1px solid #a0a4d9;
        border-radius: 6px;
        color: #1f2023;
        margin-right: 10px;
        outline: none;
        padding: 6px;
        cursor: pointer;
    }


</style>