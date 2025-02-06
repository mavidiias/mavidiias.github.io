<script>
	import Oracao from '$lib/components/Oracao.svelte';
	import { oracoes } from '$lib/oracoes.js';
    let busca = '';
	let filtrados = $state(oracoes.slice());

	function pesquisarsanto(event) {
		//para cada filme da minha lista de filmes
		console.log('oi');
		filtrados = [];
		for (const item of oracoes) {
			//  se o filme conter o texto do campo de busca
			if (item.title.toLowerCase().includes(busca.toLowerCase())) {
				//    adicionar o filme na lista de filtrados
				filtrados.push(item);
			}
		}
	}
	
</script>
<input bind:value={busca} class="" placeholder="Filtrar..." />
<button onclick={pesquisarsanto}>🔎</button>

<div class="cor">
	<div class="row g-4">
		{#each filtrados as card}
			<div class="col">
				<Oracao {...card} />
			</div>
		{/each}
	</div>
</div>

<style>
	.cor {
		background-color: rgb(202, 202, 255);
	}
</style>
