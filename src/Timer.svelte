<!-- отвечает за создание функционала страницы -->
<script>
    //импортируем
    import { createEventDispatcher } from "svelte"; 
    import ProgressBar from './ProgressBar.svelte'; 

    //время таймера
    const totalSeconds = 20;

    let secondLeft = totalSeconds;
    let isRunning = false;

    //прогресс
    $: progress = ((totalSeconds - secondLeft)/ totalSeconds) * 100; 
    const dispatch = createEventDispatcher();
    
    //функция,запускающая таймер нажатием
    function startTimer() { 
        isRunning = true;

    //готовый таймер
    const timer = setInterval(() =>{ 
        secondLeft -= 1;
        if (secondLeft == 0) {
          clearInterval(timer); 
          isRunning =false;
          secondLeft = totalSeconds;
          dispatch("end");  
        }
    }, 1000)
    }
    

</script>
<style>
 h2 {
    /*внешний отступ со всех сторон*/
    margin: 0; 
 }
 .start {
     /*цвет кнопки старт*/
     background-color: rgb(154, 73, 73);
     /*размер кнопки старт*/
     width: 100%;
     margin: 10px 0;
 } 
 .start[disabled] {
     background-color: rgb(194, 194, 194);
     cursor: not-allowed;
 } 
</style>  
<!-- элемент разделения контента --> 
<div bp="grid">
    <!-- h2 заголовок -->
    <!-- offset - выравнивает по центру экрана -->
    <h2 bp="offset-5@md 4@md 12@sm">
        Seconds Left:{secondLeft}</h2>
</div>

<!-- Вызов ProgressBar.svelte -->
<ProgressBar {progress} />

<div bp="grid">
<!--кнопка старт-->
<button disabled={isRunning} 
on:click={startTimer} 
bp="offset-5@md 4@md 12@sm" 
class="start">
Start
</button>

</div>