<script lang='ts'>
    $: menuVisible = false;
    $: menuClass = `nav-menu ${menuVisible ? 'visible' : 'hidden'}-transitory`
    $: menuButtonClass = `menu-btn${menuVisible ? ' navbar' : ''}`
</script>

<div class={menuClass}>
    I am a menu lol    
    <button
        on:click={() => {menuVisible = false}}
        class='menu-btn close-button'
        style='z-index: 2;'>
        Close
    </button>
</div>
<button
    on:click={() => {menuVisible = true}}
    class={menuButtonClass}
    style='z-index: 1;'>
    Menu
</button>

<div class='navbar'>
    I am a navbar lol
</div>

<style>
    button {
        border: none;
        border-radius: 0.4rem;
        font-size: 2rem;
        color: #8884FF;
        background-color: white;
        font-weight: bold;
        padding: 0.4rem;
        box-shadow: 5px 5px 15px 5px rgba(0,0,0,0.3);
        transition: all 0.2s ease-in-out;
        position: fixed;
        bottom: 0;
        right: 0;
        margin: 1rem;
    }

    button:hover {
        transform: scale(1.05);
        transition: all 0.2s ease-in-out;
    }

    .navbar {
        display: none;
    }

    .nav-menu {
        position: fixed;
        top: 0;
        left: 0;
        height: 100vh;
        width: 100vw;
        background-color: white;
        display: block;
    }

    .nav-menu-hidden {
        opacity: 0;
        visibility: hidden;
    }

    .hidden-transitory {
        opacity: 0;
        visibility: hidden;
        transition: all 0.4s ease-in-out;
    }

    .visible-transitory {
        opacity: 1;
        visibility: visible;
        transition: all 0.4s ease-in-out;
    }

    @media only screen and (min-width: 800px) {
        .navbar {
            display: block;
        }
        .nav-menu, .menu-btn {
            display: none;
        }
    }
</style>