<template>
  <div>
    <v-card class="rounded-lg pa-1" color="#252537" :height="height" flat>
      <v-card-text>
        <div class="d-flex justify-space-between align-center">
          <div class="text-uppercase subtitle-2 text--secondary">
            My Scheduled Events
          </div>
          <div>
            <v-btn
              small
              class="text-capitalize rounded-lg"
              depressed
              color="#4365cf"
            >
              <span class="button"> Today </span>
              <v-icon right> mdi-chevron-down </v-icon>
            </v-btn>
          </div>
        </div>

        <div>
          <v-row>
            <v-col cols="12" md="7">
              <div class="pa-4">
                <Doughnut height="180" width="200" />
              </div>
            </v-col>
            <v-col cols="12" md="5" class="my-4">
              <!-- <Doughnut /> -->
              <div class="pa-4 rounded-lg medium-widget-description">
                <section
                  v-for="(item, i) in 3"
                  :key="i"
                  :class="`${i > 0 ? 'mt-2' : ''}`"
                >
                  <div class="font-weight-bold title">2</div>
                  <div class="caption">Consultations</div>
                </section>
              </div>
            </v-col>
          </v-row>
        </div>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    height: {
      default: '100%',
      required: false,
      type: String,
    },
  },

  data() {
    return {
      chartData1: {
        labels: ['January', 'February', 'March'],
        datasets: [{ data: [40, 20, 12] }],
      },
      chartOptions1: {
        responsive: true,
      },
      chartData2: {
        labels: ['VueJs', 'EmberJs', 'ReactJs', 'AngularJs'],
        datasets: [
          {
            backgroundColor: ['#41B883', '#E46651', '#00D8FF', '#DD1B16'],
            data: [40, 20, 80, 10],
          },
        ],
      },
      chartOptions2: {
        responsive: true,
        maintainAspectRatio: false,
      },
    }
  },
}
</script>

<style scoped>
.medium-widget-description {
  background-color: #35374e;
}
</style>