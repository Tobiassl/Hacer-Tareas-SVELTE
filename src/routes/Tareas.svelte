<script>
    let tareas = [];
    let nombreTarea = '';

    function agregarTarea(event){
        if(event.key === 'Enter'){

            const tarea = {
                nombre: nombreTarea,
                estado: false
            }
            tareas.push(tarea);
            console.log(tareas);
            tareas = tareas;
            nombreTarea = '';
        }
    }

    function deleteTarea(i){
        tareas.splice(i, 1);
        tareas = tareas;
    }

    function actualizarTarea(tarea, i){
        tareas[i].estado = !tarea.estado
    }
</script>

<div>
   <div class="container mt-5">
       <div class="row">
           <div class="col-lg-8 offset-lg-2">
            <input placeholder="Ingrese una tarea..." class="input" name="text" type="text"
                    on:keydown={agregarTarea}
                    bind:value={nombreTarea}    
                    >
              <br>
            </div>
           
           <div class="col-lg-6 offset-lg-3">
               {#if tareas.length === 0}
               <div class="card p-2">
                   <h6>No hay tareas para mostrar</h6>
               </div>
               {/if}

               <ul class="list-group">
                {#each tareas as tarea, i}
                   <li class="list-group-item d-flex justify-content-between">
                       <span class={tarea.estado === true ? 'text-success cursor' : 'cursor'} on:click={() => actualizarTarea(tarea, i)}>
                           <i class={tarea.estado === true ? 'fa-sharp fa-regular fa-circle-check' : 'far fa-circle'} ></i>
                       </span>
                        <h5>{ tarea.nombre }</h5>
                        <span class="cursor text-danger" on:click={() => deleteTarea(i)}>
                            <i class="fas fa-trash-alt"></i>
                        </span>
                   </li>
                   {/each}
               </ul>
           </div>
       </div>
   </div>
</div>

<style>
    .list-group{
        margin: 20px;
    }

    .card {
        margin: 20px;
    }

    .input {
        margin: 0 auto;
        text-align: center;
        justify-content: center;
        font-size: 1.8rem;
        background-color: #212121;
        width: 850px;
        height: 50px;
        padding: 10px;
        border: 2px solid white;
        border-radius: 5px;
    }
    .input:focus {
        color: rgb(0, 255, 255);
        background-color: #212121;
        outline-color: rgb(0, 255, 255);
        box-shadow: -3px -3px 15px rgb(0, 255, 255);
        transition: .1s;
        transition-property: box-shadow;
}
    

    .cursor {
        cursor: pointer;
    }
</style>