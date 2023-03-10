<script>
import Navbar from './Navbar.svelte';
import Tareas from './Tareas.svelte';
</script>

<main class="fondo">
    <Navbar/>
    <Tareas/>
</main>

<style>
.fondo{
    background-image: url(../img/railroad-line-3121544_1920.jpg);
    height: 100vh;
    background-position: center;
    background-size: cover;
}

</style>