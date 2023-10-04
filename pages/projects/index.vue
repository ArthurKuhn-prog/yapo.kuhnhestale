<script setup lang="ts">
    const { data: projects } = await useFetch('http://localhost:8000/api/projects')
</script>

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
