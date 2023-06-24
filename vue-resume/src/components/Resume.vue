<template>
  <div class="my-div bg-grey-1 q-pa-md">
      <div class="row justify-between q-mx-sm text-h4 text-primary">
        <div class="text-bold">{{ name }}</div>
        <div v-if="designation" class="q-ml-lg text-h6 flex items-end text-secondary">
          Full Stack Software Developer, 
          {{ designation }}
        </div>
      </div>
      <q-separator horizontal color="primary" style="height: 3px" />
      <div class="row justify-center q-gutter-xs q-mt-md">
        <ContactCard link="https://www.google.com/maps/place/Montgomery,+Calgary,+AB/@51.0643662,-114.1828838,12.93z/data=!4m6!3m5!1s0x53716ef989772efd:0xd9c32fe94b8d9f74!8m2!3d51.074714!4d-114.1641658!16zL20vMGg0dGM1?entry=ttu" title="Address" text="Calgary AB, T3B 0Z8" icon="pin_drop"/>
        <ContactCard link="mailto:crookes.garnet@gmail.com" title="Email" text="crookes.garnet@gmail.com" icon="alternate_email"/>
        <ContactCard link="tel:+15872190406" title="Phone" text="(587) 219-0406" icon="phone_in_talk"/>
        <ContactCard link="https://github.com/gcrookes" title="GitHub" text="@gcrookes">
          <img :src="githubIcon" alt="Github Link" class="centered-image" style="width: 2.5rem"/>
        </ContactCard>
      </div>
      <SectionCard title="Technical & Professional Skills" icon="construction">
        <div class="q-mt-sm q-px-md text-italic justify-between row">
          <q-badge v-for="skill in skills" class="q-ma-xs q-py-xs text-body" style="font-size: 15px" size="lg" :color="colors[skill.type] ?? 'primary'" rounded :key="skill"><q-icon name="add" />{{ skill.name }}</q-badge>
        </div>
      </SectionCard>
      <SectionCard title="Education" icon="school">
          <div class="q-mx-md q-mt-sm text-secondary">
            <div class="row justify-between">
              <div class="text-weight-bold">University of Calgary, M.Eng Software Engineering</div>
              <div>April 2023</div>
            </div>
            <div class="row justify-between" style="font-size: 12px;">
              <div class="text-italic q-ml-sm">Cumulative GPA</div>
              <div>4.0 of 4.0</div>
            </div>
            <div class="row justify-between q-mt-xs">
              <div class="text-weight-bold">University of Alberta, BSc. Mechanical Engineering, Coop with Distinction</div>
              <div>April 2019</div>
            </div>
            <div class="row justify-between" style="font-size: 12px;">
              <div class="text-italic q-ml-sm">Cumulative GPA</div>
              <div>3.7 of 4.0</div>
            </div>
          </div>
      </SectionCard>
      <SectionCard title="Work Experience" icon="precision_manufacturing">
        <q-card v-for="exp in experiences" class="q-mx-md q-mt-sm" :key="exp">
          <div class="q-mx-sm">
            <div class="q-my-none row justify-between">
              <div class="row text-bold">
                {{ exp.name }}
              </div>
              <div class="text-secondary">
                {{ exp.time }}
              </div>
            </div>
            <div class="q-my-none row justify-between align-center">
              <div class="row text-bold">
                {{ exp.position }}
              </div>
              <div class="text-secondary">
                {{ exp.location }}
              </div>
            </div>
          </div>
          <q-separator color="primary" />
          <div v-if="exp.technology.length > 0" class="q-pt-xs text-secondary text-italic text-weight-bold">
            Utilized: 
            <q-badge v-for="skill in exp.technology" class="q-ma-xs" :color="colors[skill.type] ?? 'primary'" rounded :key="skill">{{ skill.name }}</q-badge>
          </div>
          <table class="text-secondary q-pt-xs">
            <li v-for="line in exp.description" class="q-ml-md" :key="line">{{ line }}</li>
          </table>
        </q-card>
      </SectionCard>
        <div class="page-break" />
      <SectionCard title="Software Projects" icon="architecture">
          <q-card v-for="project in projects" class="q-mx-md q-mt-sm" :key="project">
            <div class="q-my-none row text-h6 text-bold justify-between align-center">
              {{ project.name }}
              <div class="text-xs row">
                <a v-if="project.github" :href="project.github" class="link-wrapper" target="_blank" >
                  <img :src="githubIcon" alt="Github Link" class="centered-image" style="width: 1.5rem"/>
                </a>
              </div>
            </div>
            <q-separator color="primary" />
            <div class="q-pt-xs text-secondary text-italic text-weight-bold">
              Utilized: 
              <q-badge v-for="skill in project.technology" class="q-ma-xs" :color="colors[skill.type] ?? 'primary'" rounded :key="skill">{{ skill.name }}</q-badge>
            </div>
            <table class="text-secondary">
              <li v-for="line in project.description" class="q-ml-md" :key="line">{{ line }}</li>
            </table>
          </q-card>
      </SectionCard>
  </div>
</template>

<script lang="ts">
  import { defineComponent, ref } from 'vue'
  import SectionCard from './SectionCard.vue'
  import githubIcon from '../assets/github.svg'
  import ContactCard from './ContactCard.vue'

  export default defineComponent({
    props: {
      name: {type: String, required: true},
      designation: { type: String, default: '' }
    },
    components: {
      SectionCard,
      ContactCard
    },
    setup() {
      const count = ref(0)
      const colors = {
        concept: 'deep-orange-7',
        database: 'blue-grey-8',
        framework: 'red-8',
        hardware: 'green-10',
        language: 'indigo-7',
        platform: 'teal-7',
        tool: 'grey-10',
      }
      const skills = [
        {name: 'TypeScript', type: 'language'},
        {name: 'C#', type: 'language'},
        {name: 'HTML/CSS', type: 'language'},
        {name: 'Python', type: 'language'},
        {name: 'Java', type: 'language'},
        {name: 'C++', type: 'language'},
        {name: 'VueJS', type: 'framework'},
        {name: 'ASP.NET Core', type: 'framework'},
        {name: 'React', type: 'framework'},
        {name: 'Spring Boot', type: 'framework'},
        {name: 'Unity', type: 'framework'},
        {name: 'Microsoft Azure', type: 'platform'},
        {name: 'CosmosDB', type: 'database'},
        {name: 'MySQL', type: 'database'},
        {name: 'PostgreSQL', type: 'database'},
        {name: `REST API's`, type: 'concept'},
        {name: 'NoSQL Databases', type: 'concept'},
        {name: 'Relational Databases', type: 'concept'},
        {name: 'Serverless', type: 'concept'},
        {name: 'Machine Learning', type: 'concept'},
      ]
      const projects = [
        {
          name: 'Movie Theater Ticket Website',
          technology: [{name: 'Javascript', type:'language'},  {name: 'Java', type:'language'}, {name: 'React', type:'framework'}, {name: 'Spring Boot', type:'framework'}, {name: 'MySQL', type:'database'}, {name: 'JPA', type:'library'}, {name: 'REST API', type:'concept'}],
          description: [
            'Created a website where users can find and purchase tickets for a movie theater',
            'Frontend implemented using React, users can login or use the site as a guest',
            'Backend implemented in Spring Boot, with data stored on a MySQL database',
          ],
          github: "https://github.com/ChengDave/ticket-reservation-system",
        },
        {
          name: 'EOG Mouse Control - NatHacks Hackathon',
          technology: [{name: 'Python', type: 'language'}, {name: 'Tensorflow', type: 'library'}, {name: 'Arduino', type: 'hardware'}, {name: 'EXG Pills', type: 'hardware'}, {name: 'Multithreading', type: 'concept'}, {name: 'Serial Communication', type: 'concept'}],
          description: [
            'Created a Brain Computer Interface to control a computer mouse from EOG Data',
            'Captured and filtered data from multiple EXG Pill sensors on an Arduino',
            'Used serial communication to transmit data between Arduino and computer',
            'Ran a multithreaded script to analyze data and control a computer mouse',
          ],
          github: "https://github.com/gcrookes/EOGMouseControl",
        },
        {
          name: 'Decline Analysis Application',
          technology: [{name: 'Python', type: 'language'}, {name: 'PyQt5', type: 'library'}, {name: 'MatPlotLib', type: 'library'}, {name: 'Numpy', type: 'library'}, {name: 'Pandas', type: 'library'}, {name: 'Pickle', type: 'library'}],
          description: [
            'Windows application to improve efficiency of decline analysis of oil & gas wells',
            'GUI allows user to interact with data and select points to fit a curve to',
            'Implemented system to create and load save files using Pickle',
            'Imports/Exports CSV files allowing collaboration with other programs',
          ],
          github: "https://github.com/gcrookes/DeclineAnalysis",
        },
        {
          name: 'Course Registration Website',
          technology: [{name: 'Java', type: 'language'}, {name: 'Javascript', type: 'language'}, {name: 'HTML', type: 'language'}, {name: 'CSS', type: 'language'}, {name: 'Spring Boot', type: 'framework'}, {name: 'MySQL', type: 'database'}, {name: 'JPA', type: 'library'}, {name: 'REST API', type: 'concept'}],
          description: [
            'Created a website which students could use to login, enroll in, or drop courses',
            'Frontend implemented with HTML/CSS/Javascript, served on the backend',
            'Backend implemented in Spring Boot, with data stored on a MySQL database',
            'Communcation was done between client and server using a REST API',
          ],
          github: "https://github.com/dpwalz/ENSF607-608"
        }
      ]
      const experiences = [
        {
          name: 'Child Friendly Care',
          position: 'Full Stack Software Developer',
          location: 'Calgary, AB',
          time: 'Feb. 2023 to Present',
          technology: [
            {name: 'TypeScript', type: 'language'},
            {name: 'C#', type: 'language'},
            {name: 'HTML/CSS', type: 'language'},
            {name: 'VueJS', type: 'framework'},
            {name: 'ASP.NET Core', type: 'framework'},
            {name: 'Microsoft Azure', type: 'platform'},
            {name: 'CosmosDB', type: 'database'},
            {name: 'Serverless', type: 'concept'},
          ],
          description: [
            'Developed a web application to integrate all functionality required to operate a daycare in a single site',
            'Built frontend site as a Single Page Application in VueJS using the Quasar framework for UI components',
            'Created RESTful API using the ASP.NET Core framework deployed on serverless Azure Functions',
            'Utilized Microsoft Azure Cosmos NoSQL database for data storage and logging production failures',
            'Used Azure Dev Ops to deploy services, manage code repositories, and track issues',
          ]
        },
        {
          name: 'Capstone Industry Project',
          position: 'Engineering Student',
          location: 'Calgary, AB',
          time: 'Jan. 2023 to Apr. 2023',
          technology: [
            {name: 'Python', type: 'language'},
            {name: 'C#', type: 'language'},
            {name: 'ROS Network', type: 'framework'},
            {name: 'Unity Engine', type: 'framework'},
            {name: 'Open CV', type: 'library'},
            {name: 'Computer Vision', type: 'concept'},
            {name: 'Control System', type: 'concept'},
          ],
          description: [
            'Developed a vision based control system to steer simulatted equipment inside of a Unity Simulation',
            'Created a computer vision algorithm to detect the edge between standing and cut crop using OpenCV',
            'Produced a control system that used the feedback from they computer vision to steer an implement',
            'Simulated environment in Unity and communicated with a ROS server in a separate Linux environment',
            'Communicated with industry sponsor to track progess and wrote a detailed technical report on solution',
          ]
        },
        {
          name: 'MacDon Industries LTD',
          position: 'Mechanical Design Engineer',
          location: 'Winnipeg, MB',
          time: 'April 2019 to April 2022',
          technology: [],
          description: [
            'Designed hydraulic and mechanical parts and systems for mobile ag equipment (Combine Draper Header)',
            'Communicate with testing department to develop test plans and support field testing',
            'Released designs to production and coordinated with manufacturing and testing to produce product',
          ]
        },
      ]
      return {
        count,
        skills,
        projects,
        colors,
        githubIcon,
        experiences,
      }
    }
  })
</script>

<style lang="sass" scoped>
.bar
  width: 5px
  height: 100%
  border-radius: 3px 0px 0px 3px

.my-div 
  width: 800px
  margin-left: auto
  margin-right: auto
  border-left: 2px solid black
  border-right: 2px solid black
  height: 100%
  background-color: light-grey-1

  @media print
    border: none !important
    background-color: white !important
.link-wrapper
  display: flex
  align-items: center

.centered-image
  display: block
  margin: auto

.rounded-div
  border-radius: 5px 5px 5px 5px

.no-decoration
  text-decoration: none
  color: black

.light-primary-color
  background-color: hsl(200, 60%, 80%)

div
  font-family: 'Arial', 'Helvetica', sans-serif

@media print
  .page-break 
    page-break-before: always
  
</style>
