
<script>
import axios from 'axios';

export default {
    name: "AppMain",
    data() {
        return {
            projects: [],
        };
    },
    props: {
        msg: String,
    },
    created() {
        axios.get('http://127.0.0.1:8000/api/projects')
            .then(response => {
                console.log(response.data);

                this.projects = response.data.projects.data;
            }

            )
    },
};
</script>

<template>
    <main>
        <div>
            <h1>My projects</h1>
        </div>
        <div v-for="project in projects">
            <h2>
                Nome Progetto: {{ project.name }}
            </h2>
            <div>
                Descrizione Progetto: {{ project.description }}
            </div>
            <div>
                Link progetto: {{ project.link }}
            </div>
            <hr>
            <div>
                Categoria progetto: {{ project.category }}
            </div>
            <div>
                {{ project.type }}
            </div>
            <div>
                {{ project.technologies }}
            </div>
        </div>
    </main>
</template>

<style scoped></style>
