<template>
    <div class="container" style="max-width: 600px">
        <h2 class="text-center mt-5">Lista de tareas</h2>
        <div class="d-flex mt-5">
            <input type="text" v-model="tarea" placeholder="Ingresa nueva tarea" class="w-100 form-control" />
            <button class="btn btn-success rounded-0 border border-warning" @click="submittarea">Agregar</button>
        </div>

        <table class="table table-bordered mt-5">
            <thead>
                <tr>
                    <th scope="col" class="text-center">Tarea</th>
                    <th scope="col" class="text-center">Hecho</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(tarea, index) in tareas" :key="index">
                    <td>
                        <span>{{ tarea.name }}</span>
                    </td>
                    <td class="text-center bg-dark text-light">
                        <div @click="eliminartarea(index)">
                            <span class="fa fa-trash pointer">Eliminar</span>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: "trabajoProps",
    props: {
        msg: String,
    },

    data() {
        return {
            editartarea: null,

            tareas: [
                {
                    name: "Pagar cuenta internet",
                },
                {
                    name: "Ir al supermercado",
                },
                {
                    name: "Comprar pan",
                },
                {
                    name: "Pagar Netflix",
                },
            ],
        };
    },

    methods: {

        eliminartarea(index) {
            this.tareas.splice(index, 1);
        },

        submittarea() {
            if (this.tarea.length === 0) return;

            if (this.editartarea != null) {
                this.tareas[this.editartarea].name = this.tarea;
                this.editartarea = null;
            } else {
                this.tareas.push({
                    name: this.tarea,
                });
            }

            this.tarea = "";
        },
    },
};
</script>