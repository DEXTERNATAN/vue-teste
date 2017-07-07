<template>
    <main>
        <div class="page-header">
            <div class="container">
                <div class="pull-right">
                    <router-link to="/novo" class="btn btn-primary">
                        <span class="fa fa-plus" aria-hidden="true"></span>
                        Novo Usuário
                    </router-link>
                </div>
                <h1 class="">Gerenciamento de usuários</h1>
            </div>
        </div>
        <div class="container">

            <Alert v-if="alert" v-bind:message="alert"></Alert>

            <div class="box">
                <div class="form-group">
                    <label for="search" class="sr-only">Pesquisar</label>
                    <input id="search" class="form-control" placeholder="Pesquisar usuário" v-model="SearchFilter">
                </div>
                <table class="table">
                    <thead>
                        <tr>
                            <th>Nome</th>
                            <th>Ações</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(us, index) in filterBy(usuarios, SearchFilter)" v-bind:key="index">
                            <td>{{us.nome}}</td>
                            <td class="is-icon">
                                <router-link     v-bind:to="'/detalhe/'+us.id" title="Visualizar">
                                    <i class="fa fa-eye" aria-hidden="true"></i>
                                    </i>
                                </router-link>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </main>
</template>
<script>

import axios from 'axios';
import Alert from '../components/Alert.vue'

export default {
    data: () => ({
        usuarios: [],
        errors: [],
        alert: '',
        SearchFilter: ''
    }),
    methods: {
        BuscaUsuario: function () {
            axios.get('http://localhost:3000/api/usuarios/')
                .then(response => {
                    this.usuarios = response.data;
                })
                .catch(e => {
                    this.errors.push(e)
                })
        },
        filterBy(list, value) {
            value = value.charAt(0).toUpperCase() + value.slice(1);
            return list.filter(function (usuario) {
                return usuario.nome.indexOf(value) > -1;
            });
        }
    },
    created: function () {
        if (this.$route.query.alert) {
            this.alert = this.$route.query.alert;
        }
        this.BuscaUsuario();
    },
    updated: function () {
        this.BuscaUsuario();
    },
    components: {
        Alert
    }
}
</script>
<style scoped>

</style>