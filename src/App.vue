<template>
    <v-app>
        <div id="header">
        </div>
        <v-content>
            <div id="main">
                <EventListPage/>
            </div>
        </v-content>
        <div id="footer">
        </div>
    </v-app>
</template>

<script>
    import EventListPage from './components/EventListPage';

    export default {
        name: 'App',
        components: {
            EventListPage,
        },
        data: () => ({
            //
        }),
    };
</script>
