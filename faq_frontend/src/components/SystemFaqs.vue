<template>
<div class="system-faqs">
    <div class="content-faqs">
        <div class="title-content-faqs">
            <h1>FAQ's</h1>
            <h2>Veja as principais dúvidas</h2>
        </div>
        <div class="content-input">
            <input type="text" v-model="search" placeholder="Pesquise por uma palavra chave">
        </div>
        <div class="content-buttons">
            <button :style="{ 'background-color': selectP ? 'var(--azul_claro)' : 'var(--branco)', 'color': 'var(--azul)'}" @click="prog">Programação</button>
            <button :style="{ 'background-color': selectS ? 'var(--azul_claro)' : 'var(--branco)', 'color': 'var(--azul)'}" @click="sal">Salário</button>
            <button :style="{ 'background-color': selectO ? 'var(--azul_claro)' : 'var(--branco)', 'color': 'var(--azul)'}" @click="outros">Outros</button>
        </div>
        <div class="content-form-faqs">
            <div class="cards" v-for="obj in faqsTipo" :key="obj.id">
               <span class="title-card">{{ obj.question }}?<button @click="showCard(obj.id)"><img src="../assets/add.png" alt=""></button></span>
               <span class="text-card" v-if="show && showID == obj.id">{{ obj.response }}</span>
            </div>
        </div>
     
    </div>
</div>
</template>

<script>
import axios from 'axios'
import { url } from "@/config/global"

export default {
    name: 'SystemFaqs',
    data: () => ({
        faqs: [],
        faqsTipo: [],
        selectP: false,
        selectS: false,
        selectO: false,
        show: false,
        showID: {},
        search: ''
    }),
    computed: {

    },
    methods: {
        async buscar() {
            await axios.get(`${url}/api/faqs`)
			.then((response) => {
                this.faqs.push(...response.data.data)
			}).catch((err)=>{
				console.log(err.message());
			}).finally(()=> console.log('Final'))
        },
        showCard(value){
            this.show = !this.show
            this.showID = value
        },
        prog(){
            this.selectP = !this.selectP
            this.selectO = false
            this.selectS = false
            if(this.selectP) {
                this.faqsTipo = this.faqs.filter((value) => value.type == 1).map((value) => { return value })
            } else {
                this.faqsTipo = this.faqs
            }
        },
        sal(){
            this.selectS = !this.selectS
            this.selectO = false
            this.selectP = false
            if(this.selectS) {
                this.faqsTipo = this.faqs.filter((value) => value.type == 2).map((value) => { return value })
            } else {
                this.faqsTipo = this.faqs
            }
        },
        outros(){
            this.selectO = !this.selectO
            this.selectP = false
            this.selectS = false
            if(this.selectO) {
                this.faqsTipo = this.faqs.filter((value) => value.type == 3).map((value) => { return value })
            } else {
                this.faqsTipo = this.faqs
            }
        },
        filterData(value){
            this.faqsTipo = this.faqs.filter( item => {
                return (
                    item.question.toLowerCase().includes(value.toLowerCase()) ||
                    item.response.toLowerCase().includes(value.toLowerCase())
                );
            });
        }

    },
    watch: {
        search: function(value) {
            this.filterData(value);
        }
    },
    mounted(){
        this.buscar()
        this.faqsTipo = this.faqs
    }

}
</script>

<style scoped>
.system-faqs {
    /* min-height: 100vh;
    min-width: 100vw; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 2rem;
    height: 100%;
    width: 100%;
}

.title-content-faqs{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: var(--branco);
    font-size: 1.8vw;
}

.title-content-faqs h1{
    margin-top: 5rem;
}
.title-content-faqs h2{
    font-weight: 100;
    color: var(--roxo_claro);
    text-align: center;
    font-size: 1vw;
}
.content-faqs{
    width: 75%;
    height: 100%;
    border-radius: 16px;
    background-color: var(--roxo_fundo);
}
.content-input{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 20vh;
}
.content-input input{
    border-radius: 30px;
    padding: 0.5rem 2rem;
    border: none;
    outline: none;
    width: 50%;
    height: 30%;
    font-size: 1.2vw;
}
.content-form-faqs {
    display: flex;
    /* justify-content: center; */
    margin: 2rem;
    flex-wrap: wrap;
}
.content-buttons{
    display: flex;
    justify-content: center;
    align-items: center;
}

.content-buttons button{
    padding: 0.8rem 1.8rem;
    border-radius: 10px;
    font-size: 1vw;
    color: var(--roxo_claro);
    margin: 30px 7px;
    border: none;
    outline: none;
}
.content-buttons button:hover{
    background-color: var(--azul_claro);
    cursor: pointer;
    color: var(--azul);

}
.cards {
    display: flex;
    flex-direction: column;
    width: 40%;
    padding: 30px;
    border-radius: 16px;
    background-color: var(--branco);
    flex-wrap: wrap;
    margin: 0.8rem;
}

.title-card{
    display: flex;
    color: var(--azul);
    width: 100%;
    font-size: 1.2vw;
    font-weight: 600;
    justify-content: space-between;
    align-items: flex-start;
}
.text-card{
    margin-top: 1rem;
}
.title-card button{
    background-color: var(--azul_claro);
    border-radius: 5px;
    border: none;
    outline: none;
    /* width: 10%;
    height: 10%; */
}
.title-card button:hover{
    background-color: var(--roxo_claro);
    cursor: pointer;
}

</style>
  