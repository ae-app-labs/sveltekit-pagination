<script lang="ts">
    import { page } from '$app/stores';

    export let data;

    let pageSize = 10;
    $: totalItems = data.products.total
    $: totalPages = Math.ceil(totalItems / pageSize)
    $: currentPage = (Number($page.params.page) -1);
</script>

<h3>Products</h3>
{#each data.products.products as poduct}
    <p>{poduct.id} - {poduct.title}</p>
{/each}

<div class="pagination">
    {#each Array(totalPages) as _, index}
         <a href="/products/{ index + 1}"
         class={currentPage === index ? 'text-blue' : ''}>
            {index + 1}
        </a>
    {/each}
</div>

