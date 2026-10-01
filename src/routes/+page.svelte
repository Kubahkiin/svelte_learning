<script lang="ts">
	import Header from './Header.svelte';


    let formState = $state({
        name: '',
        birthday: '',
        step: 0,
        error: ''
    });
</script>

<Header name={formState.name}/>

<main>
    <p>Step: {formState.step + 1}</p>

    {@render formStep({question: "What's your name",
        id: "name",
        type: "text"
    })}

    <p style="color:crimson;">{formState.error}</p>
</main>

{#snippet formStep({ question, id, type}: {
    type: string;
    id: string;
    question: string;
})}
    <article>
        <div>
            <label for={id}>{question}</label>
            <input {type} {id} bind:value={formState[id]}>
        </div>
    </article>

    
{/snippet}