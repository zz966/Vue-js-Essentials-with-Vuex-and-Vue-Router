<template>
    <div>
        <AppHeader>1</AppHeader>
        <div class="ui contaniner">
            <router-view></router-view>
        </div>
        
    </div>
</template>

<script>
import AppHeader from './components/AppHeader'

export default {
    name:'App',
    components:{
        AppHeader
    }
};
</script>

<style scoped>

</style>