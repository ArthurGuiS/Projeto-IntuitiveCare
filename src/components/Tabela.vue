<template>
    <div class="container">
        <div>
            <h2 class="titulo">Relação de Operadoras Ativas ANS</h2>
        </div>
        <div>
            <label for="pesquisa">Barra de pesquisa: </label>
            <input id="pesquisa" type="text" v-model="search" placeholder="Pesquise aqui...">
        </div>
    </div>
    <table>
        <thead>
            <tr>
                <th>#</th>
                <th>Registro ANS</th>
                <th>CNPJ</th>
                <th>Razão Social</th>
                <th>Nome Fantasia</th>
                <th>Modalidade</th>
                <th>Logradouro</th>
                <th>Número</th>
                <th>Complemento</th>
                <th>Bairro</th>
                <th>Cidade</th>
                <th>UF</th>
                <th>CEP</th>
                <th>DDD</th>
                <th>Telefone</th>
                <th>Fax</th>
                <th>Endereço eletrônico</th>
                <th>Representante</th>
                <th>Cargo Representante</th>
                <th>Data Registro ANS</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(user, index) in filtrar" :key="index">
                <th>{{index + 1}}</th>
                <td>{{user.registro}}</td>
                <td>{{user.cnpj}}</td>
                <td>{{user.razaoSocial}}</td>
                <td>{{user.nomeFantasia}}</td>
                <td>{{user.modalidade}}</td>
                <td>{{user.logradouro}}</td>
                <td>{{user.numero}}</td>
                <td>{{user.complemento}}</td>
                <td>{{user.bairro}}</td>
                <td>{{user.cidade}}</td>
                <td>{{user.uf}}</td>
                <td>{{user.cep}}</td>
                <td>{{user.ddd}}</td>
                <td>{{user.telefone}}</td>
                <td>{{user.fax}}</td>
                <td>{{user.enderecoEletronico}}</td>
                <td>{{user.representante}}</td>
                <td>{{user.cargoRepresentante}}</td>
                <td>{{user.dataRegistro}}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: 'Tabela',
    data(){
        return {
            users: [],
            search: ''
        }
    },
    mounted: function() {
        const x = require('../assets/csvjson.json')
        this.users = x
    },
    computed: {
        filtrar() {
            const aux = this.search.toLowerCase()
            if(this.search === "") {
                return this.users
            }
            return this.users.filter( (user) => {
                return Object.values(user).some( (word) => 
                    String(word).toLowerCase().includes(aux)
                )
            })
        }
    }
}
</script>

<style scoped>
    .container {
        display: flex;
        align-items: center;
        padding: .8rem 1rem;
    }

    .titulo {
        color: blue;
        margin-right: 3rem;
    }

    #pesquisa {
        padding: .5rem 2rem;
        font-size: 1rem;
    }

    label {
        font-size: 1rem;
    }

    table {
        font-size: 1rem;
        border-spacing: 0;
    }

    td, th {
    border: 1px solid black;
    padding: 3px 5px;
    }


</style>