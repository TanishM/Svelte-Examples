<script>
    import Title from "$lib/Title.svelte";

    //conditional rendering
    let clicked = false;
    function handleClicked() {
        clicked = !clicked;
    }

    //each blocks
    let fruits = ['apple', 'banana', 'grape', 'orange'];

    //reactive state: first show without reactive, then with reactive
    let count = 0;
    $: doubled = count * 2;

    //input binding, no example for dropdown
    let name = '';
    let boxChecked = true;

</script>




<main>
    <!-- flexbox -->
    <div class='parent'>
        <p>Hello</p>
        <p>World</p>
    </div>

    <!-- conditional rendering -->
    <button on:click={handleClicked}>Conditionally Rendered</button>
        {#if clicked}
            <p>Button was clicked!</p>
        {/if}
  
    <!-- each blocks -->
    <ul>
        <p>List of fruits:</p>
        {#each fruits as fruit}
            <li>{fruit}</li>
        {/each}
        
        <!-- use to show index, and then put i+1 into li so t -->
        <!-- {#each fruits as fruit, i}
            <li>{i}. {fruit}</li>
        {/each} -->
    </ul>    

    <!-- reactive state  -->
    <button on:click={() => count += 1}>Reactive counter: {count}</button>
    <p>doubled: {doubled}</p>

    <!-- input binding  -->
    <!-- text input, add conditional rendering after initially explaining  -->
    <input bind:value={name} placeholder="Enter your name" />
    {#if name}
        <p>Hey {name}!</p>
    {/if}
    <br>
    <!-- checkbox, first time seeing {:else} -->
    <label> 
        <input type='checkbox' bind:checked={boxChecked} />
        Check me
    </label>
    {#if boxChecked}
        <p>Box is checked!</p>
    {:else}
        <p>Box is not checked!</p>
    {/if}

    <!-- Title -->
    <Title titleText="Our First Component"/>
</main>

<style>
    /*flexbox*/
    .parent {
        /* display: flex; */
        /* justify-content: space-between; */
        /* justify-content: center;  */
    }


</style>