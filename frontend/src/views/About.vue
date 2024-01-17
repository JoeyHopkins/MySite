<template>
  <v-container class="center-content">
    <div>
      <h1 class="center-text text-blue">
        <b>
          Resume
        </b>
      </h1>
      <div class="download-link" @click="openPdfInNewTab">
        <span class="center-content">View PDF</span>
      </div>
    </div>
  </v-container>
  <v-container class="center-content">
    <v-card class="page-card">
      <h2 class="text-blue mx-5 py-3">
        <b>
          Experience
        </b>
      </h2>
      <div style="margin-bottom: -20px;">
        <img 
          src="/src/assets/images/MacTechLogo.png" 
          alt="Macguyvertech Logo" 
          width="200" 
          height="75"
        >
      </div>
      <h4 class="mx-5 lighten-text">
        January 2022 - PRESENT ({{ formattedMonthsSinceEnteredDate(macTechStartDate) }})
      </h4>
      <h3 class="mx-5">
        <b>
          MacGuyverTech, Glenolden, PA (Remote) - 
        </b>
        <i>  
          Lead Full Stack Engineer / Project Manager
        </i>
      </h3>
      <ul class="bullet-points mx-5 pt-5">
        <li class="bullet-list-padding">Integral piece to application development due to depth of knowledge and understanding of client systems</li>
        <li class="bullet-list-padding">100% remote, trusted to work independently primarily using Node/Vue and SQL DBs to build business applications</li>
        <li class="bullet-list-padding">Streamlined long term vision for project in project management role by establishing weekly sprints with client</li>
        <li class="bullet-list-padding">Optimized test in production by leading architecture of production and software upgrades</li>
        <li class="bullet-list-padding">Trusted to take decisive and accurate actions when conflicts arise</li>
        <li class="bullet-list-padding">Forecasted and avoided blockers by organizing the team of developers and managing the project without incentive</li>
        <li class="bullet-list-padding">Managed application upkeep and pushes to testing environments and production servers</li>
        <li class="bullet-list-padding">Took Initiative in managing databases and writing scripts to refresh clients test data daily</li>
        <li class="bullet-list-padding">Relied upon to revise and educate junior developers preventing sub par code from making it to production servers</li>
        <li class="bullet-list-padding">Delegated practical tests for new developers in conjunction with the HR team</li>
        <li class="bullet-list-padding">Led the onboarding and orientation for new developers</li>
        <li class="bullet-list-padding">Worked with a team to scrape data from an API and use it to populate a client's database</li>
        <li class="bullet-list-padding">Responsible for working with 3rd party vendors to ensure application expectations are met</li>
        <li class="bullet-list-padding">Strong understanding of team capabilities, leading to accurate and efficient work assignments</li>
      </ul>


      <div style="margin-bottom: -80px; margin-left: -15px;">
        <img 
          src="/src/assets/images/Staghead.png" 
          alt="Macguyvertech Logo" 
          width="200" 
          height="200"
        >
      </div>
      <h4 class="mx-5 pt-5 lighten-text">
        June 2022 - August 2022 (3 months)
      </h4>
      <h3 class="mx-5">
        <b>
          Staghead Blockchain Services, Colorado (Remote) - 
        </b>
        <i>  
          Full Stack Engineer / Blockchain Engineer
        </i>
      </h3>
      <ul class="bullet-points mx-5 pt-5">
        <li class="bullet-list-padding">Spearheaded the development of an intuitive and visually appealing user interface for a groundbreaking blockchain application.</li>
        <li class="bullet-list-padding">Applied expertise in Solidity to seamlessly integrate and communicate with the Ethereum blockchain, enhancing the app's capabilities and ensuring a robust and secure foundation.</li>
        <li class="bullet-list-padding">Led the creation of a comprehensive web app mockup, providing a compelling and user-friendly demonstration of the blockchain functionalities to potential clients.</li>
        <li class="bullet-list-padding">Demonstrated a keen understanding of both front-end design principles and blockchain technology, resulting in a highly engaging and informative user experience.</li>
      </ul>
    </v-card>
  </v-container>
  <v-container class="center-content">
    <v-card class="page-card">
      <h2 class="text-blue mx-5 py-3">
        Education
      </h2>
      <v-row>
        <div style="margin-top: 15px; margin-left: 35px;">
          <img 
            src="/src/assets/images/DakotaState.png" 
            alt="Macguyvertech Logo" 
            width="100" 
            height="100"
          >
        </div>
        <v-col>
          <h3>
            <b>Dakota State University, South Dakota</b>
          </h3>
          <div>
            <h3>
              <i>  
                Bachelor of Computer Science
              </i>
            </h3>
          </div>
          <h4 class="lighten-text">
            June 2015 - December 2020
          </h4>
          <div class="pb-5">
            <a href="https://dsu.edu/" target="_blank" class="custom-link">https://dsu.edu/</a>
          </div>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
  <v-container>
    <h1 class="center-text text-blue">
      <b>
        Skills
      </b>
    </h1>
    <div class="card-container">
      <v-card v-for="(item, index) in items" :key="index" class="skill-card">
        <v-card-title>{{ item.skill }}</v-card-title>
        <v-card-text>{{ item.length }}</v-card-text>
      </v-card>
    </div>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      pdfPath: 'http://localhost:5173/' + 'src/assets/downloads/Resume.pdf',
      macTechStartDate: '2022-01-01',
      items: [
        { skill: 'Card 1', length: 'Description for Card 1' },
        { skill: 'Card 2', length: 'Description for Card 2' },
        { skill: 'Card 3', length: 'Description for Card 3' }
      ]
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

.lighten-text {
  color: #555;
}

.card-container {
  display: flex;
  flex-direction: row;
  margin-bottom: 10px; 
  flex-wrap: wrap;
  gap: 1em;
  justify-content: center;
  
}

.skill-card {
  background-color: #D1AFF9 !important;
  border-radius: 20px;
}


</style>
