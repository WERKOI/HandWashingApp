<script> //отвечает за создание функционала страницы
    import { createEventDispatcher } from "svelte"; 
    import ProgressBar from './ProgressBar.svelte'; //импортирует
    const totalSeconds = 20; //время таймера
    let secondLeft = totalSeconds;
    let isRunning = false;
    $: progress = ((totalSeconds - secondLeft)/ totalSeconds) * 100; //прогресс
    const dispatch = createEventDispatcher();
    function startTimer() { //функция,запускающая таймер нажатием
        isRunning = true;
        const timer = setInterval(() =>{ //готовый таймер
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
    margin: 0;/*внешний отступ со всех сторон*/ 
 }
 .start {
     background-color: rgb(154, 73, 73) ;/*цвет кнопки старт*/
     width: 100%;/*размер кнопки старт*/
     margin: 10px 0;
 } 
 .start[disabled] {
     background-color: rgb(194, 194, 194);
     cursor: not-allowed;
 } 
</style>   
<div bp="grid"><!--элемент разделения контента-->
    <h2 bp="offset-5@md 4@md 12@sm"><!--offset - выравнивает по центру экрана-->
        Seconds Left:{secondLeft}</h2><!--h2 заголовок-->
</div>
<ProgressBar {progress} /><!--Вызов ProgressBar.svelte-->

<div bp="grid">

<button disabled={isRunning} 
on:click={startTimer} 
bp="offset-5@md 4@md 12@sm" 
class="start">
Start
</button><!--кнопка старт-->

</div>