<script>
	import Rodape from '../Rodape.svelte';

	const tarefas = $state([]);
	let tarefaNova = $state();
	let tarefaEditandoIndice = $state();
	let tarefaEditando = $state();

	function adicionarTarefa() {
		tarefas.push(tarefaNova);
		tarefaNova = '';
	}

	function excluirTarefa(i) {
		tarefas.splice(i, 1);
	}

	function editarTarefa(i) {
		tarefaEditandoIndice = i;
		tarefaEditando = tarefas[i];
	}

	function salvarTarefa(i) {
		tarefas[i] = tarefaEditando;
		tarefaEditandoIndice = null;
	}

	function cancelarEdicao(i) {
		tarefas[i] = tarefas[i];
		tarefaEditandoIndice = null;
	}
</script>

<div class="fundo text-center">
	<br> 
	<h1 class="titulo">Lista de Oarações🩵</h1>
	<br />
	<p>
		<input placeholder="Digite a tarefa..." bind:value={tarefaNova} />
		<button style="background: #ADD8E6" onclick={adicionarTarefa}>➕</button>
	</p>
	<ul>
		{#each tarefas as tarefa, i}
			<li>
				{#if tarefaEditandoIndice == i}
					<input bind:value={tarefaEditando} />
					<button style="background: #ADD8E6" onclick={() => salvarTarefa(i)}>✅</button>
					<button style="background: #ADD8E6" onclick={() => cancelarEdicao(i)}>❌</button>
				{:else}
					{tarefa}
					<button style="background: #ADD8E6" onclick={() => editarTarefa(i)}>✏</button>
					<button style="background: #ADD8E6" onclick={() => excluirTarefa(i)}>🗑</button>
				{/if}
			</li>
		{/each}
	</ul>
</div>

<svelte:head>
	<style>
		body {
			background-color: #dae5ec;
		}
	</style>
</svelte:head>

<style>
	.titulo {
		text-align: center;
		font-family: Lucida Handwriting;
		text-shadow: 5px 5px 5px rgba(0, 0, 0, 0.3);
	}

	.meio {
		text-align: center;
	}
</style>
