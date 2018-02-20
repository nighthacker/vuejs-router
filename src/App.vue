<!-- App.vue -->
<template>
  <div>
    <button @click="goTo('/articles')">Go to Articles</button>
    <button @click="goTo('/')">Go to Home</button>
    <app-router></app-router>
  </div>
</template>

<script>
    import AppRouter from "./components/AppRouter";
    import { push } from "./history";

    export default {
        components: {
            AppRouter
        },
        methods: {
            goTo(route) {
                push(route);
            }
        }
    };
</script>
