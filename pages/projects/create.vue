<template>
    <div>
        <Head>
            <Title>My App</Title>
            <Meta name="csrf-token" content="{{ csrf_token() }}"/>
        </Head>
        <form @submit.prevent="saveProject">
            <div>
                <label>Title</label>
                <input type="text" v-model="project.title"/>
            </div>
            
            <div>
                <label>Descriptione</label>
                <input type="text" v-model="project.description"/>
            </div>
            
            <div>
                <label>Thumbnail</label>
                <input type="text" v-model="project.thumbnail.url"/>
            </div>

            <div>
                <label>Content</label>
                <textarea v-model="project.content[0]"></textarea>
            </div>

            <div>
                <button type="submit" class="btn btn-primary">Save</button>
            </div>
        </form>
    </div>
</template>

<script>

export default{
    name:'Project create',
    data(){
        return {
            project:{
                title:'',
                description:'',
                thumbnail: {
                    url:'',
                },
                content:[]
            },
        }
    },
    methods: {
        async saveProject(){
            await $fetch('http://localhost:8000/api/projects',{
                method: POST,
                body: this.project
            })
        }
    }
}
</script>