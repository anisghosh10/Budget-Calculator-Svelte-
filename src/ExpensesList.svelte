<script>
    import SectionTitle from './Title.svelte'
    import Expense from './Expense.svelte'
    export let expenses = [];
    import {fly} from "svelte/transition";
    import {flip} from "svelte/animate";
</script>

<style>
    h2{
        text-transform: capitalize;
    }
</style>

<section>
    <SectionTitle title="expense list" />
    <ul>
        {#each expenses as expense,index (expense.id)}  <!-- this expense.id helps to set the value to a unique id during retrieval so that the specific item gets deleted or inserted and the animation is for that item only-->
        <div in:fly={{x:200,delay:(index+1) * 500}} out:fly={{x:-200}} animate:flip>
            <Expense {...expense}/>
        </div>
            {:else}
            <h2>no expenses added to the list</h2>
        {/each}
    </ul>
</section>