<template>
  <v-container class="center-content">
    <v-card class="page-card">
      <h1 class="center-text text-blue">
        <b>
          Skills
        </b>
      </h1>
      <v-tabs
        bg-color="transparent"
        center-active
        v-model="tab"

      >
        <!-- direction="vertical" -->
        <v-tab value="option-One">One</v-tab>
        <v-tab value="option-Two">Two</v-tab>
        <v-tab value="option-Three">Three</v-tab>
        <v-tab value="option-Four">Four</v-tab>
        <v-tab value="option-Five">Five</v-tab>
        <v-tab value="option-Six">Six</v-tab>
        <v-tab value="option-Seven">Seven</v-tab>
        <v-tab value="option-Eight">Eight</v-tab>
        <v-tab value="option-Nine">Nine</v-tab>
        <v-tab value="option-Ten">Ten</v-tab>
        <v-tab value="option-Eleven">Eleven</v-tab>
        <v-tab value="option-Twelve">Twelve</v-tab>
        <v-tab value="option-Thirteen">Thirteen</v-tab>
        <v-tab value="option-Fourteen">Fourteen</v-tab>
        <v-tab value="option-Fifteen">Fifteen</v-tab>
        <v-tab value="option-Sixteen">Sixteen</v-tab>
        <v-tab value="option-Seventeen">Seventeen</v-tab>
        <v-tab value="option-Eighteen">Eighteen</v-tab>
        <v-tab value="option-Nineteen">Nineteen</v-tab>
        <v-tab value="option-Twenty">Twenty</v-tab>
      </v-tabs>
      <v-window v-model="tab">
        <v-window-item value="option-One">
          <v-card  class="page-card center-text">
            Tab 1
          </v-card>
        </v-window-item>
        <v-window-item value="option-Two">
          <v-card  class="page-card center-text">
            Tab 2
          </v-card>
        </v-window-item>
        <v-window-item value="option-Three">
          <v-card  class="page-card center-text">
            Tab 3
          </v-card>
        </v-window-item>
      </v-window>
    </v-card>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      tab: 'option-One',
      items: [
        { skill: '010 Hex Editor', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Anaconda', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Bash', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Binary Ninja', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Bitbucket', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Bootstrap', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'C', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'C++', length: '2016', image: "/src/assets/images/skills/vite.png" },
        { skill: 'C#', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Calculus', length: '2018', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Computer Graphics', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'CSS3', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'D3.js', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Data Structures', length: '2016', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Discrete Mathmatics', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Expo', length: '2023', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Figma', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Filezilla', length: '2018', image: "/src/assets/images/skills/vite.png" },
        { skill: 'FTP', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'GDB', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Ghidra', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Git', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Handlebars', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'HTML5', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'IDA', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'INetSim', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Javascript', length: '2020', image: "/src/assets/images/skills/JavaScript-logo.png" },
        { skill: 'Java', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Jira', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'JQuery', length: '2023', image: "/src/assets/images/skills/vite.png" },
        { skill: 'JSON', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Linear Algebra', length: '2016', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Linux', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'LISP', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Mailgun', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Maleware Analysis', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'MariaDB', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'MongoDB', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'MS Excel', length: '2010', image: "/src/assets/images/skills/vite.png" },
        { skill: 'MS PowerPoint', length: '2010', image: "/src/assets/images/skills/vite.png" },
        { skill: 'MS Word', length: '2010', image: "/src/assets/images/skills/vite.png" },
        { skill: 'MySQL', length: '2016', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Navicat', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Node JS', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'NoSQL', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Object Oriented Programming', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'ODBC with ProvideX', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'OpenGL', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'PHP', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'PostgreSQL', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Postman', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Powershell', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Prettier', length: '2018', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Probability', length: '2018', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Process Monitor', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Project Management', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Prolog', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Puppeteer', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Python', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'React', length: '2023', image: "/src/assets/images/skills/vite.png" },
        { skill: 'React Native', length: '2023', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Reverse Engineering', length: '2018', image: "/src/assets/images/skills/vite.png" },
        { skill: 'SFTP', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Solidity', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'SQLite', length: '2020', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Sql Server', length: '2016', image: "/src/assets/images/skills/vite.png" },
        { skill: 'SSH', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Statistics', length: '2017', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Sublime', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Suricata', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Typescript', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'VBA', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Virtual Machines', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Visual Studio', length: '2015', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Visual Studio Code', length: '2016', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Vite', length: '2023', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Vue', length: '2022', image: "/src/assets/images/skills/Vue.png" },
        { skill: 'Vuetify', length: '2021', image: "/src/assets/images/skills/vite.png" },
        { skill: 'VueX', length: '2021', image: "/src/assets/images/skills/vite.png" },
        { skill: 'WinDBG', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Windows', length: '2010', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Wireshark', length: '2019', image: "/src/assets/images/skills/vite.png" },
        { skill: 'Wordpress', length: '2022', image: "/src/assets/images/skills/vite.png" },
        { skill: 'x64/x86 Assembly', length: '2018', image: "/src/assets/images/skills/vite.png" },
      
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