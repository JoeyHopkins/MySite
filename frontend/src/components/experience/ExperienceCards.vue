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
                :color="item.expand == false ? 'green-darken-2' : 'red-darken-2'"
                :icon="item.expand == false ? 'mdi-view-list' : 'mdi-close'"
              ></v-icon>
              <v-tooltip
                activator="parent"
                location="bottom"
              >
                {{item.expand == false ? 'Open Details' : 'Close Details'}}
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
        width="90%"
        class="mt-10 mx-auto page-card"
      >
      <div class="center-content" :style="item.image.style">
          <v-img
            :src="item.image.src"
            :alt="item.image.alt"
            :width="item.image.width"
            :height="item.image.height"
          />
        </div>
        <h1 class="center-content mt-5">
          <b>
            {{item.title}}
          </b>
        </h1>
        <h2 class="center-content">
          <b>
            {{item.location}}
          </b>
        </h2>
        <h2 class="center-content">
          <i>
            {{item.positions.join(' / ')}}
          </i>
        </h2>
        <h2 class="center-content lighten-text">
            {{item.dates.join(' ')}}
        </h2>
        <ul class="bullet-points mx-15 py-5">
          <li v-for="(bullet, bulletsIndex) in item.bullets" :key="bulletsIndex">
            {{ bullet }}
          </li>
        </ul>
        <h2 class="center-content pt-5">
          <b>
            Tech Stack
          </b>
        </h2>
        <v-divider
          :thickness="5"
          class="border-opacity-75 mx-10"
          color="purple"
        >
        </v-divider>
        <v-row class="mx-10 my-5 spread center-text">
          <v-card v-for="(skill, skillIndex) in item.techStack" :key="skillIndex" class="skill-card mt-5">
            <v-row class="my-3 mx-5">
                <div class="circle-img-container  mr-3">
                  <img 
                    :src="skill.image"
                    alt="Macguyvertech Logo" 
                    class="circle-img"
                    :class="item.class"
                  />
                </div>
              <v-col>
                <h3>
                  <b>
                    {{ skill.name }}
                  </b>
                </h3>
              </v-col>
            </v-row>
          </v-card>
        </v-row>
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
            location: 'Glenolden, PA (Remote)',
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
            bullets: [
              "Integral piece to application development due to depth of knowledge and understanding of client systems",
              "100% remote, trusted to work independently primarily using Node/Vue and SQL DBs to build business applications",
              "Streamlined long term vision for project in project management role by establishing weekly sprints with client",
              "Optimized test in production by leading architecture of production and software upgrades",
              "Trusted to take decisive and accurate actions when conflicts arise",
              "Forecasted and avoided blockers by organizing the team of developers and managing the project without incentive",
              "Managed application upkeep and pushes to testing environments and production servers",
              "Took Initiative in managing databases and writing scripts to refresh clients test data daily",
              "Relied upon to revise and educate junior developers preventing sub par code from making it to production servers",
              "Delegated practical tests for new developers in conjunction with the HR team",
              "Led the onboarding and orientation for new developers",
              "Worked with a team to scrape data from an API and use it to populate a client's database",
              "Responsible for working with 3rd party vendors to ensure application expectations are met",
              "Strong understanding of team capabilities, leading to accurate and efficient work assignments",
            ],
            techStack: [
              { name: 'Javascript', image: '/src/assets/images/skills/vite.png' },
              { name: 'HTML', image: '/src/assets/images/skills/vite.png' },
              { name: 'CSS', image: '/src/assets/images/skills/vite.png' },
              { name: 'Node.js', image: '/src/assets/images/skills/vite.png' },
              { name: 'Vue', image: '/src/assets/images/skills/vite.png' },
              { name: 'PHP', image: '/src/assets/images/skills/vite.png' },
              { name: 'Wordpress', image: '/src/assets/images/skills/vite.png' },
              { name: 'Powershell', image: '/src/assets/images/skills/vite.png' },
              { name: 'SQL Server', image: '/src/assets/images/skills/vite.png' },
              { name: 'MYSQL', image: '/src/assets/images/skills/vite.png' },
              { name: 'ODBC with ProvideX', image: '/src/assets/images/skills/vite.png' },
              { name: 'VBA', image: '/src/assets/images/skills/vite.png' },
            ],
          },
          { 
            title: 'Dakota State University', 
            location: 'Madison, South Dakota (Remote)',
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
            bullets: [
              "Dakota State details",
            ],
            techStack: [
              { name: 'C', image: '/src/assets/images/skills/vite.png' },
              { name: 'C++', image: '/src/assets/images/skills/vite.png' },
              { name: 'C#', image: '/src/assets/images/skills/vite.png' },
              { name: 'Java', image: '/src/assets/images/skills/vite.png' },
              { name: 'Python', image: '/src/assets/images/skills/vite.png' },
              { name: 'Bash', image: '/src/assets/images/skills/vite.png' },
              { name: 'x86/x64 Assembly', image: '/src/assets/images/skills/vite.png' },
              { name: 'MySQL', image: '/src/assets/images/skills/vite.png' },
              { name: 'Prolog', image: '/src/assets/images/skills/vite.png' },
              { name: 'LISP', image: '/src/assets/images/skills/vite.png' },
            ],
          },
          { 
            title: 'Staghead Blockchain Services', 
            location: 'Colorado (Remote)',
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
            bullets: [
              "Spearheaded the development of an intuitive and visually appealing user interface for a groundbreaking blockchain application.",
              "Applied expertise in Solidity to seamlessly integrate and communicate with the Ethereum blockchain, enhancing the app's capabilities and ensuring a robust and secure foundation.",
              "Led the creation of a comprehensive web app mockup, providing a compelling and user-friendly demonstration of the blockchain functionalities to potential clients.",
              "Demonstrated a keen understanding of both front-end design principles and blockchain technology, resulting in a highly engaging and informative user experience.",
            ],
            techStack: [
              { name: 'Vue', image: '/src/assets/images/skills/vite.png' },
              { name: 'Javascript', image: '/src/assets/images/skills/vite.png' },
              { name: 'HTML', image: '/src/assets/images/skills/vite.png' },
              { name: 'CSS', image: '/src/assets/images/skills/vite.png' },
              { name: 'Solidity', image: '/src/assets/images/skills/vite.png' },
            ],
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
  margin-bottom: 10px;
}

.skill-card {
  background-color: lightpink !important;
  border-radius: 20px !important;
  /* width: 250px; */
}

.circle-img-container {
  width: 50px;
  height: 50px;
  overflow: hidden;
  border-radius: 50%;
}

.circle-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

</style>