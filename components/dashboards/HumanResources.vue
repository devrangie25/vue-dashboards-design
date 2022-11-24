<template>
  <div class="pa-6">
    <v-row>
      <v-col cols="12" md="8">
        <div>
          <v-row>
            <v-col cols="12">
              <v-card
                color="#5066fd"
                class="rounded-lg px-4 py-2"
                height="200"
                flat
              >
                <v-card-text>
                  <v-row>
                    <v-col cols="12" md="6">
                      <div class="headline white--text font-weight-bold">
                        Hello Katie!
                      </div>

                      <div class="body-1 white--text mt-4">
                        You have 16 new applications. It is a lot of work for
                        today! So let's start.
                      </div>

                      <div class="review-it">
                        <NuxtLink
                          to="/dashboard/human-resources"
                          class="white--text"
                        >
                          review it!
                        </NuxtLink>
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
            <v-col cols="12" class="my-n2 d-flex justify-space-between">
              <div class="to-hire-title">You need to hire</div>
              <div>
                <NuxtLink
                  to="/dashboard/human-resources"
                  class="black--text text--secondary"
                >
                  see all
                </NuxtLink>
              </div>
            </v-col>
            <v-col cols="12" md="6" v-for="(item, i) in 4" :key="i">
              <v-card color="#fefefe" class="rounded-lg pa-1" flat>
                <v-card-actions class="mx-4">
                  <div class="display-2 font-weight-bold mr-1">3</div>
                  <v-card-subtitle>
                    <div class="font-weight-bold">Content Designer</div>
                    <div class="text--secondary">
                      {{ `(${10} candidates)` }}
                    </div>
                  </v-card-subtitle>
                  <v-spacer></v-spacer>

                  <v-progress-circular
                    :value="50"
                    size="60"
                    width="6"
                    color="blue-grey"
                  >
                    <template>
                      <div class="caption font-weight-bold">10%</div>
                    </template>
                  </v-progress-circular>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>

          <v-row>
            <v-col cols="12">
              <v-card color="#fefefe" class="rounded-lg pa-1" height="100%" flat>
                <v-app-bar color="transparent" flat denseflat class="pt-2 px-4">
                  <v-toolbar-title class="title font-weight-bold"
                    >Recruitment Progress</v-toolbar-title
                  >
                  <v-spacer></v-spacer>
                  <v-btn
                    color="#5066fd"
                    dark
                    width="120"
                    depressed
                    class="text-none"
                  >
                    See all
                  </v-btn>
                </v-app-bar>

                <v-card-text>
                  <v-data-table
                    :headers="headers"
                    :items="desserts"
                    hide-default-footer
                  >
                    <template v-slot:item.status="{ item }">
                      <v-icon :color="getColor(item.status)">
                        mdi-circle-medium
                      </v-icon>
                      {{ item.status }}
                    </template>
                    <template v-slot:item.actions="{ item }">
                      <v-btn icon>
                        <v-icon size="20">
                          mdi-dots-vertical
                        </v-icon>
                      </v-btn>
                    </template>
                  </v-data-table>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </v-col>

      <v-col cols="12" md="4">
        <div>
          <v-row>
            <v-col cols="12">
              <v-card color="#fefefe" class="rounded-lg" height="400" flat>
                <v-card-title>
                  <v-toolbar dense flat>
                    <v-btn icon>
                      <v-icon>mdi-chevron-left</v-icon>
                    </v-btn>

                    <v-spacer></v-spacer>

                    <v-toolbar-title>
                      {{ getTodayDate }}
                    </v-toolbar-title>

                    <v-spacer></v-spacer>

                    <v-btn icon>
                      <v-icon>mdi-chevron-right</v-icon>
                    </v-btn>
                  </v-toolbar>
                </v-card-title>

                <v-card-text>
                  <v-sheet height="300">
                    <v-calendar
                      :now="today"
                      :value="today"
                      color="primary"
                      ref="calendar"
                    >
                      <template v-slot:day="{ past, date }">
                        <v-row class="fill-height">
                          <template v-if="past && tracked[date]">
                            <v-sheet
                              v-for="(percent, i) in tracked[date]"
                              :key="i"
                              :title="category[i]"
                              :color="colors[i]"
                              :width="`${percent}%`"
                              height="100%"
                              tile
                            ></v-sheet>
                          </template>
                        </v-row>
                      </template>
                    </v-calendar>
                  </v-sheet>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12">
              <v-card
                height="480"
                color="#fefefe"
                flat
                class="rounded-lg pa-1"
              >
                <v-app-bar color="transparent" flat denseflat class="pt-2 px-4">
                  <v-toolbar-title class="title font-weight-bold"
                    >New Applicants</v-toolbar-title
                  >
                  <v-spacer></v-spacer>
                  <NuxtLink
                    to="/dashboard/human-resources"
                    class="text--secondary"
                  >
                    see all
                  </NuxtLink>
                </v-app-bar>
                <v-card-text class="mt-n4">
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
                            class="body-1"
                            v-text="file.title"
                          ></v-list-item-title>

                          <v-list-item-subtitle
                            class="caption"
                            v-text="file.subtitle"
                          ></v-list-item-subtitle>
                        </v-list-item-content>

                        <v-list-item-action>
                          <div class="d-flex">
                            <v-btn icon>
                              <v-icon size="20" color="#1da097"
                                >mdi-account-circle</v-icon
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
            </v-col>
          </v-row>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
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
      colors: ['#1867c0', '#fb8c00', '#000000'],
      category: ['Development', 'Meetings', 'Slacking'],
      month: [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'July',
        'August',
        'September',
        'October',
        'November',
        'December',
      ],
      headers: [
        {
          text: 'Full Name',
          align: 'start',
          sortable: false,
          value: 'fullname',
        },
        { text: 'Profession', value: 'profession' },
        { text: 'Status', value: 'status' },
        { text: '', value: 'actions', sortable: false }
      ],
      desserts: [
        {
          fullname: 'John Doe',
          profession: 'UI/UX Designer',
          status: 'Tech Interview'
        },
        {
          fullname: 'John Doe',
          profession: 'Web Developer',
          status: 'Final Interview'
        },
        {
          fullname: 'John Doe',
          profession: 'Senior Developer',
          status: 'Initial Interview'
        },
        {
          fullname: 'John Doe',
          profession: 'Database Manager',
          status: 'Task'
        },
        {
          fullname: 'John Doe',
          profession: 'Business Analyst',
          status: 'Tech Interview'
        },
      ],
    }
  },

  computed: {
    getTodayDate() {
      return this.month[new Date().getMonth()] + ' ' + new Date().getFullYear()
    },
  },

  methods: {
    getColor(status) {
      if (status === 'Tech Interview') return 'red'
      else if (status  === 'Initial Interview') return 'orange'
      else return 'green'
    },
  },
}
</script>

<style scoped>
.to-hire-title {
  font-weight: 500;
  font-size: 1.3rem;
}

.review-it {
  position: absolute;
  bottom: 1.5rem;
}
</style>