<template>
    <div class="container">
        <h2>Sign up</h2>
        <form action="mysite.php" @submit.prevent="handleSubmit">
            <table>
                <tr><td>Username</td></tr>
                <tr><td><input type="text" class="form-control" v-model="username"></td></tr>
                <tr><td>Email</td></tr>
                <tr><td><input type="email" class="form-control" v-model="email"></td></tr>
                <tr><td>Password</td></tr>
                <tr><td><input type="password" name="" id="" class="form-control" v-model="password"></td></tr>
                <tr><td><input type="submit" value="submit"></td></tr>
            </table>
        </form>
    </div>
</template>
<script setup>
    import {ref} from 'vue'
    import {useRouter} from 'vue-router';

    let username = ref('');
    let email = ref('');
    let password = ref('');

    const router = useRouter();

    async function handleSubmit(){
        const response = await fetch('http://localhost:3000/signin', {
            method: 'POST',
            body: JSON.stringify({
                username: username.value,
                password: password.value
            }),
            headers: { 'Content-type' : 'application/json;'},
        })
        .then(response=>response.json());
        alert('Successfully created user!');
        router.push('/fantasy');

    }
</script>