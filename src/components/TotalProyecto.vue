<template>
    <hr>
    <h3>
        <div class="row">
            <div class="col-6 my-3">
                 <!-- propiedades calculadas| computadas -->
                Total Proyectos: {{ numeroProyectos }}

            </div>
            <div class="col-6 text-end" >
                <button @click="limpiarData" class="btn btn-warning">Limpiar proyectos</button>
            </div>
        </div>
    </h3>
    <div class="table-responsive">
        <!-- el over nos sirve para pintar -->
        <table class="table table-dark table-hover">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Proyecto</th>
                    <th>Tipo</th>
                    <th>Urgente</th>
                    <th>Completado</th>
                    <th></th>
                </tr>
            </thead>

            <tbody>
                <tr v-for="(proyecto, index) in proyectos" :key="index">
                    <td>{{ index+1 }}</td>
                    <td> {{ proyecto.proyecto }} </td>
                    <td> {{ proyecto.tipo }} </td>
                    <!-- operador ternario -->
                    <td @click="cambiarEstado(proyecto, 'urgente')" :class="proyecto.urgente ? 'bg-success' : 'bg-danger'"> {{ proyecto.urgente ? "Si" : "No" }} </td>
                    <td @click="cambiarEstado(proyecto, 'completado')" :class="proyecto.completado ? 'bg-success' : 'bg-danger'"> {{ proyecto.completado ? "Completo" : "Incompleto" }} </td>
                    <td > <button  @click="deleteP(index)" class="btn btn-danger">Eliminar</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>


<script>
    export default{
        props: ['numeroProyectos','proyectos', 'cambiarEstado','limpiarData','deleteP'],
        
    };
</script>