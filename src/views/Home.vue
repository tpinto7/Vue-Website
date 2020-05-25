<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <v-img
      dark
      max-height="500px"
      src="https://i.ytimg.com/vi/-MKapbz0GIo/maxresdefault.jpg"
    >
      <v-layout fill-height align-center>
        <v-container>
          <v-row align="center" justify="center" class="white--text">
            <v-col cols="12">
              <div
                :class="{'display-2 font-weight-bold ': $vuetify.breakpoint.smAndUp, 'title font-weight-bold': $vuetify.breakpoint.smAndDown}"
              >Welcome to my page.</div>
              <div
                :class="{'headline': $vuetify.breakpoint.smAndUp, 'subtitle-1': $vuetify.breakpoint.smAndDown}"
              >I make applications.</div>
            </v-col>
          </v-row>
        </v-container>
      </v-layout>
    </v-img>
    <v-container class="mt-5">
      <v-layout wrap>
        <v-flex xs12>
          <div class="display-1 font-weight-bold" id="about">About me</div>
        </v-flex>
        <v-flex xs12 mt-5>
          <div
            class="body-1 mt-3"
          >Hey there! My name is Tyler and I am a 2B Software Engineering student at the University of Waterloo. I am passionate about using software for social good, particularly in the health care and sustainability industries.
          I have a strong background in full-stack software development and am building my skills in machine learning and game development. <b>I am actively looking for a Fall 2020 Internship</b>.
          </div>
          <br>
          <div>I have extensive experience with Java, JavaScript, and C++, and am constantly improving my skills every day!</div> 
          <!-- maybe add picture slideshow here --> 
        </v-flex>
      </v-layout>
      <v-layout wrap my-5>
        <v-flex xs12>
          <div class="display-1 font-weight-bold" id="portfolio" style="margin-bottom: 10px;">Work Experience</div>
        </v-flex>
        <v-flex>
          <v-layout wrap>
            <template v-for="(job, i) in jobs">
              <v-card :key="i" style="margin-bottom: 30px;" width="100%">
                <v-card-title>
                <h2><b> {{job.role}} - {{job.name}} </b></h2>

       
                <!-- <div style="float:right!important;">{{job.date}}</div> -->

                                </v-card-title>
                                         <v-card-text>
                <template v-for="(point, j) in job.points">
                  
                  <div :key="j">• {{point}} </div>
                </template>
                      <v-layout>
              <template v-for="(tech, i) in job.technologies">
                <v-flex xs3 :key="i">
                  <div class="text-center">
                    <v-btn icon>
                      <v-icon>{{tech.icon}}</v-icon>
                    </v-btn>
                    <div class="caption">{{tech.name}}</div>
                  </div>
                </v-flex>
              </template>
            </v-layout>
                </v-card-text>

              </v-card>
              <!-- <v-flex :key="i" xs12 sm6 md4>
                {{job.name}}
          <p-portfolio-app :app="app" /> 
              </v-flex> -->
            </template>
          </v-layout>
        </v-flex>
      </v-layout>
      <v-layout wrap my-5>
        <v-flex xs12>
          <div class="display-1 font-weight-bold" id="portfolio" style="margin-bottom: 10px;">Projects</div>
        </v-flex>
        <v-flex>
          <v-layout wrap>
            <template v-for="(project, i) in projects">
              <v-card :key="i" style="margin-bottom: 30px;" width="100%"> 
                
                <div style="text-align:center;">
                  <v-img float="middle" src="src\assets\baguette-logo.png"></v-img>
                                    <v-img float="middle" src="/guardian.jpg"></v-img>
                </div>
                <v-card-title>
                <h2><b> {{project.name}} </b></h2>

       
                <!-- <div style="float:right!important;">{{job.date}}</div> -->

                        </v-card-title>
                            <v-card-text>
                              <div>
                                {{project.description}}
                                </div>
                <!-- <template v-for="(point, j) in job.points">
                  
                  <div :key="j">• {{point}} </div>
                </template> -->
                              <div v-if="project.awards">
        <b>{{project.awards}}</b>
      </div>  
                      <v-layout>
              <template v-for="(tech, i) in project.technologies">
                <v-flex xs3 :key="i">
                  <div class="text-center">
                    <v-btn icon>
                      <v-icon>{{tech.icon}}</v-icon>
                    </v-btn>
                    <div class="caption">{{tech.name}}</div>
                  </div>
                </v-flex>
              </template>
            </v-layout>
            <v-layout>
              <template>
         <v-flex xs12>         
           <div class="text-center">  
            <v-btn icon :href="project.code.link" target="_blank">
              <v-icon>{{project.code.icon}}</v-icon>
            </v-btn>
            <v-btn icon :href="project.devpost.link" target="_blank">
              <v-icon>{{project.devpost.icon}}</v-icon>
            </v-btn>
            </div>
         </v-flex>
              </template>
              </v-layout>
                </v-card-text>

              </v-card>
              <!-- <v-flex :key="i" xs12 sm6 md4>
                {{job.name}}  
          <p-portfolio-app :app="app" /> 
              </v-flex> -->
            </template>
          </v-layout>
        </v-flex>
      </v-layout>
      <v-layout wrap my-5>
        <v-flex xs12 mb-5>
          <div class="display-1 font-weight-bold" id="contact">Feel free to reach out!</div>
        </v-flex>
        <template v-for="(contact, i) in contactLinks">
          <v-flex sm6 md4 xs12 :key="i">
            <p-contact-info :contact="contact" />
          </v-flex>
        </template>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import PContactInfo from "@/components/PContactInfo.vue";

export default {
  name: "home",
  components: {
    PContactInfo
  },
  data() {
    return {
      aboutText:
        "I enjoy building apps in my free time when I'm not doing much. Looking to get into machine learning and trying to automate as many things as possible. Love to encourage new coders that they can do it too! I'm not very smart, just curious to see how things work. I'm also not that good of a writer as you can see. lol. Anyways, you are free to download any of the code thats on my github! And I hope you have a great day!",
      jobs: [
        {
          name: "Veeva",
          role: "Software Engineer",
          date: "Jan 2020 - Apr 2020",
          points: [ "Implemented async job thread in Java which validates an object’s component dependencies and persists the results to SQL database, reducing UI latency by 7.5s.",
          "Added validation logic to an import endpoint that stores results to a downloadable attachment using Java, decreasing the number of components with errors being deployed by 87%.",
"Wrote scripts in company-specific metadata language to create notification and configuration report templates.",
"Constructed frontend logic and components using JS and React to enhance data transferred to RESTful APIs." ],
          technologies: [
            {
              name: "Java",
              icon: "mdi-language-java",
              link: ""
            },
            {
              name: "Spring",
              icon: "mdi-leaf",
              link: ""
            },
            {
              name: "JavaScript",
              icon: "mdi-language-javascript",
              link: ""
            },
                {
              name: "React",
              icon: "mdi-react",
              link: ""
            },
                {
              name: "MySQL",
              icon: "mdi-fish",
              link: ""
            },
          ],
        },
        {
          name: "PointClickCare",
          role: "Software Engineer",
          date: "May 2019 - Aug 2019",
                    points: [ "Architected and implemented a scalable data model for the Identity and Access Management microservice used by over 100 hospitals using Java, Spring and MySQL.",
"Developed over 20 RESTful API endpoints for the admin management of users, including pagination, searching, password encryption, email validation, and the management of users’ apps and accessing entities.",
"Designed client-side web application using Vue.js and Bootstrap to enable state management and connect developed APIs. Integrated Recaptcha onto login components to improve security by 68%.",
"Created a Chrome Extension that parses a patient’s profile using jQuery in under 0.1s and fetches their medical history, observations, and activities.",
"Built workflow using Kubernetes, Argo, and Linux to automate the onboarding process for new customers." 
 ],
           technologies: [
            {
              name: "Java",
              icon: "mdi-language-java",
              link: ""
            },
            {
              name: "Spring",
              icon: "mdi-leaf",
              link: ""
            },
            {
              name: "JavaScript",
              icon: "mdi-language-javascript",
              link: ""
            },
                {
              name: "Vue",
              icon: "mdi-vuejs",
              link: ""
            },
                {
              name: "MySQL",
              icon: "mdi-fish",
              link: ""
            },
                 {
              name: "jQuery",
              icon: "mdi-language-javascript",
              link: ""
            },
          ],
        },
        {
          role: "Undergraduate Research Assistant",
          name: "Sports Applications of Machine Learning Lab",
          date: "Jan 2019 - Present",
          points: ["Collaborated with three team members to prepare a paper accepted at California’s Computer Vision and Pattern Recognition 2019 Expo (arxiv.org/abs/1903.06528).", 
"Compiled dataset for TensorFlow model by using MATLAB to provide pose estimation and event detection for golf swings using computer vision.",
"Integrating deep learning model onto mobile app using Swift and XCode."
],
technologies: [
            {
              name: "Swift",
              icon: "mdi-language-swift",
              link: ""
            },
            {
              name: "XCode",
              icon: "mdi-apple-ios",
              link: ""
            },
            {
              name: "TensorFlow",
              icon: "mdi-alpha-t",
              link: ""
            },
            {
              name: "MATLAB",
              icon: "mdi-alpha-m",
              link: ""
            }
          ],
        }



      ],
      projects: [
        {
          name: "Guardian", 
          image: "food-vision-logo.png",
          description: "Novel helmet using IOT to improve firefighter helmet. Sensors are used to track environmental data, which is uploaded onto Firebase and displayed in dynamic charts on an interactive dashboard.",
          awards: "Hack the North 2019 Overall Winner, MLH best use of Google Cloud Platform, CANSOFCOM Challenge Winner",
          technologies: [
            {
              name: "JavaScript",
              icon: "mdi-language-javascript",
              link: ""
            },
            {
              name: "Vue",
              icon: "mdi-vuejs",
              link: ""
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: "https://github.com/tpinto7/Guardian"
          },
          devpost: {
            name: "devpost",
            icon: "mdi-alpha-d-box",
            link: "https://devpost.com/software/guardian-2n7q3s"
          }
        },
        {
          name: "FireGuard", 
          image: "food-vision-logo.png",
          description: "A network of IoT beacons that can be placed in forests to predict forest fires. Time-series forecasting was used based off of the readings of each beacon's sensors, and displayed using Google Maps APIs and Vue.js.",
          awards: "Queen's Hacks Top 10 Overall, Sunlife Health Hack Winner, Best use of Radar.io",
          technologies: [
            {
              name: "JavaScript",
              icon: "mdi-language-javascript",
              link: ""
            },
            {
              name: "Vue",
              icon: "mdi-vuejs",
              link: ""
            },
             {
              name: "Google Maps",
              icon: "mdi-google-maps",
              link: ""
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: "https://github.com/tpinto7/fireguard"
          },
          devpost: {
            name: "devpost",
            icon: "mdi-alpha-d-box",
            link: "https://devpost.com/software/fireguard-07cbjk"
          }
        },
                {
          name: "The Blood Bot", 
          image: "food-vision-logo.png",
          description: "A Java GUI that estimates the amount of blood a patient lost during surgery through analyzing the blood saturation of the sponges used",
          awards: "DeltaHacks 2020 Hypercare Prize for Best Health Hack",
          technologies: [
            {
              name: "JavaScript",
              icon: "mdi-language-javascript",
              link: ""
            },
            {
              name: "Vue",
              icon: "mdi-vuejs",
              link: ""
            },
             {
              name: "Google Maps",
              icon: "mdi-google-maps",
              link: ""
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: "https://github.com/tpinto7/bloodbot"
          },
          devpost: {
            name: "devpost",
            icon: "mdi-alpha-d-box",
            link: "https://devpost.com/software/the-blood-bot"
          }
        }
      ],
      apps: [
        {
          name: "Guardian",
          price: "FREE",
          logo: "food-vision-logo.png",
          platforms: [
            {
              name: "apple",
              icon: "mdi-apple",
              link: "https://apps.apple.com/us/app/food-vision/id1437083324"
            }
          ],
          description:
            "One day my friend and I were eating at a restaurant and she suddenly asked me what an item looks like. I looked up at her an told her I didnt know. Then she told me why dont you make an app where you can see the pictures of food thats on the menu? Then I made Food Vision. :)",
          technologies: [
            {
              name: "JavaScript",
              icon: "mdi-language-javascript",
              link: ""
            },
            {
              name: "Vue",
              icon: "mdi-vuejs",
              link: ""
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: ""
          },
          devpost: {
            name: "devpost",
            icon: "mdi-alpha-d-box",
            link: ""
          }
        },
        {
          name: "Finance App",
          price: "COMING SOON",
          logo: "finance-logo.png",
          platforms: [
            {
              name: "apple",
              icon: "mdi-apple",
              link: ""
            },
            {
              name: "android",
              icon: "mdi-android",
              link: ""
            }
          ],
          description:
            "My sister always kept asking me about my money situation and how I was doing there, so I decided that I would make an app that we could use to track our finances. Using Plaid I was able to get access to my bank account and hers and connect the 2 using firebase Functions and Auth to secure the app. ",
          technologies: [
            {
              name: "VueJS",
              icon: "mdi-vuejs",
              link: ""
            },
            {
              name: "Vuetify",
              icon: "mdi-vuetify",
              link: ""
            },
            {
              name: "Cordova",
              icon: "mdi-cordova",
              link: ""
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: ""
            },
            {
              name: "Node",
              icon: "mdi-nodejs",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: "https://github.com/uzirthapa/finance-app"
          }
        },
        {
          name: "Baguette",
          price: "COMING SOON",
          logo: "baguette-logo.png",
          platforms: [
            {
              name: "apple",
              icon: "mdi-apple",
              link: ""
            },
            {
              name: "android",
              icon: "mdi-android",
              link: ""
            }
          ],
          description:
            "Similar to 'Bag it'. I wanted to make a swippable market place where people could swipe on goods from a store. Also it got rid of all the extra distractions and you are able to focus on just one item at a time. Still need to build the recommender system. But I am working on it! :)",
          technologies: [
            {
              name: "VueJS",
              icon: "mdi-vuejs",
              link: ""
            },
            {
              name: "Vuetify",
              icon: "mdi-vuetify",
              link: ""
            },
            {
              name: "Cordova",
              icon: "mdi-cordova",
              link: ""
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: ""
          }
        },
        {
          name: "Facebook UI",
          price: "OPEN SOURCE",
          logo: "facebook-logo.png",
          platforms: [
            {
              name: "web",
              icon: "mdi-web",
              link: "https://uzirthapa.github.io/facebook-ui/dist/"
            }
          ],
          description:
            "One Day build - I saw this guy on youtube building apps in 1 day and I wanted to see if I could make a better version of the Facebook UI. I didn't design it but I found this design on dribbble and just thought I would make the designers UI come to life.",
          technologies: [
            {
              name: "VueJS",
              icon: "mdi-vuejs",
              link: ""
            },
            {
              name: "Vuetify",
              icon: "mdi-vuetify",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: "https://github.com/uzirthapa/facebook-ui"
          }
        },
        {
          name: "Firebird Fitness",
          price: "LIVE",
          logo: "firebird-logo.png",
          platforms: [
            {
              name: "web",
              icon: "mdi-web",
              link: "https://firebirdfitness.xyz/"
            }
          ],
          description:
            "I needed a place to put my workouts that we do at work, So I made a place where I could store them and also if I forgot a certian exercise I could easily search it and watch a video on how to do it.",
          technologies: [
            {
              name: "VueJS",
              icon: "mdi-vuejs",
              link: "https://vuejs.org/"
            },
            {
              name: "Vuetify",
              icon: "mdi-vuetify",
              link: "https://vuetifyjs.com/"
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: "https://firebase.google.com/"
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: "https://github.com/uzirthapa/Firebird-Fitness"
          }
        },
        {
          name: "Ecommerce Biolerplate",
          price: "OPEN SOURCE",
          logo: "logo.png",
          platforms: [
            {
              name: "web",
              icon: "mdi-web",
              link: "https://ecommerce-skeleton.firebaseapp.com/"
            }
          ],
          description:
            "We Wanted to help people who want to create an ecommerce store with VueJS and Vuetify have a template that had authentication and payments integrated right from the get go. So now you can hit the ground running! In Collaboration with Aatish Balla.",
          technologies: [
            {
              name: "VueJS",
              icon: "mdi-vuejs",
              link: "https://vuejs.org/"
            },
            {
              name: "Vuetify",
              icon: "mdi-vuetify",
              link: "https://vuetifyjs.com/"
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: "https://firebase.google.com/"
            },
            {
              name: "Stripe",
              icon: "mdi-credit-card-outline",
              link: ""
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: "https://github.com/uzirthapa/ecommerce-skeleton"
          }
        },
        {
          name: "Sacred Summits",
          price: "LIVE",
          logo: "ss-logo-high-res.png",
          platforms: [
            {
              name: "web",
              icon: "mdi-web",
              link: "https://sacred-summits-web.firebaseapp.com/"
            }
          ],
          description:
            "Sacred Summits was looking for a redesign of their website and they asked me to come up with a sample. This is what I came up with.",
          technologies: [
            {
              name: "VueJS",
              icon: "mdi-vuejs",
              link: "https://vuejs.org/"
            },
            {
              name: "Vuetify",
              icon: "mdi-vuetify",
              link: "https://vuetifyjs.com/"
            },
            {
              name: "Firebase",
              icon: "mdi-firebase",
              link: "https://firebase.google.com/"
            }
          ],
          code: {
            name: "github",
            icon: "mdi-github",
            link: ""
          }
        }
      ],
      contactLinks: [
        {
          name: "Email",
          value: "tjpinto@uwaterloo.ca",
          link: "mailto:tjpinto@uwaterloo.ca",
          icon: "mdi-email"
        },
        {
          name: "LinkedIn",
          value: "Tyler Pinto",
          link: "https://www.linkedin.com/in/tylerpinto/",
          icon: "mdi-linkedin"
        },
        {
          name: "Github",
          value: "tpinto7",
          link: "https://github.com/tpinto7/",
          icon: "mdi-github"
        },
      ]
    };
  }
};
</script>
