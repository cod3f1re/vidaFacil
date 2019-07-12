<template>
  <v-app id="app">
    <v-layout>
      <v-flex>
        <v-sheet height="500">
          <v-calendar :now="today" :value="today" color="primary">
            <template v-slot:day="{ date }">
              <template v-for="event in eventsMap[date]">
                <v-menu :key="event.title" v-model="event.open" full-width offset-x>
                  <template v-slot:activator="{ on }">
                    <div
                      v-if="!event.time"
                      v-ripple
                      class="my-event"
                      v-on="on"
                      v-html="event.title"
                    ></div>
                  </template>
                  <v-card color="grey lighten-4" flat
                  min-width="50px">
                    <v-toolbar color="primary" dark>
                      <v-toolbar-title v-html="event.title"></v-toolbar-title>
                      <v-spacer></v-spacer>
                      <v-btn icon>
                        <v-icon>edit</v-icon>
                      </v-btn>
                    </v-toolbar>

                    <v-img
                      :src="`https://cocina-casera.com/wp-content/uploads/2016/11/hamburguesa-queso-receta.jpg`"
                      :lazy-src="`https://cocina-casera.com/wp-content/uploads/2016/11/hamburguesa-queso-receta.jpg`"
                      aspect-ratio="1"
                      class="grey lighten-2 imagen"
                    ></v-img>
                    <v-card-title primary-title>
                      <v-card-text>
                        <p class="text-md-center">
                          Precio<p class="precio">
                              $<span v-html="event.details">
                              </span>
                        </p>
                      </v-card-text>
                    </v-card-title>

                    <v-toolbar>
                      <v-flex xs6>
                        <v-card-actions>
                          <v-btn flat color="secondary">Cancelar</v-btn>
                        </v-card-actions>
                      </v-flex>
                      <v-flex xs6>
                        <v-card-actions>
                          <v-btn color="primary">Ver receta</v-btn>
                        </v-card-actions>
                      </v-flex>
                    </v-toolbar>
                  </v-card>
                </v-menu>
              </template>
            </template>
          </v-calendar>
        </v-sheet>
      </v-flex>
    </v-layout>
  </v-app>
</template>

<style lang="stylus" scoped>
.my-event {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  border-radius: 2px;
  background-color: #1867c0;
  color: #ffffff;
  border: 1px solid #1867c0;
  width: 100%;
  font-size: 12px;
  padding: 3px;
  cursor: pointer;
  margin-bottom: 1px;
}

p {
  margin-bottom: unset;
}

.precio {
  font-size: 20px;
  font-weight: bold;
}

.v-card__text {
  padding-top: 0px;
  padding-bottom: 0px;
}

.imagen {
  width: 100%;
}

@media only screen and (max-width: 600px) {
  .v-card {
    width: 200px;
  }
  .v-card__actions {
    padding: 0px;
  }
  .v-btn{
  font-size: 10px;
  }
  .v-toolbar__content{
    padding-left: 0px;
  }
  .v-toolbar__title {
      font-size: 15px;
  }
}
</style>
<script>
export default {
  data: () => ({
    today: '2019-01-08',
    events: [
      {
        title: 'Vacation',
        details: 'Going to the beach!',
        date: '2018-12-30',
        open: false
      },
      {
        title: 'Vacation',
        details: 'Going to the beach!',
        date: '2018-12-31',
        open: false
      },
      {
        title: 'Vacation',
        details: 'Going to the beach!',
        date: '2019-01-01',
        open: false
      },
      {
        title: 'Meeting',
        details: 'Spending time on how we do not have enough time',
        date: '2019-01-07',
        open: false
      },
      {
        title: '30th Birthday',
        details: 'Celebrate responsibly',
        date: '2019-01-03',
        open: false
      },
      {
        title: 'Hamburguesas',
        details: '120',
        date: '2019-01-01',
        open: false
      },
      {
        title: 'Conference',
        details: 'Mute myself the whole time and wonder why I am on this call',
        date: '2019-01-21',
        open: false
      },
      {
        title: 'Hackathon',
        details: 'Code like there is no tommorrow',
        date: '2019-02-01',
        open: false
      }
    ]
  }),
  computed: {
    // convert the list of events into a map of lists keyed by date
    eventsMap() {
      const map = {};
      this.events.forEach(e => (map[e.date] = map[e.date] || []).push(e));
      return map;
    }
  },
  methods: {
    open(event) {
      alert(event.title);
    }
  }
};
</script>
