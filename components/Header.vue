<template>
    <header class="header">
        <nav class="nav">
            <NuxtLink to="/">
                <h1>Poor Boys Bar</h1>
                <h5>1328 St Bernard Ave <br> New Orleans, LA 70116</h5>
            </NuxtLink>
            <div>
                <h1>
                    <NuxtLink :to="infoRoute">{{ isInfoPage ? "close" : "info" }}</NuxtLink>
                </h1>
            </div>
        </nav>
    </header>
</template>

<script>
    export default {
        props: {
                isInfoPage: {
                    type: Boolean,
                    required: false
            }
        },
        computed: {
            infoRoute() {
                return this.isInfoPage ? "/" : "/info"
            }
        }
    }
</script>
