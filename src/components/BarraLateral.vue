<template>
    <header>
        <h1>
            <a href="https://github.com/nemesislima/pink-tracker" target="_blank">
                <img src="../assets/pd.png" alt="Gem da Pink Diamond">
            </a>
        </h1>
        <button class="button" @click="alterarTema">
            {{ textoBotao }} 
        </button>
    </header>
    
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent ({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data () {
        return {
            modoEscuroAtivo: false
        }
    },
    computed: {
        textoBotao () {
            if (this.modoEscuroAtivo) {
                return 'Desativar modo escuro'
            }
            return 'Ativar modo escuro'
        }
    },
    methods: {
        alterarTema () {
            this.modoEscuroAtivo = !this.modoEscuroAtivo,
            this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
        }
    }
})
</script>

<style scoped>
/* Todo o estilo do componente */
header {
    background: var(--bg-Lateral);
    width: 100%;
    height: 100vh;
    padding: 2rem;
    text-align: center;
}

header h1 {
    text-align: center;
}

header h1 a img {
    max-width: 40%;
}

a img:hover {
    transform: scale(1.2);
}

a img:active {
    transform: scale(1.3);
}

header button {
    background-color: var(--bg-Lateral-box);
    color: white;
    margin: 15px;
}

button:hover {
    color: white;
    transform: scale(1.1);
}

button:active {
    color: white;
    transform: scale(1.1);
}

button:focus {
    color: white;
    border-color: white;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>
