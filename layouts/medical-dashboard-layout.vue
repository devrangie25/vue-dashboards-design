<template>
  <v-app>
    <v-main>
      <v-card class="pa-6" height="100%" flat>
        <v-row>
          <v-col v-if="!['extra-small', 'small', 'medium'].includes(width)" cols="12" lg="1" class="d-flex justify-center">
            <v-card elevation="3" width="80" class="rounded-lg" height="100%">
              <v-navigation-drawer
                floating
                permanent
                mini-variant
                mini-variant-width="80"
                class="px-2"
                height="100%"
                color="#4363d1"
                dark
              >
                <v-list>
                  <v-list-item three-line class="mb-16">
                    <v-list-item-avatar>
                      <v-img
                        src="https://cdn.vuetifyjs.com/images/john.png"
                      ></v-img>
                    </v-list-item-avatar>
                  </v-list-item>

                  <v-list-item v-for="(item, i) in items" :key="i">
                    <v-list-item-icon>
                      <v-btn icon class="rounded-lg">
                        <v-icon size="25">{{ item.icon }}</v-icon>
                      </v-btn>
                    </v-list-item-icon>

                    <v-list-item-content />
                  </v-list-item>
                </v-list>

                <template v-slot:append>
                  <v-list>
                    <v-list-item class="mt-16">
                      <v-list-item-icon>
                        <v-btn icon class="rounded-lg">
                          <v-icon size="25">mdi-logout</v-icon>
                        </v-btn>
                      </v-list-item-icon>
                      <v-list-item-content />
                    </v-list-item>
                  </v-list>
                </template>
              </v-navigation-drawer>
            </v-card>
          </v-col>
          <v-col cols="12" lg="11">
            <v-container fluid class="pa-0">
              <Nuxt />
            </v-container>
          </v-col>
        </v-row>
      </v-card>
    </v-main>
  </v-app>
</template>

<script>
export default {

  data() {
    return {
      items: [
        { title: 'Home', icon: 'mdi-home' },
        { title: 'Sales', icon: 'mdi-chart-box' },
        { title: 'Calendar', icon: 'mdi-calendar-month' },
        { title: '3', icon: 'mdi-account-multiple' },
        { title: '4', icon: 'mdi-information' },
        { title: 'Settings', icon: 'mdi-cog' },
      ],
    }
  },

  beforeCreate(){
    this.$vuetify.theme.dark = true
  },

  computed: {
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
}
</script>
