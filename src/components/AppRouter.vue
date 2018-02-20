<!-- Router.vue -->
<template>
    <component :is="routedComponent"></component>
</template>

<script>
    // Router.js
    //import HomePage from "./HomePage";
    //import ArticlesPage from "./ArticlesPage";
    import { listen } from "./../history";

    const routes = {
        //"/": HomePage,
        "/": () => import("./HomePage"),
        //"/articles": ArticlesPage
        "/articles": () => import("./ArticlesPage")
    };

    export default {
        data() {
            return { current: window.location.pathname };
        },
        computed: {
            routedComponent() {
                return routes[this.current];
            }
        },
        render(createElement) {
            //return createElement(this.routedComponent);
            return createElement(() => Promise.resolve('<div>Hey boy</div>'));
        },
        created() {
            listen((route, previousRoute) => {
                this.current = route
            });

            window.addEventListener(
                "popstate",
                event => (this.current = window.location.pathname)
            );
        }
    };



</script>