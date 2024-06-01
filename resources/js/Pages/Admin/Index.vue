<script>
export default {
    name: 'ExamplePage',
    data() {
        return {
            dialog: false,
            form: {
                email: '',
                username: '',
                password: '',
            }
        }
    },
    mounted() {
        new DataTable('#example');
    },
    methods: {
        async onSubmit(){
            try {
                const resp = await axios.post('users', this.form);
                console.log(resp.data)
            } catch (error) {
                
            }
        }
    },
};
</script>

<template>
    <VContainer>
        <VRow>
            <VCol cols="12" class="my-14">
                <v-card>
                    <template v-slot:title>
                        <v-sheet class="title">
                            <h2>Usuarios</h2>
                            <v-btn color="secondary" @click="dialog = true">Agregar</v-btn>
                        </v-sheet>
                    </template>
                    <VRow>
                        <VCol cols="12" class="container">
                            <table id="example">
                                <thead>
                                    <tr>
                                        <th>Name</th>
                                        <th>Position</th>
                                        <th>Office</th>
                                        <th>Age</th>
                                        <th>Start date</th>
                                        <th>Salary</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>Tiger Nixon</td>
                                        <td>System Architect</td>
                                        <td>Edinburgh</td>
                                        <td>61</td>
                                        <td>2011-04-25</td>
                                        <td>$320,800</td>
                                    </tr>
                                </tbody>
                            </table>
                        </VCol>
                    </VRow>
                </v-card>
            </VCol>
        </VRow>
    </VContainer>
    <v-dialog v-model="dialog" width="auto">
        <v-card width="500" prepend-icon="mdi-update" title="Agregar usuario">
            <template v-slot:text>
                <form @submit.prevent="onSubmit()">
                    <v-col cols="12">
                        <v-text-field v-model="form.username" label="Username" required></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field v-model="form.email" label="Email" required></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field v-model="form.password" label="Password" required></v-text-field>
                    </v-col>
                    <v-col cols="12" class="options">
                        <v-btn color="error" @click="dialog = false">Cancelar</v-btn>
                        <v-btn color="primary" type="submit">Agregar</v-btn>
                    </v-col>
                </form>
            </template>
        </v-card>
    </v-dialog>
</template>

<style scoped>
.title {
    display: flex;
    justify-content: space-between;
}

.options {
    display: flex;
    justify-content: space-between;
}
.container{
    padding-left: 40px;
    padding-right: 40px;
    padding-top: 60px;
}
</style>