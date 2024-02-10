<template>
  <v-row class="center-content spread-elements pt-5">
    <div v-for="(item, index) in cardData" :key="index">
      <v-card class="center-text dynamic-width-card flip-in" style="display: flex; flex-direction: column;">
        <div class="center-content" :style="item.image.style">
          <v-img :src="item.image.src" :alt="item.image.alt" :width="item.image.width" :height="item.image.height" />
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
            <v-btn variant="plain" @click="toggleExpand(item)">
              <v-icon size="large" :color="item.expand == false ? 'green-darken-2' : 'red-darken-2'"
                :icon="item.expand == false ? 'mdi-view-list' : 'mdi-close'"></v-icon>
              <v-tooltip activator="parent" location="bottom">
                {{ item.expand == false ? 'Open Details' : 'Close Details' }}
              </v-tooltip>
            </v-btn>
          </div>
        </div>
      </v-card>
    </div>
  </v-row>





  <div v-for="(item, index) in cardData" :key="index">
    <v-expand-transition>
      <v-card v-show="cardData[index].expand" width="90%" class="mt-10 mx-auto page-card">
        <div class="center-content" :style="item.image.style">
          <v-img :src="item.image.src" :alt="item.image.alt" :width="item.image.width" :height="item.image.height" />
        </div>
        <h1 class="center-content mt-5">
          <b>
            {{ item.title }}
          </b>
        </h1>
        <h2 class="center-content">
          <b>
            {{ item.location }}
          </b>
        </h2>
        <h2 class="center-content">
          <i>
            {{ item.positions.join(' / ') }}
          </i>
        </h2>
        <h2 class="center-content lighten-text">
          {{ item.dates.join(' ') }}
        </h2>

        <div v-if="item.type == 'Work'">
          <ul class="bullet-points mx-15 py-5">
            <li v-for="(bullet, bulletsIndex) in item.bullets" :key="bulletsIndex">
              {{ bullet }}
            </li>
          </ul>
          <v-card class="mx-10 mb-10">
            <v-expansion-panels multiple variant="accordion" style="background-color:darkorchid">
              <v-expansion-panel v-for="(item, index) in item.expandableData" :key="index"
                style="background-color: blueviolet;">
                <v-expansion-panel-title v-slot="{ open }" style="display: flex; justify-content: center; color: white;">
                  <v-row class="center-content">
                    {{ item.sectionName }}
                  </v-row>
                </v-expansion-panel-title>

                <v-expansion-panel-text>
                  <v-row class="mx-1 my-1">
                    <v-card v-for="(dataItem, dataIndex) in item.items" :key="dataIndex"
                      class="skill-card mt-3 mx-2 center-text px-5 py-2">
                      {{ dataItem.name }}
                    </v-card>
                  </v-row>
                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>
          </v-card>
        </div>


        <div v-if="item.type == 'Education'">
          <h1 class="center-text mt-5">
            <b>
              Computer Science Classes
            </b>
          </h1>
          <v-divider :thickness="5" class="border-opacity-75 mx-10 mb-3" color="purple">
          </v-divider>

          <v-card class="mx-10 mb-10">
            <v-expansion-panels multiple variant="accordion" style="background-color:darkorchid">
              <v-expansion-panel v-for="(item, index) in item.expandableData" :key="index"
                style="background-color: blueviolet;">
                <v-expansion-panel-title v-slot="{ open }" style="display: flex; justify-content: center; color: white;">
                  <v-row class="center-content">
                    {{ item.className }}
                  </v-row>
                </v-expansion-panel-title>

                <v-expansion-panel-text>
                  <v-row class="mx-1 my-1">
                    <v-card v-for="(dataItem, dataIndex) in item.items" :key="dataIndex"
                      class="skill-card mt-3 mx-2 center-text px-5 py-2">
                      {{ dataItem.name }}
                    </v-card>
                  </v-row>
                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>
          </v-card>

        </div>
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
          type: 'Work',
          location: 'Glenolden, PA (Remote)',
          positions: ['Lead Full Stack Engineer', 'Project Manager'],
          dates: ['Jan. 2022 - PRESENT', '(' + this.machtechFormattedDate + ')'],
          image: {
            src: '/src/assets/images/MacTechLogo.png',
            alt: 'Macguyvertech.logo',
            height: '170px',
            style: "margin-bottom: -10px; padding-top: 10px"
          },
          bottomClass: "",
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
          expandableData: [
            {
              sectionName: "Tech Stack",
              items: [
                { name: 'Javascript' },
                { name: 'Node.js' },
                { name: 'Vuetify' },
                { name: 'Bootstrap' },
                { name: 'HTML' },
                { name: 'CSS' },
                { name: 'Vue' },
                { name: 'PHP' },
                { name: 'Wordpress' },
                { name: 'Powershell' },
                { name: 'SQL Server' },
                { name: 'MYSQL' },
                { name: 'ODBC with ProvideX' },
                { name: 'VBA' },
              ]
            },
            {
              sectionName: "Skills Developed",
              items: [
                { name: 'Git' },
                { name: 'FTP' },
                { name: 'SFTP' },
                { name: 'SSH' },
                { name: 'Project Management' },
                { name: 'Jira' },
                { name: 'Client Communication' },
              ]
            }
          ],
        },
        {
          title: 'Dakota State University',
          type: 'Education',
          location: 'Madison, South Dakota (Remote)',
          positions: ['Bachelor of Computer Science'],
          dates: ['June 2015 - Dec. 2020'],
          image: {
            src: '/src/assets/images/DakotaState.png',
            alt: 'Dakota State Logo',
            height: '120px',
            style: "padding-top: 25px; padding-bottom: 25px"
          },
          bottomClass: "mb-14",
          expand: false,

          expandableData: [
            { className: "Artificial Intelligence", },
            { className: 'Reverse Engineering' },
            { className: 'Assembly' },
            { className: 'Object Oriented Design' },
            { className: 'Artificial Intelligence' },
            { className: 'Operating Systems' },
            { className: 'Paralell Computing' },
            { className: 'Malware Analysis' },
          ],
          techStack: [
            { name: 'C' },
            { name: 'C++' },
            { name: 'C#' },
            { name: 'Java' },
            { name: 'Python' },
            { name: 'Bash' },
            { name: 'x86/x64 Assembly' },
            { name: 'MySQL' },
            { name: 'Prolog' },
            { name: 'LISP' },
          ],
          seniorClasses: [
            {
              name: 'Malware Analysis',
              experience: [
                { name: 'General Debugger (GDB)' },
                { name: 'IDA' },
                { name: 'WinDBG' },
                { name: 'Wireshark' },
                { name: 'Binary Ninja' },
                { name: 'Ghidra' },
                { name: '010 Hex Editor' },
                { name: 'INetSim' },
                { name: 'Suricata' },
                { name: 'Process Monitor' },
                { name: 'Virtual Machines' },
                { name: 'x86/x64 Assembly' },
              ],
            },
            { name: 'Reverse Engineering' },
            { name: 'Assembly' },
            { name: 'Object Oriented Design' },
            { name: 'Artificial Intelligence' },
            { name: 'Jira' },
            { name: 'Operating Systems' },
            { name: 'Paralell Computing' },
          ]
        },
        {
          title: 'Staghead Blockchain Services',
          type: 'Work',
          location: 'Colorado (Remote)',
          positions: ['Full Stack Engineer', 'Blockchain Engineer'],
          dates: ['June 2022 - Aug. 2022', '(3 months)'],
          image: {
            src: '/src/assets/images/Staghead.png',
            alt: 'Staghead Logo',
            height: '225px',
            style: "margin-bottom: -60px; padding-top: 5px"
          },
          bottomClass: "",
          expand: false,
          bullets: [
            "Spearheaded the development of an intuitive and visually appealing user interface for a groundbreaking blockchain application.",
            "Applied expertise in Solidity to seamlessly integrate and communicate with the Ethereum blockchain, enhancing the app's capabilities and ensuring a robust and secure foundation.",
            "Led the creation of a comprehensive web app mockup, providing a compelling and user-friendly demonstration of the blockchain functionalities to potential clients.",
            "Demonstrated a keen understanding of both front-end design principles and blockchain technology, resulting in a highly engaging and informative user experience.",
          ],
          expandableData: [
            {
              sectionName: "Tech Stack",
              items: [
                { name: 'Vue' },
                { name: 'Javascript' },
                { name: 'CSS' },
                { name: 'Node.js' },
                { name: 'HTML' },
                { name: 'Solidity' },
              ]
            },
          ],
        },
      ],
    };
  },
  methods: {
    toggleExpand(item) {
      if (item.expand == false)
        for (let card of this.cardData)
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