<template>
  <div class="my-div bg-grey-1 q-pa-md">
      <div class="row justify-center text-h3 text-primary">
        {{ name }}
      </div>
      <q-separator horizontal color="primary" />
      <div class="row justify-center text-secondary q-my-sm">
          <div class="text-right q-pa-xs">
            5015B 23rd Ave
            <br>
            Calgary AB, T3B 0Z8
          </div>
          <q-separator vertical color="primary" thickness="2px" />
          <div class="q-pa-xs">
            (587) 219-0406
            <br>
            crookes.garnet@gmail.com
          </div>
      </div>
      <SectionCard title="Technical & Professional Skills">
        <div class="q-my-sm">
          <q-badge v-for="skill in skills" class="q-ma-xs" color="primary" rounded outline><q-icon name="add" />{{ skill }}</q-badge>
        </div>
      </SectionCard>
      <SectionCard title="Education">
          <div class="q-ml-xs q-my-sm text-secondary">
            <div>University of Calgary, M.Eng Software Engineering</div>
            <div>University of Alberta, BSc. Mechanical Engineering, Coop with Distinction</div>
          </div>
      </SectionCard>
      <SectionCard title="Software Projects">
          <q-card v-for="project in projects" class="q-mx-md q-my-sm">
            <div class="q-my-none text-h6 text-bold">{{ project.name }}</div>
            <q-separator color="primary" />
            <div class="q-pt-xs text-secondary text-italic">
              Utilized: 
              <q-badge v-for="skill in project.technology" class="q-ma-xs" color="primary" rounded>{{ skill }}</q-badge>
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

  export default defineComponent({
    props: {
      name: {type: String, required: true}
    },
    components: {
      SectionCard
    },
    setup() {
      const count = ref(0)
      const skills = [
        'Python',
        'Java',
        'C++',
        'JavaScript',
        'HTML/CSS',
        'Arduino',
        'MySQL',
        'React',
        `REST API's`,
        'Spring Boot',
        'Relational Databases',
        'Machine Learning',
        'Microsoft PowerPoint',
        'Microsoft Excel',
        'Microsoft Word'
      ]
      const projects = [
        {
          name: 'Movie Theater Ticket Website',
          technology: ['React', 'Javascript', 'Java', 'Spring Boot', 'MySQL', 'JPA', 'REST API'],
          description: [
            'Created a website where users can find and purchase tickets for a movie theater',
            'Frontend implemented using React, users can login or use the site as a guest',
            'Backend implemented in Spring Boot, with data stored on a MySQL database',
          ]
        },
        {
          name: 'EOG Mouse Control - NatHacks Hackathon',
          technology: ['Python', 'Tensorflow', 'Arduino', 'Serial Communication', 'EXG Pills', 'Multithreading'],
          description: [
            'Created a Brain Computer Interface to control a computer mouse from EOG Data',
            'Captured and filtered data from multiple EXG Pill sensors on an Arduino',
            'Used serial communication to transmit data between Arduino and computer',
            'Ran a multithreaded script to analyze data and control a computer mouse',
          ] 
        },
        {
          name: 'Decline Analysis Application',
          technology: ['Python', 'PyQt5', 'MatPlotLib', 'Numpy', 'Pandas', 'Pickle'],
          description: [
            'Windows application to improve efficiency of decline analysis of oil & gas wells',
            'GUI allows user to interact with data and select points to fit a curve to',
            'Implemented system to create and load save files using Pickle',
            'Imports/Exports CSV files allowing collaboration with other programs',
          ] 
        },
        {
          name: 'Course Registration Website',
          technology: ['Java', 'Javascript', 'HTML', 'CSS', 'Spring Boot', 'MySQL', 'JPA', 'REST API'],
          description: [
            'Created a website which students could use to login, enroll in, or drop courses',
            'Frontend implemented with HTML/CSS/Javascript, served on the backend',
            'Backend implemented in Spring Boot, with data stored on a MySQL database',
            'Communcation was done between client and server using a REST API',
          ] 
        }
      ]
      return {
        count,
        skills,
        projects
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

</style>
