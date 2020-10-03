<template>
<div id="wrapper">
    <header-component></header-component>

    <todo-component></todo-component>
</div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import TodoComponent from './components/TodoComponent.vue';

export default {
    components: {
        HeaderComponent,
        TodoComponent
    }
}
</script>
