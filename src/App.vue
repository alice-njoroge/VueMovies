<template>
    <v-app>
        <v-toolbar app>
            <v-toolbar-title class="headline text-uppercase">
                <span>ALIMovies</span>
                <span class="font-weight-light">The Movies NInja</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-flex xs12 sm6 md3>
                <v-text-field
                        label='Movie Name'
                        v-model='searchString'
                >
                </v-text-field>
            </v-flex>
            <v-btn
                    flat
                    :disabled="!dataAvailable"
                    @click="searchMovie">
                <span class="mr-2">Search</span>
            </v-btn>
        </v-toolbar>

        <v-content>
            <router-view></router-view>
        </v-content>
    </v-app>
</template>

<script>

    export default {
        name: 'App',
        components: {},
        data() {
            return {
                searchString: ''
            }
        },
        methods: {
            searchMovie() {
                this.$router.push('/search/' + this.searchString)
                this.searchString = ''
            }
        },
        computed: {
            dataAvailable() {
                return this.searchString !== null && this.searchString !== ''
            }
        }
    }
</script>
