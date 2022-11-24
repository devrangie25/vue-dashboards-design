<template>
  <div>
    <v-row>
      <!-- First column -->
      <v-col cols="12" md="8">
        <div>
          <v-row>
            <v-col cols="12" md="7" class="d-flex align-center">
              <v-text-field
                hide-details="auto"
                class="rounded-lg"
                solo
                append-icon="mdi-magnify"
                background-color="#3b3b4d"
              ></v-text-field>
            </v-col>
            <v-col cols="12" md="5" class="d-flex justify-end align-center">
              <v-btn
                class="mr-1 rounded-lg"
                depressed
                height="48"
                color="#3b3b4d"
              >
                <v-icon size="25" color="#4163cf"> mdi-bell </v-icon>
              </v-btn>
              <v-btn
                class="ml-1 rounded-lg"
                depressed
                height="48"
                color="#3b3b4d"
              >
                <v-icon size="25" color="#4163cf"> mdi-cog </v-icon>
              </v-btn>
            </v-col>
          </v-row>

          <v-row>
            <v-col cols="12" md="12">
              <v-card color="#4363d1" class="rounded-lg pa-1" height="200">
                <v-card-text>
                  <v-row>
                    <v-col cols="12" md="6">
                      <div
                        class="
                          date-time
                          pa-2
                          rounded-lg
                          d-flex
                          align-center
                          justify-start
                        "
                      >
                        <v-icon size="22"> mdi-calendar-month </v-icon>
                        <span class="mx-1"> Apr 24, 2022 2:20 pm </span>
                      </div>

                      <div class="greetings">
                        <span
                          class="d-flex headline font-weight-bold white--text"
                        >
                          Good Day, Dr. James
                        </span>
                        <span
                          class="
                            d-flex
                            subtitle-2
                            white--text
                            font-weight-light
                          "
                        >
                          Have a Nice Monday!
                        </span>
                      </div>
                    </v-col>
                    <v-col cols="12" md="6" class="d-flex justify-end">
                      <v-img src="/img/bighead.svg" height="160" contain />
                    </v-col>
                  </v-row>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <v-row>
            <v-col
              v-for="(item, i) in smallWidgetData"
              :key="i"
              cols="12"
              md="4"
            >
              <cw-small
                height="100%"
                :title="item.title"
                :color="item.color"
                :count="item.count"
                :average="item.average"
                :subtitle="item.subtitle"
              />
            </v-col>
          </v-row>

          <v-row>
            <v-col v-for="i in 2" :key="i" cols="12" md="6">
              <cw-medium height="100%" />
            </v-col>
          </v-row>
        </div>
      </v-col>

      <!-- Second column -->
      <v-col cols="12" md="4">
        <div>
          <v-row>
            <v-col cols="12">
              <div>
                <v-card
                  height="100%"
                  color="#252537"
                  class="pa-0 rounded-lg"
                  flat
                >
                  <v-app-bar color="#4264ce" rounded="lg" flat>
                    <v-toolbar-title class="overline font-weight-bold"
                      >My Profile</v-toolbar-title
                    >
                    <v-spacer></v-spacer>

                    <v-btn icon>
                      <v-icon small>mdi-pencil</v-icon>
                    </v-btn>
                  </v-app-bar>

                  <v-card-text class="pa-2 mt-2">
                    <div>
                      <v-row>
                        <v-col
                          cols="12"
                          md="4"
                          class="d-flex justify-center align-center"
                        >
                          <v-avatar size="100">
                            <v-img
                              width="100%"
                              alt="user"
                              src="https://images.pexels.com/photos/5199158/pexels-photo-5199158.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                            />
                          </v-avatar>
                        </v-col>
                        <v-col cols="12" md="8" class="d-flex align-center">
                          <section>
                            <div
                              class="font-weight-bold profile-title white--text"
                            >
                              Dr. Alisha James
                            </div>
                            <div class="subtitle-1 overline">
                              Dermathologist
                            </div>
                            <div>
                              <v-icon> mdi-map-marker </v-icon>
                              <span class="body-2"> Cebu, Philippines </span>
                            </div>
                          </section>
                        </v-col>
                      </v-row>
                    </div>

                    <div class="pa-4 mt-2">
                      <v-row>
                        <v-col cols="12" md="4">
                          <div class="text-center caption">Date Birth</div>
                          <div
                            class="
                              text-center
                              body-1
                              font-weight-bold
                              white--text
                            "
                          >
                            17.07.86
                          </div>
                        </v-col>
                        <v-divider vertical></v-divider>
                        <v-col cols="12" md="4">
                          <div class="text-center caption">Blood</div>
                          <div
                            class="
                              text-center
                              body-1
                              font-weight-bold
                              white--text
                            "
                          >
                            17.07.86
                          </div>
                        </v-col>
                        <v-divider vertical></v-divider>
                        <v-col cols="12" md="4">
                          <div class="text-center caption">Working Hours</div>
                          <div
                            class="
                              text-center
                              body-1
                              font-weight-bold
                              white--text
                            "
                          >
                            17.07.86
                          </div>
                        </v-col>
                      </v-row>
                    </div>
                  </v-card-text>
                </v-card>
              </div>
            </v-col>
            <v-col cols="12">
              <div>
                <v-card height="575" color="#252537" flat class="rounded-lg">
                  <v-app-bar color="#4264ce" rounded="lg" flat>
                    <v-toolbar-title class="overline font-weight-bold"
                      >New Patients</v-toolbar-title
                    >
                    <v-spacer></v-spacer>
                    <NuxtLink
                      to="/dashboard/medical"
                      class="white--text button"
                    >
                      see all
                    </NuxtLink>
                  </v-app-bar>

                  <v-card-text>
                    <div>
                      <v-list subheader two-line color="transparent">
                        <v-list-item v-for="file in files" :key="file.title">
                          <v-list-item-avatar>
                            <v-img
                              width="100%"
                              alt="user"
                              src="https://images.pexels.com/photos/5199158/pexels-photo-5199158.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                            />
                          </v-list-item-avatar>

                          <v-list-item-content>
                            <v-list-item-title
                              v-text="file.title"
                            ></v-list-item-title>

                            <v-list-item-subtitle
                              v-text="file.subtitle"
                            ></v-list-item-subtitle>
                          </v-list-item-content>

                          <v-list-item-action>
                            <div class="d-flex">
                              <v-btn icon>
                                <v-icon size="20" color="#1da097"
                                  >mdi-information</v-icon
                                >
                              </v-btn>
                              <v-btn icon class="mx-n2">
                                <v-icon size="20" color="#b96d74"
                                  >mdi-file-eye-outline</v-icon
                                >
                              </v-btn>
                              <v-btn icon>
                                <v-icon size="20" color="#4962b8"
                                  >mdi-phone</v-icon
                                >
                              </v-btn>
                            </div>
                          </v-list-item-action>
                        </v-list-item>
                      </v-list>
                    </div>
                  </v-card-text>
                </v-card>
              </div>
            </v-col>
          </v-row>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'MedicalDashboard',
  data() {
    return {
      smallWidgetData: [
        {
          title: 'Offline Work',
          count: 27,
          subtitle: 'Hospital Patients',
          average: '-6',
          color: '#b96d74',
        },
        {
          title: 'Online Work',
          count: 9,
          subtitle: 'Online Consultations',
          average: '+12',
          color: '#1da097',
        },
        {
          title: 'Laboratory Work',
          count: 19,
          subtitle: 'Laboratory Analysis',
          average: '+0',
          color: '#4962b8',
        },
      ],
      today: '2019-01-10',
      tracked: {
        '2019-01-09': [23, 45, 10],
        '2019-01-08': [10],
        '2019-01-07': [0, 78, 5],
        '2019-01-06': [0, 0, 50],
        '2019-01-05': [0, 10, 23],
        '2019-01-04': [2, 90],
        '2019-01-03': [10, 32],
        '2019-01-02': [80, 10, 10],
        '2019-01-01': [20, 25, 10],
      },
      colors: ['#b96d74', '#1da097', '#4962b8'],
      category: ['Development', 'Meetings', 'Slacking'],
      files: [
        {
          color: 'blue',
          icon: 'mdi-clipboard-text',
          subtitle: 'Jan 20, 2014',
          title: 'Tim Duncan',
        },
        {
          color: 'amber',
          icon: 'mdi-gesture-tap-button',
          subtitle: 'Jan 10, 2014',
          title: 'Kevin Durant',
        },
        {
          color: 'amber',
          icon: 'mdi-gesture-tap-button',
          subtitle: 'Jan 10, 2014',
          title: 'Stephen Curry',
        },
        {
          color: 'amber',
          icon: 'mdi-gesture-tap-button',
          subtitle: 'Jan 10, 2014',
          title: 'Lebron James',
        },
        {
          color: 'amber',
          icon: 'mdi-gesture-tap-button',
          subtitle: 'Jan 10, 2014',
          title: 'Kobe Bryant',
        },
        {
          color: 'amber',
          icon: 'mdi-gesture-tap-button',
          subtitle: 'Jan 10, 2014',
          title: 'James Harden',
        },
      ],
    }
  },
}
</script>

<style scoped>
.date-time {
  background-color: #738ce4;
}

.greetings {
  bottom: 1rem !important;
  position: absolute;
}

.profile-title {
  font-size: 1.3rem;
  letter-spacing: 0.1rem;
}
</style>
