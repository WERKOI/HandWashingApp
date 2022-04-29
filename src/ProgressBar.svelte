<script>
    export let progress = 0;   
</script>

<style>
    .progress-container {/*задаём стиль классу*/
        margin: 20px 0;/*определяем отступ*/
        border: solid rgb(194, 194, 194) 1px;/*определяем границы*/
    }
    .progress-bar {/*задаём стиль классу*/
        height: 30px; /*определяем высоту*/
        background-color: rgb(77, 199, 55);/*определить задний свет*/
    }
</style>

<div bp="grid">
    <div bp="offset-5@md 4@md 12@sm" class="progress-container"><!--контейнер, создаём класс progress-container-->
    <div class="progress-bar" style="width: {progress}%"></div><!--контейнер, создаём класс progress-bar-->
    <span class="sr-only">%{progress}</span><!--строковой контейнер, создаём класс-->
    </div>  
</div>