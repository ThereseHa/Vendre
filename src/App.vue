<template>
    <div id="app">
        <NavBar />
        <EmployeeList />
    </div>
</template>

<script>
    import EmployeeList from './components/EmployeeList.vue'
    import NavBar from './components/NavBar.vue'

    export default {
        components: {
            EmployeeList,
            NavBar
        }
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
    body {
        font-family: 'Roboto', sans-serif;
    }
</style>
