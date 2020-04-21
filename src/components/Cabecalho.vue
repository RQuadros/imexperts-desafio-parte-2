<template>
    <div>
        <b-navbar toggleable="lg" type="dark" class="pt-3 pb-3 px-5 bg-cinza shadow-sm">
            <b-container fluid class="px-0">
                <b-navbar-brand href="#" class="mr-4">
                <img src="logo-imexperts.jpg" alt="Imexperts" widht="200px" class="bg-blend">
                </b-navbar-brand>
                <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
                <b-collapse id="nav-collapse" is-nav class="d-flex justify-content-between">
                    <b-navbar-nav class="d-flex align-items-center">
                        <b-button
                            size="sm" 
                            class="p-3 shadow-sm my-sm-0 text-uppercase bg-white border-0" 
                            >
                                <b-icon class="d-inline" icon="shield-shaded" style="color: #666; height: 20px; width: auto;"></b-icon>
                        </b-button>
                        <b-button
                            size="sm" 
                            class="p-3 my-sm-0 text-uppercase bg-gradient border-0 mr-4" 
                            >
                                <b-icon class="d-inline" icon="person-fill" style="color: #fff; height: 20px; width: auto;"></b-icon>
                        </b-button>
                        <b-nav-form class="position-relative">
                            <b-form-input 
                                size="sm" 
                                class="border-top-0 border-left-0 border-right-0 rounded-0 border-bottom border-secondary bg-transparent py-4 font-italic" 
                                style="width: 300px; text-indent: 0"
                                placeholder="Pesquisar..."
                                ></b-form-input>
                                <b-icon class="d-inline-block position-absolute" icon="search" style="color: #666; height: 20px; width: auto; right: 0;"></b-icon>        
                        </b-nav-form>
                    </b-navbar-nav>
                    <b-navbar-nav class="d-flex align-items-center">
                        <b-button
                            size="sm" 
                            class="p-3 shadow-sm my-sm-0 mr-3 text-uppercase bg-white border-0"
                            v-b-toggle.menu-lateral
                            >
                            <b-icon class="d-inline" icon="list-check" style="color: #666; height: 20px; width: auto; margin-bottom: -3px"></b-icon>
                    </b-button>
                    <b-button
                        size="sm" 
                        class="ml-auto p-3 my-sm-0 mr-4 text-uppercase bg-botao border-0 d-flex align-items-center" 
                        >
                        <b-icon class="mr-2" icon="person-fill" style="color: #fff; height: 20px; width: auto;"></b-icon>
                        <span>Incluir Usuário</span>
                    </b-button>
                    <b-icon class="d-inline-block ml-4" icon="house-door-fill" style="color: #666; height: 20px; width: auto"></b-icon>
                    <b-icon class="d-inline-block ml-4" icon="gear-fill" style="color: #666; height: 20px; width: auto"></b-icon>
                    <b-icon class="d-inline-block ml-4" icon="power" style="color: #666; height: 20px; width: auto"></b-icon>
                    </b-navbar-nav>
                </b-collapse>
            </b-container>
        </b-navbar>
        <b-sidebar id="menu-lateral" aria-labelledby="sidebar-no-header-title" no-header right shadow backdrop width="33%" class="bg-cinza">
            <header class="text-uppercase bg-white p-4 font-weight-bold d-flex align-items-center shadow-sm">
                <b-icon class="d-inline" icon="list-check" style="color: #999; height: 28px; width: 28px;"></b-icon>
                <span id="sidebar-no-header-title" class="mb-1 ml-3 h5 font-weight-bold">Filtros</span>
                <b-button-close block v-b-toggle.menu-lateral class="ml-auto p-3 bg-white shadow-sm"></b-button-close>
            </header>
            <div class="px-4">
                <p class="font-italic my-5">Utilize os filtros abaixo para refinar os resultados da tabela, clique no botão APLICAR para salvar as alterações.</p>
                <b-dropdown id="dropdown-data-de-inclusao" variant="bg-transparent text-left p-0" class="w-100 border-bottom border-secondary" style="background-position: right!important">
                    <template v-slot:button-content>
                        <b-icon class="d-inline-block mr-3" icon="calendar" style="color: #999; height: 20px; width: auto"></b-icon>
                        <span class="text-uppercase text-left font-weight-bold py-4 d-inline-block texto-magenta" style="letter-spacing: 0.1px;">Todas as datas de inclusão</span>
                    </template>
                </b-dropdown>
                <b-dropdown id="dropdown-data-de-alteracao" variant="bg-transparent text-left p-0" class="w-100 border-bottom border-secondary" style="background-position: right!important">
                    <template v-slot:button-content>
                        <b-icon class="d-inline-block mr-3" icon="calendar" style="color: #999; height: 20px; width: auto"></b-icon>
                        <span class="text-uppercase text-left font-weight-bold py-4 d-inline-block texto-magenta" style="letter-spacing: 0.1px;">Todas as datas de alteração</span>
                    </template>
                </b-dropdown>
                <b-dropdown id="dropdown-ativos-e-inativos" variant="bg-transparent text-left p-0" class="w-100 border-bottom border-secondary" style="background-position: right!important">
                    <template v-slot:button-content>
                        <b-icon class="d-inline-block mr-3" icon="toggle-on" style="color: #999; height: 20px; width: auto"></b-icon>
                        <span class="text-uppercase text-left font-weight-bold py-4 d-inline-block texto-magenta" style="letter-spacing: 0.1px;">Ativos e inativos</span>
                    </template>                    
                </b-dropdown>
                <b-button disabled class="text-uppercase bg-transparent border mt-5 w-100 p-4 texto-magenta borda-magenta">Aplicar</b-button>
            </div>
        </b-sidebar>
    </div>
</template>
<script>
export default {
    data() {
        return {
        }
    },
  methods: {
  }
}    
</script>

<style scoped>
    img {
        width: 150px;
    }
    svg {
        cursor: pointer;
        height: 1.35em;
        width: auto;
    }
    .bg-blend {
        mix-blend-mode: multiply;
    }
    .texto-magenta,
    .texto-magenta:hover,
    .texto-magenta:disabled {
        color: #D83467;
    }
    .borda-magenta {
        border-color: #D83467!important;
    }
</style>

<style>
    .dropdown-toggle::after {
        position: absolute!important;
        right: 0!important;
        top: 50%;
    }
</style>