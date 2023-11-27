<template>
  <div class="my-div bg-grey-1 q-pa-md">
    <div class="row justify-between q-mx-sm text-h4 text-primary">
      <div class="text-bold">{{ name }}</div>
      <div
        v-if="designation"
        class="q-ml-lg text-h6 flex items-end text-secondary"
      >
        Full Stack Software Developer,
        {{ designation }}
      </div>
    </div>
    <q-separator horizontal color="primary" style="height: 3px" />
    <div class="row justify-center q-gutter-xs q-mt-md">
      <ContactCard
        link="https://www.google.com/maps/place/Montgomery,+Calgary,+AB/@51.0643662,-114.1828838,12.93z/data=!4m6!3m5!1s0x53716ef989772efd:0xd9c32fe94b8d9f74!8m2!3d51.074714!4d-114.1641658!16zL20vMGg0dGM1?entry=ttu"
        title="Address"
        text="Calgary AB, T3B 0Z8"
        icon="pin_drop"
      />
      <ContactCard
        link="mailto:crookes.garnet@gmail.com"
        title="Email"
        text="crookes.garnet@gmail.com"
        icon="alternate_email"
      />
      <ContactCard
        link="tel:+15872190406"
        title="Phone"
        text="(587) 219-0406"
        icon="phone_in_talk"
      />
      <ContactCard
        link="https://github.com/gcrookes"
        title="GitHub"
        text="@gcrookes"
      >
        <img
          :src="githubIcon"
          alt="Github Link"
          class="centered-image"
          style="width: 2.5rem"
        />
      </ContactCard>
    </div>
    <SectionCard title="Technical & Professional Skills" icon="construction">
      <div class="q-mt-sm q-px-md text-italic justify-between row">
        <q-badge
          v-for="skill in skills"
          class="q-ma-xs q-py-xs text-body"
          style="font-size: 15px"
          size="lg"
          :color="colors[skill.type] ?? 'primary'"
          rounded
          :key="skill"
          ><q-icon name="add" />{{ skill.name }}</q-badge
        >
      </div>
    </SectionCard>
    <SectionCard title="Education" icon="school">
      <div class="q-mx-md q-mt-sm text-secondary">
        <div class="row justify-between">
          <div class="text-weight-bold">
            University of Calgary, M.Eng Software Engineering
          </div>
          <div>April 2023</div>
        </div>
        <div class="row justify-between" style="font-size: 12px">
          <div class="text-italic q-ml-sm">Cumulative GPA</div>
          <div>4.0 of 4.0</div>
        </div>
        <div class="row justify-between q-mt-xs">
          <div class="text-weight-bold">
            University of Alberta, BSc. Mechanical Engineering, Coop with
            Distinction
          </div>
          <div>April 2019</div>
        </div>
        <div class="row justify-between" style="font-size: 12px">
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
        <div
          v-if="exp.technology.length > 0"
          class="q-pt-xs text-secondary text-italic text-weight-bold"
        >
          Utilized:
          <q-badge
            v-for="skill in exp.technology"
            class="q-ma-xs"
            :color="colors[skill.type] ?? 'primary'"
            rounded
            :key="skill"
            >{{ skill.name }}</q-badge
          >
        </div>
        <table class="text-secondary q-pt-xs">
          <li v-for="line in exp.description" class="q-ml-md" :key="line">
            {{ line }}
          </li>
        </table>
      </q-card>
    </SectionCard>
    <div class="page-break" />
    <SectionCard title="Work Experience" icon="precision_manufacturing">
      <q-card
        v-for="exp in experiencesPage2"
        class="q-mx-md q-mt-sm"
        :key="exp"
      >
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
        <div
          v-if="exp.technology.length > 0"
          class="q-pt-xs text-secondary text-italic text-weight-bold"
        >
          Utilized:
          <q-badge
            v-for="skill in exp.technology"
            class="q-ma-xs"
            :color="colors[skill.type] ?? 'primary'"
            rounded
            :key="skill"
            >{{ skill.name }}</q-badge
          >
        </div>
        <table class="text-secondary q-pt-xs">
          <li v-for="line in exp.description" class="q-ml-md" :key="line">
            {{ line }}
          </li>
        </table>
      </q-card>
    </SectionCard>
    <SectionCard title="Software Projects" icon="architecture">
      <q-card
        v-for="project in projects"
        class="q-mx-md q-mt-sm"
        :key="project"
      >
        <div
          class="q-my-none row text-h6 text-bold justify-between align-center"
        >
          {{ project.name }}
          <div class="text-xs row items-center">
            <a :href="project.video" class="link-wrapper" target="_blank">
              <q-icon
                v-if="project.video"
                class="link-wrapper"
                name="play_circle"
                size="1.5rem"
              />
            </a>
            <a :href="project.website" class="link-wrapper" target="_blank">
              <q-icon
                v-if="project.website"
                class="link-wrapper"
                name="language"
                size="1.5rem"
              />
            </a>
            <a
              v-if="project.github"
              :href="project.github"
              class="link-wrapper"
              target="_blank"
            >
              <img
                :src="githubIcon"
                alt="Github Link"
                class="centered-image"
                style="width: 1.5rem"
              />
            </a>
          </div>
        </div>
        <q-separator color="primary" />
        <div class="q-pt-xs text-secondary text-italic text-weight-bold">
          Utilized:
          <q-badge
            v-for="skill in project.technology"
            class="q-ma-xs"
            :color="colors[skill.type] ?? 'primary'"
            rounded
            :key="skill"
            >{{ skill.name }}</q-badge
          >
        </div>
        <table class="text-secondary">
          <li v-for="line in project.description" class="q-ml-md" :key="line">
            {{ line }}
          </li>
        </table>
      </q-card>
    </SectionCard>
    <!-- <SectionCard title="Other" icon="architecture">
      <q-card title="Academic Achievements">
        <div
          class="q-my-none row text-h6 text-bold justify-between align-center"
        >
          Academic Achievements
        </div>
        <q-separator color="primary" />
        <div
          v-for="ach in academicAchievements"
          :key="ach.name"
          class="q-mx-md text-secondary"
        >
          {{ ach.name }}
        </div>
      </q-card>
    </SectionCard> -->
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import SectionCard from "./SectionCard.vue";
import githubIcon from "../assets/github.svg";
import ContactCard from "./ContactCard.vue";

export default defineComponent({
  props: {
    name: { type: String, required: true },
    designation: { type: String, default: "" },
  },
  components: {
    SectionCard,
    ContactCard,
  },
  setup() {
    const count = ref(0);
    const colors = {
      concept: "deep-orange-7",
      database: "blue-grey-8",
      framework: "red-8",
      hardware: "green-10",
      language: "indigo-7",
      platform: "teal-7",
      tool: "grey-10",
    };
    const skills = [
      { name: "Python", type: "language" },
      { name: "TypeScript", type: "language" },
      { name: "C#", type: "language" },
      { name: "HTML/CSS", type: "language" },
      { name: "Java", type: "language" },
      { name: "C++", type: "language" },
      { name: "SQL", type: "language" },
      { name: "ASP.NET Core", type: "framework" },
      { name: "VueJS", type: "framework" },
      { name: "React", type: "framework" },
      { name: "Spring Boot", type: "framework" },
      { name: "Unity", type: "framework" },
      { name: "Microsoft Azure", type: "platform" },
      { name: "CosmosDB", type: "database" },
      { name: "MySQL", type: "database" },
      { name: `REST API's`, type: "concept" },
      { name: "NoSQL Databases", type: "concept" },
      { name: "Relational Databases", type: "concept" },
      { name: "Serverless", type: "concept" },
      { name: "Machine Learning", type: "concept" },
    ];
    const projects = [
      {
        name: "Movie Theater Ticket System",
        technology: [
          { name: "Javascript", type: "language" },
          { name: "React", type: "framework" },
          { name: "Spring Boot", type: "framework" },
          { name: "MySQL", type: "database" },
          { name: "REST API", type: "concept" },
        ],
        description: [
          "Created a website where users can find and purchase tickets for a movie theater",
          "Frontend implemented using React, users can login or use the site as a guest",
          "Backend implemented in Spring Boot, with data stored on a MySQL database",
        ],
        github: "https://github.com/AI-Cupid/registration-form",
      },
      {
        name: "EOG Mouse Control - NatHacks Hackathon",
        technology: [
          { name: "Python", type: "language" },
          { name: "Tensorflow", type: "library" },
          { name: "Arduino", type: "hardware" },
          { name: "EXG Pills", type: "hardware" },
          { name: "Multithreading", type: "concept" },
          { name: "Serial Communication", type: "concept" },
        ],
        description: [
          "Created a Brain Computer Interface to control a computer mouse from EOG Data",
          "Captured and filtered data from multiple EXG Pill sensors on an Arduino",
          "Used serial communication to transmit data between Arduino and computer",
        ],
        github: "https://github.com/gcrookes/EOGMouseControl",
        website:
          "http://mohammed-alhajjaj.sptek.tech/project-details.html?id=UKEGBC2UP0ay9Csg48v00g",
        video:
          "https://www.youtube.com/watch?v=8hNw2gWGpAQ&ab_channel=MohammedAlhajjaj",
      },
      {
        name: "AI Cupid Registration Page",
        technology: [
          { name: "Typescript", type: "language" },
          { name: "VueJs", type: "framework" },
          { name: "PostgreSQL", type: "database" },
          { name: "Supabase", type: "platform" },
          { name: "REST API", type: "concept" },
        ],
        description: [
          "Created and deployed a Vue Js website to capture registrations for a dating app concept",
          "Saved all registrations in to a Supabase database",
        ],
        github: "https://github.com/AI-Cupid/registration-form",
        website: "https://ai-cupid.github.io/registration-form/#/",
      },
      {
        name: "Course Registration Website",
        technology: [
          { name: "Java", type: "language" },
          { name: "Javascript", type: "language" },
          { name: "HTML", type: "language" },
          { name: "CSS", type: "language" },
          { name: "Spring Boot", type: "framework" },
          { name: "MySQL", type: "database" },
          { name: "JPA", type: "library" },
          { name: "REST API", type: "concept" },
        ],
        description: [
          "Created a website which students could use to login, enroll in, or drop courses",
          "Frontend implemented with HTML/CSS/Javascript, served on the backend",
          "Backend implemented in Spring Boot, with data stored on a MySQL database",
          "Communcation was done between client and server using a REST API",
        ],
        github: "https://github.com/dpwalz/ENSF607-608",
      },
      {
        name: "Decline Analysis Application",
        technology: [
          { name: "Python", type: "language" },
          { name: "PyQt5", type: "library" },
          { name: "MatPlotLib", type: "library" },
          { name: "Numpy", type: "library" },
          { name: "Pandas", type: "library" },
          { name: "Pickle", type: "library" },
        ],
        description: [
          "Windows application to improve efficiency of decline analysis of oil & gas wells",
          "GUI allows user to interact with data and select points to fit a curve to",
          "Implemented system to create and load save files using Pickle",
        ],
        github: "https://github.com/gcrookes/DeclineAnalysis",
      },
    ];
    const experiences = [
      {
        name: "Child Friendly Care",
        position: "Full Stack Software Developer",
        location: "Calgary, AB",
        time: "Feb. 2023 to Present",
        technology: [
          { name: "TypeScript", type: "language" },
          { name: "C#", type: "language" },
          { name: "HTML/CSS", type: "language" },
          { name: "VueJS", type: "framework" },
          { name: "ASP.NET Core", type: "framework" },
          { name: "Microsoft Azure", type: "platform" },
          { name: "CosmosDB", type: "database" },
          { name: "Serverless", type: "concept" },
        ],
        description: [
          "Developed a web application to and integrate all functionality required to operate a daycare in a single site",
          "Successfully launched product in multiple day care centers, and quickly responeded to customer issues",
          "Built integrations with Stripe, Azure B2C, QuickBooks, Rotessa for handling transactions and authentication",
          "Integrated automanted end to end tesing through Postman into CI/CD pipeline runs",
          "Created RESTful API using the ASP.NET Core framework deployed on serverless Azure Functions",
          "Utilized Microsoft Azure Cosmos NoSQL database for data storage and logging production failures",
          "Used Azure Dev Ops to deploy services, manage code repositories, and track issues",
          "Participated in daily scrum meetings and worked with stakeholders to understand priorities",
        ],
      },
      {
        name: "Capstone Industry Project",
        position: "Engineering Student",
        location: "Calgary, AB",
        time: "Jan. 2023 to Apr. 2023",
        technology: [
          { name: "Python", type: "language" },
          { name: "C#", type: "language" },
          { name: "ROS Network", type: "framework" },
          { name: "Unity Engine", type: "framework" },
          { name: "Open CV", type: "library" },
          { name: "Computer Vision", type: "concept" },
          { name: "Control System", type: "concept" },
        ],
        description: [
          "Developed a vision based control system to steer simulatted equipment inside of a Unity Simulation",
          "Created a computer vision algorithm to detect the edge between standing and cut crop using OpenCV",
          "Produced a control system that used the feedback from they computer vision to steer an implement",
          "Simulated environment in Unity and communicated with a ROS server in a separate Linux environment",
          "Communicated with industry sponsor to track progess and wrote a detailed technical report on solution",
          "Delivered report and source code to sponsor who was optimistic about result to test in the field",
        ],
      },
    ];

    const experiencesPage2 = [
      {
        name: "MacDon Industries LTD",
        position: "Mechanical Design Engineer",
        location: "Winnipeg, MB",
        time: "April 2019 to April 2022",
        technology: [],
        description: [
          "Designed hydraulic and mechanical parts and systems for mobile ag equipment (Combine Draper Header)",
        ],
      },
      {
        name: "Repsol Canada",
        position: "Student Reservior Engineer",
        location: "Calgary, AB",
        time: "January 2018 to August 2018",
        technology: [],
        description: [
          "Supported reserviour engineering team in analyzing both conventional and unconventional assets",
          "Used techniques of Well testing, reserviour simulation, and DFIT analyis to analyze and forecast production",
        ],
      },
    ];
    const academicAchievements = [
      {
        name: "First Class Standing in Engineering",
        year: "2015-2019",
      },
      {
        name: "Healy Estate Scholarship",
        year: "2014-2019",
      },
      {
        name: "Louise McKinney Post-Secondary Scholarship",
        year: "2015, 2017",
      },
      {
        name: "Jason Lang Scholarship",
        year: "2016",
      },
      {
        name: "University of Alberta Academic Excellence Scholarship",
        year: "2014",
      },
      {
        name: "Faculty of Engineering Academic Excellence Scholarship",
        year: "2014",
      },
      {
        name: "John and Irene Basaraba Scholarship in Engineering",
        year: "2014",
      },
    ];

    const extraCurricular = [
      "Placed 3rd, 2019 Canadian Engineering Competition Consulting Division",
      "Placed 1st, 2019 Western Canada Engineering Competition Consulting Division",
      "Placed 1st, 2018 U of A Engineering Competition Consulting Division",
      "Captain of High School Basketball Team and two time MVP",
      "ASAA bronze medal in High School Provincial Volleyball",
      "President of Coronation 4-H Beef Club 2013-2014",
      "Enjoy Skiing and Hiking",
    ];

    const other = [
      "Manitoba Class 5 dr abstract and a vehicle",
      "Willing to relocate as required",
    ];

    return {
      count,
      skills,
      projects,
      colors,
      githubIcon,
      experiences,
      experiencesPage2,
      academicAchievements,
      extraCurricular,
      other,
    };
  },
});
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
  text-decoration: none
  color: inherit

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
