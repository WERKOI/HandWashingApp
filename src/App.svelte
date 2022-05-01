<!-- отвечает за создание функционала страницы -->
<script>
	// импорт файлов в App.svelte
	import Timer from './Timer.svelte';
	import HowTo from './HowTo.svelte';	

	//добавляем переменную
	let audio; 

	//функция запускает аудио
	function timerEnds(e){ 
		audio.play();
	}
</script>

<!-- заголовок -->
<h1>Handwashing App</h1>

<!-- отвечает за стиль страницы -->
<style>
	/*выравнивание по ширине*/
	h1, 
	h3 {
		/*выравнавание по центру*/
		text-align:center;
	}
</style>

<!-- вызов Timer.svelte -->
<Timer on:end={timerEnds}/>

<!-- вызов HowTo.svelte -->
<HowTo />

<!-- ссылки на ресурсы -->
<h3>
	<!-- обращение к ссылке href -->
	<a href="https://www.who.int/gpsc/clean_hands_protection/en/">
		Picture Source
	</a>

	<a href="https://freesound.org/people/metrostock99/sounds/345086/">
		Sound Source
	</a>
</h3>

<!-- добавляем звуковой контент -->
<audio bind:this={audio}>
	<!-- указывает медиа ресурсы -->
	<source src="public_sound.wav" />
</audio>
