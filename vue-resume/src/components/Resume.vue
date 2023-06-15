<template>
  <div class="my-div bg-grey-1 q-pa-md">
      <div class="row justify-center text-h4 text-primary">
        {{ name }}
      </div>
      <q-separator horizontal color="primary" />
      <div class="row justify-center q-gutter-sm q-mt-xs">
        <a href="https://www.google.com/maps?q=Calgary" target="_blank" class="no-decoration">
          <q-card class="row q-pr-sm">
            <div class="rounded-div">
              <div class="bg-accent q-ma-sm rounded-div">
                <q-icon name="pin_drop" size="2.5rem" color="black"/>
              </div>
            </div>
            <div class="q-my-auto">
              <div class="text-body text-weight-bold">
                Address
              </div>
              <div class="text-body2">
                Calgary AB, T3B 0Z8
              </div>
            </div>
          </q-card>
        </a>
        <a href="mailto:crookes.garnet@gmail.com" class="no-decoration">
          <q-card class="row q-pr-sm">
            <div class="rounded-div">
              <div class="bg-accent q-ma-sm rounded-div">
                <q-icon name="alternate_email" size="2.5rem" color="black"/>
              </div>
            </div>
            <div class="q-my-auto">
              <div class="text-body text-weight-bold">
                Email
              </div>
              <div class="text-body">
                crookes.garnet@gmail.com
              </div>
            </div>
          </q-card>
        </a>
        <a href="tel:+15872190406" class="no-decoration">
          <q-card class="row q-pr-sm">
            <div class="rounded-div">
              <div class="bg-accent q-ma-sm rounded-div">
                <q-icon name="phone_in_talk" size="2.5rem" color="black"/>
              </div>
            </div>
            <div class="q-my-auto">
              <div class="text-body text-weight-bold">
                Phone
              </div>
              <div class="text-body">
                (587) 219-0406
              </div>
            </div>
          </q-card>
        </a>
        <a href="https://github.com/gcrookes" target="_blank" class="no-decoration">
          <q-card class="row q-pr-sm">
            <div class="rounded-div">
              <div class="bg-accent q-ma-sm rounded-div">
                <img :src="githubIcon" alt="Github Link" class="centered-image" style="width: 2.5rem"/>
              </div>
            </div>
            <div class="q-my-auto">
              <div class="text-body text-weight-bold">
                GitHub
              </div>
              <div class="text-body">
                @gcrookes
              </div>
            </div>
          </q-card>
        </a>
      </div>
      <SectionCard title="Technical & Professional Skills">
        <div class="q-mt-sm">
          <q-badge v-for="skill in skills" class="q-ma-xs" :color="colors[skill.type] ?? 'primary'" rounded><q-icon name="add" />{{ skill.name }}</q-badge>
        </div>
      </SectionCard>
      <SectionCard title="Education">
          <div class="q-mx-md q-mt-sm text-secondary">
            <div class="row justify-between">
              <div class="text-weight-bold">University of Calgary, M.Eng Software Engineering</div>
              <div>April 2023</div>
            </div>
            <div class="row justify-between" style="font-size: 12px;">
              <div class="text-italic q-ml-lg">Cumulative GPA</div>
              <div>4.0 of 4.0</div>
            </div>
            <div class="row justify-between q-mt-xs">
              <div class="text-weight-bold">University of Alberta, BSc. Mechanical Engineering, Coop with Distinction</div>
              <div>April 2019</div>
            </div>
            <div class="row justify-between" style="font-size: 12px;">
              <div class="text-italic q-ml-lg">Cumulative GPA</div>
              <div>3.7 of 4.0</div>
            </div>
          </div>
      </SectionCard>
      <SectionCard title="Software Projects">
          <q-card v-for="project in projects" class="q-mx-md q-mt-sm">
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
              <q-badge v-for="skill in project.technology" class="q-ma-xs" :color="colors[skill.type] ?? 'primary'" rounded>{{ skill.name }}</q-badge>
            </div>
            <table class="text-secondary">
              <li v-for="line in project.description">{{ line }}</li>
            </table>
          </q-card>
      </SectionCard>
  </div>
</template>

<script lang="ts">
  import { defineComponent, ref } from 'vue'
  import SectionCard from './SectionCard.vue'
  import githubIcon from '../assets/github.svg'

  export default defineComponent({
    props: {
      name: {type: String, required: true}
    },
    components: {
      SectionCard
    },
    setup() {
      const count = ref(0)
      const colors = {
        language: 'indigo-7',
        hardware: 'green-10',
        database: 'blue-grey-8',
        framework: 'red-8',
        concept: 'deep-orange-7',
        tool: 'grey-10',
        platform: 'teal-7',
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
        {name: 'Microsoft Azure', type: 'platform'},
        {name: 'CosmosDB', type: 'database'},
        {name: 'MySQL', type: 'database'},
        {name: `REST API's`, type: 'concept'},
        {name: 'NoSQL Databases', type: 'concept'},
        {name: 'Relational Databases', type: 'concept'},
        {name: 'Serverless', type: 'concept'},
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
          // technology: ['Python', 'Tensorflow', 'Arduino', 'Serial Communication', 'EXG Pills', 'Multithreading'],
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
          // technology: ['Python', 'PyQt5', 'MatPlotLib', 'Numpy', 'Pandas', 'Pickle'],
          technology: [{name: 'Python', type: 'language'}, {name: 'PyQt5', type: 'library'}, {name: 'MatPlotLib', type: 'library'}, {name: 'Numpy', type: 'library'}, {name: 'Pandas', type: 'library'}, {name: 'Pickle', type: 'library'}],
          description: [
            'Windows application to improve efficiency of decline analysis of oil & gas wells',
            'GUI allows user to interact with data and select points to fit a curve to',
            // 'Implemented system to create and load save files using Pickle',
            'Imports/Exports CSV files allowing collaboration with other programs',
          ],
          github: "https://github.com/gcrookes/DeclineAnalysis",
        },
        {
          name: 'Course Registration Website',
          // technology: ['Java', 'Javascript', 'HTML', 'CSS', 'Spring Boot', 'MySQL', 'JPA', 'REST API'],
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
      return {
        count,
        skills,
        projects,
        colors,
        githubIcon,
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

</style>
