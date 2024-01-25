<template>
  <v-app id="app-container">
    <v-navigation-drawer color="#fefefe" :permanent="['large', 'extra-large'].includes(width)" app v-model="drawer">
      <v-list>
        <v-list-item three-line class="text-center">
          <v-list-item-content>
            <v-list-item-title class="brand"> motivation </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item-group v-model="nav">
          <v-list-item
            :class="`px-10 ${nav === i && 't-item'}`"
            v-for="(item, i) in items"
            :key="i"
            link
          >
            <v-list-item-icon>
              <v-icon :key="i" :color="nav === i ? navIconColor : ''">{{
                item.icon
              }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title
                :class="`body-2 ${
                  nav === i
                    ? 'text--primary font-weight-bold'
                    : 'text--secondary'
                } `"
              >
                {{ item.title }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>

      <template v-slot:append>
        <div class="pa-6">
          <v-card class="pa-4 rounded-lg" flat color="#f5f5fc">
            <v-card-text>
              <div class="d-flex justify-center subtitle-1 font-weight-bold">
                Support 24/7
              </div>
              <div class="d-flex justify-center caption text--disabled">
                Contact us anytime
              </div>
              <div class="d-flex justify-center mt-6">
                <v-btn
                  class="text-capitalize"
                  dark
                  width="130"
                  height="40"
                  depressed
                  color="#5066fd"
                >
                  Start Chat
                </v-btn>
              </div>
            </v-card-text>
          </v-card>
        </div>
      </template>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="transparent"
      class="app-bar-flat px-2"
      height="72"
      flat
      absolute
    >
      <v-app-bar-nav-icon v-if="!['large', 'extra-large'].includes(width)" @click="onClickNavIcon"></v-app-bar-nav-icon>
      <v-toolbar-title>Dashboard</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon class="mr-2">
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon class="mr-2">
        <v-icon>mdi-email-outline</v-icon>
      </v-btn>

      <v-btn icon class="mr-2">
        <v-icon>mdi-bell-outline</v-icon>
      </v-btn>

      <v-avatar color="red" size="40">
        <span class="white--text">CJ</span>
      </v-avatar>

      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-btn width="40" height="40" class="ml-1" v-bind="attrs" v-on="on" icon>
            <v-icon size="25">
              mdi-chevron-down
            </v-icon>
          </v-btn>
        </template>
        <v-list flat>
          <v-list-item v-for="(item, index) in menu" :key="index">
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-main>
      <v-container fluid class="pa-0">
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { title: 'Dashboard', icon: 'mdi-view-dashboard-outline' },
        { title: 'Recruitment', icon: 'mdi-account-tie-outline' },
        { title: 'Onboarding', icon: 'mdi-clipboard-list-outline' },
        { title: 'Recruitment Tasks', icon: 'mdi-pencil-ruler' },
        { title: 'Calendar', icon: 'mdi-calendar-month-outline' },
        { title: 'Settings', icon: 'mdi-cog-outline' },
      ],
      nav: 1,
      menu: [
        { title: 'My Profile' },
        { title: 'Settings' },
      ],
      drawer: false
    }
  },

  beforeCreate() {
    this.$vuetify.theme.dark = false
  },

  watch: {
    nav: function (newVal) {
      if (newVal) {
        console.log('Test Icon', this.testIcon(newVal))
      }
    },
  },

  computed: {
    navIconColor() {
      return '#7d74fd'
    },
    
		width() {
			const screenWidth = this.$vuetify.breakpoint.width;

			if (screenWidth < 600) {
				console.log("Extra Small Screen");
				return "extra-small";
			}
			if (screenWidth > 600 && screenWidth < 960) {
				console.log("Small Screen");
				return "small";
			}
			if (screenWidth > 960 && screenWidth < 1264) {
				console.log("Medium Screen");
				return "medium";
			}
			if (screenWidth > 1264 && screenWidth < 1904) {
				console.log("Large Screen");
				return "large";
			}
			if (screenWidth > 1904) {
				console.log("Extra Large Screen");
				return "extra-large";
			}
		},
	},

  methods: {
    testIcon(navInd) {
      if (navInd === this.nav) {
        return true
      }
      return false
    },

    onClickNavIcon() {
      this.drawer = true
    }
  },
}
</script>

<style scoped>
#app-container {
  background-color: #f5f5fc !important;
}

.t-item {
  border-right-style: solid;
  border-right-color: #5066fd;
}

.brand {
  color: #5066fd !important;
  font-weight: 500;
}

.app-bar-flat {
  padding-top: 0.9rem;
}
</style>