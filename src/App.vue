<template>
    <div id="app"
         class="container"
         v-bind:data-black-white="isBW"
    v-bind:data-resume-type="resumeType">
        <div class="header">
            <div class="name">
                Jim Lee
            </div>
        </div>
        <!-- End of Header -->

        <div class="personal-info">
            <table>
                <thead>
                    <tr>
                        <th colspan="2" class="title">
                            <h1>Contact Info</h1>
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="contact address">
                        <td><i class="fa fa-home"></i></td>
                        <td><h2>228 E Charleston Rd</h2></td>
                    </tr>
                    <tr class="contact address">
                        <td></td>
                        <td><h2>Palo Alto, CA 94306</h2></td>
                    </tr>
                    <tr class="contact phone-number">
                        <td><i class="fa fa-phone"></i></td>
                        <td><h2><a href="tel:9495021395">(949) 502-1395</a></h2></td>
                    </tr>
                    <tr class="contact email">
                        <td><i class="fa fa-envelope"></i></td>
                        <td><h2><a href="mailto:jimleee945@gmail.com">jimleee945@gmail.com</a></h2></td>
                    </tr>
                    <tr class="contact linkedln">
                        <td><i class="fa fa-linkedin-square"></i></td>
                        <td><h2><a href="https://www.linkedin.com/in/jimleee945/">linkedin.com/in/jimleee945</a></h2></td>
                    </tr>
                    <tr class="contact github">
                        <td><i class="fa fa-github"></i></td>
                        <td><h2><a href="https://github.com/jil945">https://github.com/jil945</a></h2></td>
                    </tr>
                </tbody>
            </table>
        </div>
        <!-- End of Personal Info -->

        <div class="sidebar">
            <h1 class="title">
                Skills
            </h1>

            <div class="skill-set program-lang">
                <h2 class="title">
                    Programming Languages
                </h2>
                <ul>
                    <li v-for="p in programmingLanguages" v-bind:key="p.title">
                        <span class="level">{{ p.title }}</span>
                        <div class="lang">
                            {{ p.value.join(", ") }}
                        </div>
                    </li>
                </ul>
            </div>

            <div v-for="s in skillSet" v-bind:class="['skill-set', toClass(s.title)]" v-bind:key="s.title">
                <h2 class="title">
                    {{ s.title }}
                </h2>
                <ul>
                    <li v-for="(v, i) in s.value" v-bind:key="'li-' + i">
                        <template v-if="typeof v === 'string'">
                            {{ v }}
                        </template>
                        <template v-else>
                            <span v-for="k in Object.keys(v)" v-bind:class="k" v-bind:key="k">{{ v[k] }}</span>
                        </template>
                    </li>
                </ul>
            </div>
        </div>
        <!-- End of Sidebar -->

        <div class="main">
            <div class="experience">
                <h1>Experience</h1>
                <hr>
                <div class="job">
                    <div class="duration">
                        9/2017 - 6/2019
                    </div>
                    <h2 class="title">
                        Software Development Intern
                    </h2>
                    <div class="location">
                        Siemens PLM Software, <span class="city">Cypress, CA</span>
                    </div>
                    <div class="details">
                        <ul>
                            <li>Lead a team of five in migrating a legacy database utility desktop app to a web app using Vue.js and Java Spring</li>
                            <li>Developed and maintained an issue reporting/tracking web app using Vue.js and Java Spring</li>
                            <ul>
                                <li>Implemented key features such as WYSIWYG text editor and hardware reporting system</li>
                            </ul>
                        </ul>
                    </div>
                </div>
                <div class="job">
                    <div class="duration">
                        7/2016 - 8/2016
                    </div>
                    <h2 class="title">
                        Software Testing Intern
                    </h2>
                    <div class="location">
                        Industrial Technology Research Institute, <span class="city">Hsinchu, Taiwan</span>
                    </div>
                    <div class="details">
                        <ul>
                            <li>Created test plans for ITRI OpenStack Distribution</li>
                            <li>Automated testing process using Selenium and Python</li>
                        </ul>
                    </div>
                </div>
            </div>
            
            <div class="education">
                <h1>Education</h1>
                <hr>
                <div class="degree">
                    <div class="duration">
                        9/2017 - 6/2019
                    </div>
                    <h2 class="title">
                        M.S. in Computer Science
                    </h2>
                    <div class="location">
                        University of California, Irvine
                    </div>
                    <div class="details">
                        <ul>
                            <li class="gpa">
                                GPA: 3.74/4.0
                            </li>
                            <li>Member of Association for Computer Machinery</li>
                            <li>Relevant Courses: Computer Networks, Wireless Networking, Graph Algorithms</li>
                        </ul>
                    </div>
                </div>
                <div class="degree">
                    <div class="duration">
                        9/2015 - 6/2017
                    </div>
                    <h2 class="title">
                        B.S. in Mathematics and Computer Science
                    </h2>
                    <div class="location">
                        University of California, San Diego
                    </div>
                    <div class="details">
                        <ul>
                            <li class="gpa">
                                GPA: 3.61/4.0
                            </li>
                            <li>Member of Society of Asian Scientists and Engineers</li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class="projects course-projects">
                <div class="project-header">
                    <h1>Projects</h1>
                    <hr>
                </div>

                <div v-for="p in courseProjects" v-bind:class="['project', toClass(p.title)]" v-bind:key="p.title">
                    <div class="title">
                        {{ p.title }} <span class="tech-used">({{ p.techUsed.join(", ") }})</span>
                    </div>
                    <div class="location">
                        {{ p.location }}, <span class="date">{{ p.date }}</span>
                    </div>
                    <div class="details">
                        <ul>
                            <li v-for="(d, i) in p.details" v-bind:key="i">
                                {{ d }}
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
            
            
            <!-- <div class="extra">
                <h1>Extra-Cirricular/Hobbies</h1>
                <hr>
                <div class="details">
                    <ul>
                        <li>Maintain/upgrade home lab</li>
                        <li>Learning VMWare and Docker Containers</li>
                    </ul>
                </div>
            </div> -->
        </div>
        <!-- End of Main Content -->     
    </div>
</template>

<script>
export default {
    name: "App",
    computed: {
        isBW() {
            return process.env.VUE_APP_BLACK_WHITE;
        },
        resumeType() {
            return process.env.VUE_APP_RESUME_TYPE;
        },
        isNetwork() {
            return this.resumeType === "network";
        },
        programmingLanguages() {
            let res = [];
            res.push({
                title: "Advance",
                value: [ this.isNetwork ? "C/C++" : "JavaScript", "Python", "Java"],
            });
            res.push({
                title: "Proficient",
                value: [this.isNetwork ? "JavaScript" : "C/C++", "HTML", "CSS", "PHP", "SQL"],
            });
            res.push({
                title: "Basic",
                value: ["Ocaml", "Verilog", "MATLAB"]
            });
            return res;
        },
        skillSet() {
            let res = [];
            if (!this.isNetwork) {
                res.push({
                    title: "Frameworks",
                    value: ["Vue.js", "React.js", "React Native", "Spring", "jQuery"]
                });
            }
            res.push({
                title: "Tools",
                value: this.isNetwork ? ["GNS3", "ns-3", "Wireshark"] : ["NPM", "Git", "Mecurial"]
            });
            res.push({
                title: "Operating Systems",
                value: ["Windows", "MacOs", "Linux (Ubuntu)"]
            });
            res.push({
                title: "Languages",
                value: [
                    {
                        value: "English",
                        level: "(Fluent)"
                    }, {
                        value: "Mandarin",
                        level: "(Native)"
                    }
                ]
            });
            return res;
        },
        courseProjects() {
            const UCI  = "University of California, Irvine";
            const UCSD = "University of California, San Diego";

            let JEFS = {
                title: "Just Enjoy Our Food Suggestions",
                techUsed: ["React Native", "Django"],
                location: UCI,
                date: "Winter 2019",
                details: [
                    "A cross-platform meal recommendation mobile app focused on weight loss",
                    "Used passive data stream and user preferences to create a weekly meal plan",
                    // "Worked in a group of 4, responsible for front end"
                ]
            };

            let othelloAi = {
                title: "Othello AI",
                techUsed: ["Python"],
                location: UCI,
                date: "Fall 2018",
                details: [
                    "Created an Othello AI using the Alpha-Beta pruning algorithm",
                    "Tested different heuristics to create the best heuristic for Othello"
                ]
            };

            let wifiTcp = {
                title: "Optimal Transport Layer Protocol over Wifi",
                techUsed: ["C++"],
                location: UCI,
                date: "Spring 2018",
                details: [
                    "Simulated a wireless home network using ns-3",
                    "Compared the latency, re-transmission rate, and throughput across the variations of TCP and UDP in the simulated network",
                ]
            };
            let webWorkerBenchmark = {
                title: "Web Worker Benchmark",
                techUsed: ["JavaScript", "HTML", "CSS"],
                location: UCI,
                date: "Fall 2017",
                details: [
                    "Benchmarked the limits/potential of web workers across different browsers",
                    "Created a RSA encrypt/decrypt website using web workers",
                ]
            };
            let whoseChore = {
                title: "Whose Chore",
                techUsed: ["Ruby-On-Rails", "MySQL", "Heroku"],
                location: UCSD,
                date: "Spring 2016",
                details: [
                    "A web app that helped household assign who does what chore",
                    "Responsible to testing and QA",
                ]
            };
            let autoComplete = {
                title: "Auto-Complete",
                techUsed: ["C++"],
                location: UCSD,
                date: "Spring 2016",
                details: [
                    "A web app that helped household assign who does what chore",
                    "Responsible to testing and QA",
                ]
            };
            let fileCompDepressor = {
                title: "File Compressor Decompressor",
                techUsed: ["C++"],
                location: UCSD,
                date: "Spring 2016",
                details: [
                    "Implemented file compress/decompressor using Huffman coding algorithm"
                ]
            };

            if (this.isNetwork) {
                return [ wifiTcp, JEFS, othelloAi, webWorkerBenchmark, whoseChore ];
            }
            return [ JEFS, othelloAi, webWorkerBenchmark, wifiTcp, whoseChore ];
        }
    },
    methods: {
        toClass(title) {
            return title.toLowerCase().replace(/\ /g, "-");
        }
    }
};
</script>

<style lang="scss">
    /* Global Formatting */
    * {
        font-family: Verdana, Geneva, sans-serif;
        margin: 0;
        padding: 0;
    }

    h1 {
        font-size: 19px; /* 14 pt */
    }
    h2 {
        font-size: 15px; /* 11 pt */
    }
    h3 {
        font-size: 11px; /* 8 pt */
    }
    h1, h2, h3 {
        margin: 0;
        font-weight: normal;
    }
    th, td {
        text-align: left;
        padding: 0;
    }
    a:visited {
        color: rgb(0, 0, 238);
    }
</style>
<style lang="scss" scoped>
    /* Grid Formatting */
    .container {
        display: grid;
        grid-template-columns: 5fr 12fr;
        grid-template-rows: 100px 162px auto;
        grid-template-areas: 
            "header header"
            "personal-info main"
            "sidebar main";
        justify-content: start;
        width: 100vw;
        height: 100vh;

        > * {
            padding: 15px 10px 20px 15px
        }

        .network {
            display: none;
        }

        .header {
            grid-area: header;
            background-color: #2F5496; /* Navy Blue */
            border-bottom: 2px solid #2F5496;

            .name {
                font-size: 60px; /* 36 pt */
                color: white;
                text-align: center;
                font-family: Georgia;
                font-variant: small-caps;
            }
        }
        &[data-black-white="true"] .header {
            background-color: transparent;
            .name {
                color: #2F5496;
            }
        }
    }

    /* Personal Info */
    .personal-info{
        grid-area: personal-info;
    }
    .personal-info .title{
        color: #2F5496; /* Navy Blue */
    }
    .personal-info h2{
        font-size: 13px;
    }
    .personal-info tbody i.fa{
        padding-right: 6px;
    }

    /* Side Bar Formatting */
    .sidebar, 
    .personal-info {
        background-color: #E7E6E6; /* Grey */
        border-right: 2px solid #2F5496;
    }
    .container[data-black-white="true"] .sidebar,
    .container[data-black-white="true"] .personal-info {
        background-color: transparent;
    }
    .sidebar {
        grid-area: sidebar;
    }
    .sidebar .skill-set {
        margin-top: 12px;
    }
    .sidebar .title,
    .sidebar .level{
        color: #2F5496 /* Navy Blue */
    }
    .sidebar > .title {
        font-weight: bold;
    }
    .sidebar ul {
        margin: 0 5px 0 20px;
        padding: 0;
    }
    .sidebar li{
        font-size: 14px; /* 10.5 pt */
    }
    .sidebar .languages .level {
        float: right;
        padding-right: 3.5em;
    }
    /* Main Formatting */
    .main {
        grid-area: main;
        display: grid;
        grid-auto-columns: auto;
        grid-row-gap: 12px;
        grid-template-areas:
            "experience"
            "education"
            "projects"
    }
    .container[data-resume-type="network"] .main {
        grid-template-areas: 
            "education"
            "experience"
            "projects"
    }
    .main .experience {
        grid-area: experience;
    }
    .main .education {
        grid-area: education;
    }
    .main .projects {
        grid-area: projects
    }

    .main hr {
        border-top: 2px solid #2F5496;
        margin: 2px 0 0 0;
    }
    .main ul {
        margin: 0 0 0 20px;
        padding: 0;
    }
    .main li{
        font-size: 13px; /* 10 pt */
        font-weight: normal;
    }
    .main h1,
    .main .experience .job .title,
    .main .education .degree .title,
    .main .projects .project .title {
        color: #2F5496 /* Navy Blue */
    }
    
    .main .experience .job,
    .main .education .degree {
        padding-top: 12px;
    }
    
    .main .experience .job,
    .main .education .degree{
        display: grid;
        grid-auto-columns: auto 8rem;
        grid-template-areas: 
            "title duration"
            "location location"
            "details details";
        width: 100%;
    }
    .main .experience .job .duration,
    .main .education .degree .duration{
        grid-area: duration;
        font-size: 12px; /* 9 pt */
    }
    .main .experience .job .title,
    .main .education .degree .title{
        grid-area: title;
        font-weight: bolder;
    }
    .main .experience .job .location,
    .main .education .degree .location{
        grid-area: location;
    }
    .main .location{
        font-size: 12px; /* 9 pt */
        font-style: italic;
    }
    .main .experience .job .details,
    .main .education .degree .details{
        grid-area: details;
    }

    .main .projects {
        display: grid;
        grid-auto-columns: 100%;
        grid-row-gap: 12px; /* TODO remove grid styling here */
    }
    .main .projects .project .title {
        font-weight: bold;
        font-size: 0.8rem;
    }
    .main .projects .project .tech-used {
        font-weight: normal;
    }
</style>

