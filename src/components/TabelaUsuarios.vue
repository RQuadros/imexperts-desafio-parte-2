<template>
  <b-container fluid class="align-center">
    <div v-if="usuarios.length">
        <b-row>
            <b-table 
                striped
                borderless
                :items="usuarios"
                :fields="campos"
                tbody-tr-class="position-relative"
                class="mt-4 shadow-sm position-relative"
                >
                    <template v-slot:head()="data">
                        <span class="font-weight-normal small">{{ data.label.toUpperCase() }}</span>
                    </template>
                    <template v-slot:cell(status)="data">
                        <span class="text-success text-uppercase">{{ data.value }}</span>
                    </template>
                    <template v-slot:cell(checkbox-selecao)>
                        <b-form-checkbox></b-form-checkbox>
                    </template>
                    <template v-slot:cell(acoes)="row">
                        <b-button size="sm" @click="mostrarMenuAcoesUsuario(row)" @blur="esconderMenuAcoesUsuario(row)" class="bg-transparent border-0">
                            <b-icon class="d-inline-block" icon="three-dots" style="color: #666;"></b-icon>
                        </b-button>
                        <b-button-group class="mr-5 text-right position-absolute right-0">
                            <b-button class="bg-transparent border-0 p-0">
                                <span class="d-none">Deletar</span>
                                <b-icon class="d-inline-block mx-3" icon="trash-fill" style="color: #666; height: 19; width: auto"></b-icon>   
                            </b-button>
                            <b-button class="bg-transparent border-0 p-0">
                                <span class="d-none">Arquivar</span>
                                <b-icon class="d-inline-block mx-3" icon="archive-fill" style="color: #666; height: 19; width: auto"></b-icon>   
                            </b-button>
                            <b-button class="bg-transparent border-0 p-0">
                                <span class="d-none">Segurança</span>
                                <b-icon class="d-inline-block mx-3" icon="shield-shaded" style="color: #666; height: 19; width: auto"></b-icon>   
                            </b-button>
                            <b-button class="bg-transparent border-0 p-0">
                                <span class="d-none">Editar</span>
                                <b-icon class="d-inline-block mx-3" icon="pencil" style="color: #666; height: 19; width: auto"></b-icon>   
                            </b-button>
                        </b-button-group>
                    </template>
            </b-table>
        </b-row>
        <b-row class="d-flex justify-content-center">
            <b-pagination
                class="mt-3 paginacao-customizada"
                align="center"
                v-model="paginaAtual"
                :per-page="itensPorPagina"
                :total-rows="linhas"
                first-text="Primeiro"
                prev-text="Anterior"
                next-text="Próximo"
                last-text="Último"
            ></b-pagination>
        </b-row>
    </div>
    <div v-else>
      <h5>Não há usuários ainda.</h5>
    </div>
  </b-container>
</template>

<script>
// import axios from "axios";
export default {
  data() {
    return {
        show: false,
        campos: [ 
            { key: 'checkbox-selecao', label: '', thClass: 'bg-white' },
            { key: 'usuario', label: 'Usuário', thClass: 'bg-white' },
            { key: 'email', thClass: 'bg-white' },
            { key: 'data inclusão', class: 'text-center', label: 'Data de Inclusão', thClass: 'bg-white' },
            { key: 'data alteração', class: 'text-center', label: 'Data de Alteração', thClass: 'bg-white' },
            { key: 'regras', class: 'text-center', thClass: 'bg-white' },
            { key: 'status', class: 'text-center', thClass: 'bg-white' },
            { key: 'acoes', class: 'text-center', label: 'Ações', thClass: 'bg-white' }
        ],
        usuarios: [
        { "usuario": "ANPINA", "email": "antonio.pina@tvglobo.com.br", "data inclusão": "20/04/2020", "data alteração": "20/04/2020", "regras": "01", "status": "ativo" },
        { "usuario": "CCHANG", "email": "ciro.chang@tvglobo.com.br", "data inclusão": "20/04/2020", "data alteração": "20/04/2020", "regras": "01", "status": "ativo" },
        { "usuario": "TMARCAL", "email": "thiago.marcal@tvglobo.com.br", "data inclusão": "20/04/2020", "data alteração": "20/04/2020", "regras": "01", "status": "ativo" },
        { "usuario": "ECGIANN", "email": "ecgiannotto@tvglobo.com.br", "data inclusão": "20/04/2020", "data alteração": "20/04/2020", "regras": "01", "status": "ativo" },
        { "usuario": "YFERNAND", "email": "yuri.vasquez@tvglobo.com.br", "data inclusão": "20/04/2020", "data alteração": "20/04/2020", "regras": "02", "status": "ativo" },
        { "usuario": "PLACERDA", "email": "pedro.soares.lacerda@tvglobo.com.br", "data inclusão": "20/04/2020", "data alteração": "20/04/2020", "regras": "02", "status": "ativo" }
        ],
        linhas: 10,
        itensPorPagina: 10,
        paginaAtual: 1,
        numeroLinhaSelecionada: null
    };
  },
  mounted() {
    // axios
    //   .get("url_da_api")
    //   .then(response => {
    //     this.usuarios = response.data;
    //   })
    //   .catch(err => {
    //     console.log(err);
    //   });
  },
  methods: {
    mostrarMenuAcoesUsuario(row) {                         
        const linha = document.querySelector("table tbody").children[row.index];
        linha.classList.add("mostrando-menu");
    },
    esconderMenuAcoesUsuario(row) {                         
        const linha = document.querySelector("table tbody").children[row.index];
        linha.classList.remove("mostrando-menu");
    }
  }
};
</script>

<style>
    tbody td:last-child {
        position:relative;
    }
    tbody td:last-child .btn-group {
        display: none;
        top: 0;
        right: 0;
        height: 100%;
    }
    .mostrando-menu td:last-child .btn-group {
        display: inline-flex;
    }
    .mostrando-menu {
        background: #fff!important;
    }
    .mostrando-menu > td:not(:last-child),
    .mostrando-menu > td:last-child > button {
        opacity: 0.15!important;
    }
    .paginacao-customizada > li {
        margin-left: 6px;
        margin-right: 6px;
    }
    .paginacao-customizada > li.disabled:first-child > span,
    .paginacao-customizada > li.disabled:nth-child(2) > span {
        background: #fff!important
    }
    .paginacao-customizada > li > button,
    .paginacao-customizada > li > span {
        padding: 16px!important;
        border-width: 2px!important;
        border-radius: 6px;
    }
    .paginacao-customizada > li.disabled > span {
        background-color: transparent!important;
        opacity: 0.5!important;
    }
    .paginacao-customizada-ativo > li.disabled > span {
        background-color: #fff!important;
    }
    .paginacao-customizada > li > span {
        border-color: #fff!important;
    }
    .paginacao-customizada > li.active > button.page-link {
        background-color: #D83467!important;
        border-color: #D83467!important;
        width: 56px!important;
    }
</style>