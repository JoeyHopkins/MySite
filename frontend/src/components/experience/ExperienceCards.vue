<template>
  <v-row class="center-content spread-elements pt-5">
    <div v-for="(item, index) in cardData" :key="index">
      <v-card class="center-text dynamic-width-card pb-5 flip-in">
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
            {{item.title}} 
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
          <h3 class="lighten-text">
            <i>
              {{ dates }}
            </i>
          </h3>
        </div>
      </v-card>
    </div>
  </v-row>
</template>
<script>
export default {
    props: {
        machtechFormattedDate: String,
    },
    data() {
      return {
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
            }
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
            }
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
            }
          },
        ],
      };
    },
  };
</script>

<style>
.spread-elements {
  display: flex;
  justify-content: space-evenly;
}
</style>