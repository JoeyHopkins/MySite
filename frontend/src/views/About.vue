<template>
  <v-container class="center-content fade-in">
    <div>
      <h1 class="center-text text-blue">
        <b>
          Interactive Resume
        </b>
      </h1>
      <div class="download-link" @click="openPdfInNewTab">
        <span class="center-content">View PDF</span>
      </div>
    </div>
  </v-container>
  <ExperienceCards :machtechFormattedDate="formattedMonthsSinceEnteredDate(macTechStartDate)"/>
<!-- <component :is="skills"/> -->
</template>
<script>
import Skills from '../components/experience/Skills.vue'
import ExperienceCards from '../components/experience/ExperienceCards.vue'
export default {
  components: {
    ExperienceCards,
  },
  data() {
    return {
      pdfPath: 'http://localhost:5173/' + 'src/assets/downloads/Resume.pdf',
      macTechStartDate: '2022-02-01',
      skills: Skills,
      experienceCards: ExperienceCards,
    };
  },
  methods: {
    openPdfInNewTab() {
      window.open(this.pdfPath, '_blank');
    },
    formattedMonthsSinceEnteredDate(enteredDate) {
      const monthsSinceEnteredDate = (new Date() - new Date(enteredDate)) / (30.44 * 24 * 60 * 60 * 1000);
      
      const years = Math.floor(monthsSinceEnteredDate / 12);
      const months = Math.floor(monthsSinceEnteredDate) % 12;

      const yearString = years > 0 ? `${years} ${years === 1 ? 'year' : 'years'}` : '';
      const monthString = months > 0 ? `${months} ${months === 1 ? 'month' : 'months'}` : '';

      return yearString && monthString ? `${yearString}, ${monthString}` : yearString || monthString || '0 months';
    },
  },
};
</script>
<style scoped>

.download-link {
  cursor: pointer;
  color: pink;
}

.download-link span:hover {
  color: green;
}

.bullet-points {
  list-style-type: disc;
  padding-left: 20px;
  padding-bottom: 20px;
}

@media only screen and (max-width: 600px) {
  .bullet-points li {
    text-indent: 20px;
  }
}

.bullet-list-padding {
  padding-bottom: 5px;
}

.card-container {
  display: flex;
  flex-direction: row;
  margin-bottom: 10px; 
  flex-wrap: wrap;
  gap: 1em;
  justify-content: center;
  
}
</style>