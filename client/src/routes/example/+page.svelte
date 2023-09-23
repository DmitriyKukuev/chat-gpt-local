<script lang="ts">
    let list = [
        {
            id: 1,
            name: 'todo 1',
            checked: false,
        },
        {
            id: 2,
            name: 'todo 2',
            checked: false,
        },
    ];

    let newItem = '';

    function addItem() {
        if (!newItem) return;

        const newId = (list.at(-1)?.id ?? 0) + 1;

        list.push({
            id: newId,
            name: newItem,
            checked: false,
        })

        newItem = '';

        list = list;
    }
</script>

<div>
    <h1>example</h1>

    <ul>
        {#each list as item (item.id)}
            <li>
                <span>{item.name}</span>
                <span>
                    {item.checked ? 'done' : 'incomplete'}
                </span>
                <button on:click={() => item.checked = !item.checked}>
                    {item.checked ? 'check' : 'uncheck'}
                </button>
            </li>
        {/each}
    </ul>

    <input type="text" bind:value={newItem}>
    <button on:click={addItem}>
        add item
    </button>
</div>
