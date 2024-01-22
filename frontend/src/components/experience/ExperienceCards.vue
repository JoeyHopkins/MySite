<template>
  <v-row class="center-content spread-elements pt-5">
    <div v-for="(item, index) in cardData" :key="index">
      <v-card class="center-text dynamic-width-card flip-in" style="display: flex; flex-direction: column;">
        <div class="center-content" :style="item.image.style">
          <v-img
            :src="item.image.src"
            :alt="item.image.alt"
            :width="item.image.width"
            :height="item.image.height"
          />
        </div>
        <h3>
          <b>
            {{ item.title }}
          </b>
        </h3>
        <div v-for="(position, positionIndex) in item.positions" :key="positionIndex">
          <h3>
            <i>
              {{ position }}
            </i>
          </h3>
        </div>
        <div v-for="(dates, datesIndex) in item.dates" :key="datesIndex">
          <h3 class="lighten-text" :class="item.bottomClass">
            <i>
              {{ dates }}
            </i>
          </h3>
        </div>
        <div class="details-container center-content">
          <div class="details">
            <v-btn
              variant="plain"
              @click="toggleExpand(item)"
              >
              <v-icon
                size="large"
                color="green-darken-2"
                icon="mdi-view-list"
              ></v-icon>
              <v-tooltip
                activator="parent"
                location="bottom"
              >
                Open Details
              </v-tooltip>
            </v-btn>
          </div>
        </div>
      </v-card>
    </div>
  </v-row>
  <div v-for="(item, index) in cardData" :key="index">
    <v-expand-transition>
      <v-card
        v-show="cardData[index].expand"
        height="100"
        width="90%"
        class="mt-5 mx-auto page-card"
      >
        {{item.title}}
      </v-card>
    </v-expand-transition>
  </div>
</template>
<script>
export default {
    props: {
        machtechFormattedDate: String,
    },
    data() {
      return {
        expandedCards: [],
        cardData: [
          { 
            title: 'Macguyvertech', 
            positions: ['Lead Full Stack Engineer', 'Project Manager'],
            dates: ['Jan. 2022 - PRESENT', '(' + this.machtechFormattedDate + ')'],
            image: {
              src: '/src/assets/images/MacTechLogo.png',
              alt: 'Macguyvertech.logo',
              height: '170px',
              style: "margin-bottom: -10px; padding-top: 10px"
            },
            bottomClass:"",
            expand: false,
          },
          { 
            title: 'Dakota State University', 
            positions: ['Bachelor of Computer Science'],
            dates: ['June 2015 - Dec. 2020'],
            image: {
              src: '/src/assets/images/DakotaState.png',
              alt: 'Dakota State Logo',
              height: '120px',
              style: "padding-top: 25px; padding-bottom: 25px"
            },
            bottomClass:"mb-14",
            expand: false,
          },
          { 
            title: 'Staghead Blockchain Services', 
            positions: ['Full Stack Engineer', 'Blockchain Engineer'],
            dates: ['June 2022 - Aug. 2022', '(3 months)'],
            image: {
              src: '/src/assets/images/Staghead.png',
              alt: 'Staghead Logo',
              height: '225px',
              style: "margin-bottom: -60px; padding-top: 5px"
            },
            bottomClass:"",
            expand: false,
          },
        ],
        cardDetails: [
          {
            title: 'Macguyvertech Details',
          },
          {
            title: 'Dakota State Details',
          },
          {
            title: 'Staghead Details',
          },
        ],
      };
    },
    methods: {
      toggleExpand(item) {
        if(item.expand == false)
          for(let card of this.cardData)
            card.expand = false

        item.expand = !item.expand;
      },
    },
  };
</script>
<style>
.details-container {
  flex-grow: 1;
  display: flex;
  flex-direction: row;
}

.details {
  align-self: flex-end;  
  margin-bottom: 10px; /* Adjust the margin as needed */
}
</style>