<template>
    <div>
        <v-container>
            <v-row>
                <v-col lg="12">
                    <v-stepper v-model="e1">
                        <v-stepper-header>
                            <v-stepper-step :complete="e1 > 1" step="1"> Choose destination</v-stepper-step>

                            <v-divider></v-divider>

                            <v-stepper-step :complete="e1 > 2" step="2"> Choose date </v-stepper-step>

                            <v-divider></v-divider>

                            <v-stepper-step step="3"> Step 3 </v-stepper-step>
                        </v-stepper-header>

                        <v-stepper-items>
                            <v-stepper-content step="1">
                                <v-form ref="destinationForm" class="mt-2">
                                    <v-autocomplete v-model="selectedDestination" :items="destinations" dense outlined
                                        rounded :rules="destinationRules" label="Destination"></v-autocomplete>
                                </v-form>
                                <!-- <v-btn color="primary" @click="selectedDestination ? e1 = 2 : null"> Continue </v-btn>

                                <v-btn text @click="e1 = 1"> Cancel </v-btn> -->
                                <v-btn block color="primary" @click="searchFlights">Search flights</v-btn>
                            </v-stepper-content>

                            <v-stepper-content step="2">
                                <!-- <v-card class="mb-12" color="grey lighten-1" height="200px"></v-card>-->
                                <v-row>
                                    <v-col cols="12" sm="6">
                                        <v-date-picker v-model="dates" range></v-date-picker>
                                    </v-col>
                                    <v-col cols="12" sm="6">
                                        <v-text-field v-model="dateRangeText" label="Date range"
                                            prepend-icon="mdi-calendar" readonly></v-text-field>
                                        model: {{ dates }}
                                    </v-col>
                                </v-row>
                                <v-btn color="primary" @click="e1 = 3"> Continue </v-btn>

                                <v-btn text @click="e1 = 1"> Cancel </v-btn>

                            </v-stepper-content>

                            <v-stepper-content step="3">
                                <v-card class="mb-12" color="grey lighten-1" height="200px"></v-card>

                                <v-btn color="primary" @click="e1 = 1"> Continue </v-btn>

                                <v-btn text @click="e1 = 2"> Cancel </v-btn>
                            </v-stepper-content>
                        </v-stepper-items>
                    </v-stepper>
                    <div>

                        <div>booking</div>
                    </div>
                </v-col>
            </v-row>
        </v-container>

    </div>
</template>

<script>
export default {
    name: "Booking",
    data: () => ({
        e1: 1,
        destinations: ['Moscow', 'Saint-Petersburg'],
        selectedDestination: 'Destination',
        destinationRules: [(value) => !!value || 'You need to choose destination'],
        dates: ['2019-09-10', '2019-09-20'],
    }),
    computed: {
        dateRangeText() {
            return this.dates.join(' ~ ')
        },
    },
    methods: {
        searchFlights() {
            const isValid = this.$refs['destinationForm'].validate()
            console.log(isValid)

            if (isValid) { this.e1 = 2 }
            else {
                // this.$refs['destinationForm'].resetValidation()
                setTimeout(() => {
                    this.$refs['destinationForm'].resetValidation()
                }, 1000)
            }
        }
    }
};
</script>

<style lang="scss" scoped>
</style>
