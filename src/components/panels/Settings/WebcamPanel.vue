<style>

</style>

<template>
    <v-card>
        <v-toolbar flat dense >
            <v-toolbar-title>
                <span class="subheading"><v-icon left>mdi-webcam</v-icon>Webcam</span>
            </v-toolbar-title>
        </v-toolbar>
        <v-card-text>
            <v-container px-0 py-0>
                <v-row>
                    <v-col class="py-2">
                        <v-text-field
                            v-model="webcamUrl"
                            hide-details
                            label="Webcam URL"
                        ></v-text-field>
                    </v-col>
                </v-row>
                <v-row v-if="rotationEnabled">
                    <v-col class="py-2" col-auto>
                        <v-switch v-model="rotate" hide-details label="Rotate" class="mt-0"></v-switch>
                    </v-col>
                    <v-col>
                        <v-select :items="[{ text: '90 degrees', value: 90 }, { text: '270 degrees', value: 270 }]" v-model="rotateDegrees" hide-details></v-select>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col class="py-2">
                        <v-switch v-model="flipX" hide-details label="Flip webcam horizontally" class="mt-0"></v-switch>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col class="py-2">
                        <v-switch v-model="flipY" hide-details label="Flip webcam vertically" class="mt-0"></v-switch>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col class="py-2">
                        <v-switch v-model="boolNavi" hide-details label="Show in navigation" class="mt-0"></v-switch>
                    </v-col>
                </v-row>
            </v-container>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        components: {

        },
        data: function() {
            return {
                rotationEnabled: false
            }
        },
        computed: {
            webcamUrl: {
                get() {
                    return this.$store.state.gui.webcam.url;
                },
                set(url) {
                    return this.$store.dispatch('gui/setSettings', { webcam: { url } });
                }
            },
            flipX: {
                get() {
                    return this.$store.state.gui.webcam.flipX;
                },
                set(flipX) {
                    return this.$store.dispatch('gui/setSettings', { webcam: { flipX } });
                }
            },
            flipY: {
                get() {
                    return this.$store.state.gui.webcam.flipY;
                },
                set(flipY) {
                    return this.$store.dispatch('gui/setSettings', { webcam: { flipY } });
                }
            },
            rotate: {
                get() {
                    return this.$store.state.gui.webcam.rotate;
                },
                set(rotate) {
                    return this.$store.dispatch('gui/setSettings', { webcam: { rotate } });
                }
            },
            rotateDegrees: {
                get() {
                    return this.$store.state.gui.webcam.rotateDegrees;
                },
                set(rotateDegrees) {
                    return this.$store.dispatch('gui/setSettings', { webcam: { rotateDegrees } });
                }
            },
            boolNavi: {
                get() {
                    return this.$store.state.gui.webcam.bool;
                },
                set(showNav) {
                    return this.$store.dispatch('gui/setSettings', { webcam: { bool: showNav } });
                }
            },
        },
        methods: {

        }
    }
</script>