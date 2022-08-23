<script lang='ts'>
import type { NavItem as NItem } from "./navigation.svelte";
import NavItem from "./NavItem.svelte";

export let navItems: NItem[] = [];
export let backgroundColor: string = 'white';
$: menuVis = false;
$: visClass = `${menuVis ? 'visble' : 'hidden'}`
</script>

{#if menuVis}
    <div
        class={`modal menu${visClass}`}
        style={`--modal-bg: ${backgroundColor}`}>
        {#each navItems as nItem}
            <NavItem glow={true} navItem={nItem}/>
        {/each}
        <button
            class={`menu${visClass}`}
            on:click={() => {menuVis = false}}>
            Close
        </button>
    </div>
{:else}
    <button
        class={`menu${visClass}`}
        on:click={() => {menuVis = true}}>
        Menu
    </button>
{/if}

<style>
    div.modal {
        width: 100vw;
        height: 100vh;
        max-width: 100vw;
        max-height: 100vh;
        background-color: var(--modal-bg);
    }

    .menu {
        transition: all 0.2s ease-in-out;
    }

    button.menu {
        border: none;
        border-radius: 0.4rem;
        font-size: 2rem;
        color: #8884FF;
        background-color: white;
        font-weight: bold;
        padding: 0.4rem;
        box-shadow: 5px 5px 15px 5px rgba(0,0,0,0.3);
        position: fixed;
        bottom: 0;
        right: 0;
        margin: 1rem;
    }

    button.menu:hover {
        transform: scale(1.05);
    }

    .menu.visible {
        opacity: 0;
        visibility: hidden;
    }

    .menu.visible {
        opacity: 1;
        visibility: visible;
    }
</style>