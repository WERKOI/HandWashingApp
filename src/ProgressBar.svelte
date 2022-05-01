<script>
    export let progress = 0;   
</script>

<style>
    /* задаём стиль классу */
    .progress-container {
        /* определяем отступ */
        margin: 20px 0;
        /* определяем границы */
        border: solid rgb(194, 194, 194) 1px;
    }
    /* задаём стиль классу */
    .progress-bar {
        /* определяем высоту */
        height: 30px; 
        /* определить задний свет */
        background-color: rgb(77, 199, 55);
    }
</style>

<div bp="grid">
    <!-- контейнер, создаём класс progress-container -->
    <div bp="offset-5@md 4@md 12@sm" class="progress-container">
    <!-- контейнер, создаём класс progress-bar -->
    <div class="progress-bar" style="width: {progress}%"></div>
    <!-- строковой контейнер, создаём класс -->
    <span class="sr-only">%{progress}</span>
    </div>  
</div>