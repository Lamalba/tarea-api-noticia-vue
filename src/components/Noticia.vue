<template>
    <div class="content">
        <h1 class="title">  {{ title }}</h1>
        <h2 class="resume">  {{ resume }}</h2>
        <div class="fa-ul" align="left">
            <li><i class="fas fa-briefcase"></i>  {{ matter }}</li>
            <li><i class="fas fa-calendar-week"></i>  {{ date }}</li>
        </div>
        <div v-if="photo">
            <img :src="'https://d2eb79appvasri.cloudfront.net/imagenes_noticias/' + photo" alt :id="photoAlt"/>
        </div>
        <div class="text" v-html="text"></div> 
    </div>
</template>


<script>
import axios from 'axios';

export default {
    name: 'Noticia',

    data() {
        return {
            all: '',
            title: '',
            resume: '',
            matter: '',
            date: '',
            photo: '',
            photoAlt: '',
            text: null,
            API: 'https://externo-smartlex-api-contenidos.iberley.es/',
            id: 'noticias/30547/{texto}',
            token: '?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6InRlc3QifQ.eyJ1c2VybmFtZSI6Im1jYXJiYWxsb0BpYmVybGV5LmVzIiwiaWQiOiI3MCIsImV4cCI6MTYxODk4NjI4NywiaWF0IjoxNjE4ODI0Mjg3LCJyb2xlcyI6WyJST0xFX1BSRU1JVU0iXSwibWF0IjoiUEUsQ0ksTUUsQURNLEZJLExBIiwiY29sIjoiQ0MsU1VCLExFLENWIiwiZ2MiOiIyIn0.mZ2TlHcpOTlmcsAnINTGJVTextxnWZm9nDk1bVWLWm5jfH0uHuC-uLMN9ruP9N-W0pg6hBY4CQ8iQZ01OXxragYqH-L0WP3M2f_LbVrcG-Bu0TPckU1Wi-ONw-PCU9XXnZzEt-YLHFTNGekPp60crvF5Jb-e3ramqCsrLV0m8l9VUU9tl-vR450x0YcNrJT44o67pvs0-fYBYlfgPWaVZg-pLhWsGrDKi0AVPgUx2g_2NdzavNEHc6wWhzZ90fN13Y2vH6UeQFx49PH237CfbZuBbGt50FxZjTKYBs4xyvYfuPY1ZbsiSciDCrkWZG-4gLRly9WY0CB2BGtJLwV4-FalxISonr9Y4Q286Bwj5MY3mFE6VYi13HffEnUXe47OcfbHnqGjf5VmMsAHBBM3eG5n7AZVbSKOX2esjTftDOgy4fCoPqdEzgElZtna57e5rNGMx8AKj65qX0inpQ949NbeJJD9k7e4MlHFEB1VyxRUZg1RafbESktYdk8S03GIKPLuch1cBjAlABP_BSryuK7ZfkvRpRyVMrzK4ELJbm6vLAcaLKIOVt8iW3DVSK6zJihuTCP_BmfX2kOXn1fLs94FKdW_d8haCIpP6AmNWNCDikAmJwXdNVhK96_JinBYUulaJj41DOf03trzA-LYAP92H-JDqs3sm94E2NCiDTY&_format=json'
        }
    },

    mounted() {
        this.getNew();
    },

    methods: {
        getNew() {
            axios.get(this.API + this.id + this.token)
            .then(response => {
                this.all = response.data,
                console.log(this.all),
                this.title = response.data.titulo,
                this.resume = response.data.seo_description,
                this.matter = response.data.materias[0].toUpperCase(),
                this.date = response.data.date,
                this.photo = response.data.imagencompleta,
                this.photoAlt = response.data.imagenalt,
                this.text = response.data.html
            })
            .catch(e => console.log(e))
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.content {
    margin: 2%;
    padding: 20px;
    color: #555555;
    font-family: 'Roboto', Arial, sans-serif;
}

.title {
    font-family: 'Majerit', serif;
    font-size: 2.5rem;
    color: black;
}

h2 {
    font-family: 'Majerit',serif;
    font-weight: 500;
    margin: 20px 0;
    line-height: 1.2;
}

.resume {
    font-style: italic;
    font-size: 16px;
    color: #565656;
    font-family: 16px 'Majerit', serif;
}

img {
    max-width: 100%;
    height: auto;
    margin-left: 20%;
    padding-bottom: 2%;
    padding-top: 2%;
}

body {
    font-family: 'Roboto', Arial, sans-serif;
    font-size: 15px;
    min-width: 270px;
    line-height: 1.42857;
    color: #555;
    font-weight: 400;
    overflow-x: hidden;
}

.fa-ul {
    padding: 10px;
}

.photo {
    padding: 10px;
}


a:hover {
    color: blueviolet;
}



@media (max-width: 500px) {
  img {
    position: relative;
    top: 13%;
    left: -5%;
    width: 70%;
  }
}

</style>