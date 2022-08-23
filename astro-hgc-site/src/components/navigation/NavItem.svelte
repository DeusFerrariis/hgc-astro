<script lang='ts'>
import type { NavItem } from './navigation.svelte'

export let navItem: NavItem;
export let color = 'white';
export let glow: boolean = false;

$: glowClass = glow ? ' glow' : ''
</script>

<li
    class={`n-item expand${glowClass}`}
    style={`--n-item-color: ${color}`}>
    <a
        class={`n-item expand${glowClass}`}
        href={navItem.path}
        style={`--n-item-color: ${color}`}>
        {navItem.title}
    </a>
</li>

<style>
    li.n-item {
        list-style-type: none;
        font-weight: bold;
        color: var(--n-item-color);
    }

    a.n-item {
        text-decoration: none;
        color: var(--n-item-color);
    }

    .n-item, .n-item:hover {
        transition: all .2s ease-in-out;
    }

    .n-item.expand:hover {
        transform: scale(1.15);
    }

    .n-item.glow:hover {
        text-shadow: 0 0 4px white;
    }
</style>