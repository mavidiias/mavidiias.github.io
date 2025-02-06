<script>
	import CartaMagic from '$lib/components/CartaMagic.svelte';
	import { cards } from '$lib/data.js';
    import { getContext } from 'svelte';
	
	let filtrados = $state(cards.slice());

    const busca = getContext('busca');
    $effect(() => {
		 console.log(busca()); 
		//  const termo=busca()
		// filtrados = [];
		// for (const item of cards) {
		// 	//  se o filme conter o texto do campo de busca
		// 	if (item.title.toLowerCase().includes(termo.toLowerCase())) {
		// 		//    adicionar o filme na lista de filtrados
		// 		filtrados.push(item);
		// 	}
		// }
	})

</script>

<div class="cor">
	<div class="row g-4">
		{#each filtrados as card}
			<div class="col">
				<CartaMagic {...card} />
			</div>
		{/each}
	</div>
</div>

<style>
	.cor {
		background-color: rgb(202, 202, 255);
	}
</style>
