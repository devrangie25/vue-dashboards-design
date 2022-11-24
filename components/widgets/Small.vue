<template>
  <div>
    <v-card class="rounded-lg pa-1" color="#252537" :height="height" flat>
      <v-card-text>
        <div class="d-flex justify-space-between align-center mb-1">
          <div class="text-uppercase subtitle-2 text--secondary">
            {{ title }}
          </div>
          <div>
            <v-btn icon small>
              <v-icon> mdi-dots-horizontal </v-icon>
            </v-btn>
          </div>
        </div>

        <div>
          <v-row align="end">
            <v-col cols="12" md="5">
              <div>
                <v-sheet
                  class="v-sheet--offset mx-auto pa-4"
                  color="#35344c"
                  rounded="lg"
                  height="100%"
                >
                  <v-sparkline
                    :value="value"
                    :color="color"
                    line-width="4"
                    height="350"
                  ></v-sparkline>
                </v-sheet>
              </div>
            </v-col>

            <v-col cols="12" md="7">
              <div class="title font-weight-bold pb-1">{{ count }}</div>
              <div class="caption">{{ subtitle }}</div>
              <div :class="`caption avg rounded-lg mt-1 px-2 py-1 ${color}`">
                {{ average }}% than average
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
    title: {
      default: 'Offline Work',
      required: false,
      type: String,
    },
    count: {
      default: 0,
      required: false,
      type: Number,
    },
    subtitle: {
      default: 'Online Consultations',
      required: false,
      type: String,
    },
    average: {
      default: '+0',
      required: false,
      type: String,
    },
    color: {
      default: '#e49b56',
      required: false,
      type: String,
    },
  },

  data() {
    return {
      labels: ['12am', '3am', '6am', '9am', '12pm', '3pm', '6pm', '9pm'],
      value: [200, 675, 410, 390, 310, 460, 250, 240],
    }
  },
}
</script>

<style scoped>
.widget-caption {
  position: absolute !important;
  bottom: 1rem !important;
}

.avg {
  background-color: #35344c;
}
</style>