<script>//отвечает за создание функционала страницы
	import Timer from './Timer.svelte'; // импорт файлов в App.svelte
	import HowTo from './HowTo.svelte';	
	let audio; //добавляем переменную
	function timerEnds(e){ //функция запускает аудио
		audio.play();
	}
</script>

<h1>Handwashing App</h1><!--Заголовок-->

<style>/*отвечает за стиль страницы*/
	h1, 
	h3 {/*выравнивание по ширине*/
		text-align:center;/*выравнавание по центру*/
	}
</style>

<Timer on:end={timerEnds}/><!--Вызов Timer.svelte-->

<HowTo /><!--Вызов HowTo.svelte-->

<h3><!--ссылки на ресурсы-->
	<a href="https://www.who.int/gpsc/clean_hands_protection/en/"><!--обращение к ссылке href-->
		Picture Source
	</a>

	<a href="https://freesound.org/people/metrostock99/sounds/345086/">
		Sound Source
	</a>
</h3>

<audio bind:this={audio}><!--добавляем звуковой контент-->>
	<source src="public_sound.wav" /><!--указывает медиа ресурсы-->>
</audio>
