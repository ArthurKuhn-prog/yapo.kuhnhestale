<template>
    <div>
        <div>
            <table>
                <thead>
                    <tr>
                        <th>title</th>
                        <th>description</th>
                        <th>thumbnail</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(project, index) in projects" :key="index">
                        <td>{{project.title}}</td>
                        <td>{{project.description}}</td>
                        <td v-if="project.thumbnail != null"><img :src="project.thumbnail.url"></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Projects',
    data(){
        return {
            projects: [],
        }
    },
    mounted(){
        this.getProjects();
    },
    methods:{
        getProjects(){
            axios.get(`http://localhost:8000/api/projects`).then(res => {
                this.projects = res.data.projects;
            });
        }
    }
}
</script>