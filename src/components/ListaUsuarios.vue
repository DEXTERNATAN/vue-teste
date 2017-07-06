<template>
    <div class="container">
        <Alert v-if="alert" v-bind:message="alert"></Alert>
        <h1 class="page-header">Gerenciamento de usuários</h1>
        <input class="form-control" placeholder="Enter Last Name" v-model="SearchFilter">
        <br>
        <div class="col-lg-12">
            <div class="panel panel-default">
                <table class="table table-striped">
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
                                <router-link class="btn btn-success" v-bind:to="'/detalhe/'+us.id">
                                    <i class="fa fa-plus-circle"></i>
                                    </i>
                                </router-link>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
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