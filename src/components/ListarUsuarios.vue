<template>

    <div class="container listar-usuarios">
        <h1 class="text-center">Listagem de Usuários</h1>
        <table id="usuarios" class="table table-striped table-bordered">
            <thead class="thead-dark">
                <tr>
                    <th>Id</th>
                    <th>Nome</th>
                    <th>E-mail</th>
                    <th>Endereço</th>
                </tr>
            </thead>
            <tbody>

                <tr v-for="usuario in usuarios" :key="usuario.id">
                    <td>{{ usuario.id }}</td>
                    <td>{{ usuario.nome }}</td>
                    <td>{{ usuario.email }}</td>
                    <td>{{ usuario.endereco }}</td>
                </tr>

            </tbody>
        </table>
    </div>
</template>
<script>
import axios  from 'axios'

export default ({
    name: "ListarUsuarios",
    data(){
        return {
            usuarios:[]
        };
    },
    methods:{
        async listarUsuarios(){
            try{
                const response = await axios.get("https://localhost:7114/api/usuario/listar-usuarios");
                this.usuarios = response.data;
            }catch(error){
                console.error("Ocorreu um erro ao carregar os dados");
            }
        },
    },
    created(){
            this.listarUsuarios();
        }
})
</script>

<style scoped>

</style>