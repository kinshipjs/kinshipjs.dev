<script context="module">
    import { writable } from "svelte/store";

    export let appShellScrollY = writable(0);
    /** @type {import("svelte/store").Writable<{link: string, label: string}[]>}*/
    export let breadcrumbs = writable([]);
</script>

<script>
	import MyORMSidebarRight from '$lib/components/sidebars/MyORMSidebarRight.svelte';
	import MyORMSidebarLeft from '$lib/components/sidebars/MyORMSidebarLeft.svelte';
    import { autoModeWatcher, modeCurrent, LightSwitch } from '@skeletonlabs/skeleton';
    import { AppBar, AppShell } from "@skeletonlabs/skeleton";
    import { page } from "$app/stores";
    import { onMount } from 'svelte';
    import '../theme.postcss';
    import '@skeletonlabs/skeleton/styles/skeleton.css';
    import '../app.postcss';

    const allowedLeftSidebarPages = [
        "/docs"
    ];

    /**
     * @param {Event} e
     */
    function handleScroll(e) {
        // @ts-ignore
        $appShellScrollY = e.currentTarget.scrollTop;
    }

    $: slotSidebarLeft = $page.url.pathname.startsWith("/docs") ? `sm:w-0 md:w-60 sticky overflow-y-scroll min-h-full variant-filled-secondary` : "w-0"
    $: slotSidebarRight = $page.url.pathname.startsWith("/docs/reference") ? `sm:w-0 md:w-72 sticky overflow-y-scroll min-h-full variant-filled-secondary` : "w-0"
</script>

<svelte:head>{@html `<script>${autoModeWatcher.toString()} autoModeWatcher();</script>`}</svelte:head>

<AppShell on:scroll={handleScroll} 
    {slotSidebarRight}
    {slotSidebarLeft}>
    <svelte:fragment slot="header">
        <AppBar shadow="shadow-xl">
            <svelte:fragment slot="lead">
                <a href="/">
                    <div class="d-flex flex">
                        <img alt="kinship-logo" src="https://raw.githubusercontent.com/kinshipjs/branding/fd20339ab90b4c7ef1be4521d6bdd3bf030f37d5/kinship-logo-title-only.png" width=192 height=192>
                        <img alt="kinship-logo" src="https://raw.githubusercontent.com/kinshipjs/branding/fd20339ab90b4c7ef1be4521d6bdd3bf030f37d5/kinship-logo-db-only.png" width=64 height=64>
                    </div>
                </a>
            </svelte:fragment>
            <svelte:fragment slot="trail">
                <a href="/docs">
                    Documentation
                </a>
                <a href="https://www.github.com/@kinshipjs/core">
                    <img alt="github" src="{$modeCurrent ? "/github-mark.png" : "/github-mark-white.svg"}" width=32 height=32>
                </a>
                <LightSwitch/>
            </svelte:fragment>
        </AppBar>
    </svelte:fragment>
	<svelte:fragment slot="sidebarLeft">
        <MyORMSidebarLeft/>
    </svelte:fragment>
    <svelte:fragment slot="sidebarRight">
        <MyORMSidebarRight/>
    </svelte:fragment>
    <svelte:fragment>
        <AppShell>
            <svelte:fragment slot="header">
                <ol class="breadcrumbs">
                    {#each $breadcrumbs as crumb, i}
                        {#if (i+1) < $breadcrumbs.length}
                            <li class="crumb"><a class="anchor" href={crumb.link}>{crumb.label}</a></li>
                        {:else}
                            <li class="crumb">{crumb.label}</li>
                        {/if}
                    {/each}
                </ol>
            </svelte:fragment>
            <slot />
        </AppShell>
    </svelte:fragment>

	<svelte:fragment slot="pageFooter">Page Footer</svelte:fragment>
</AppShell>

<style>
</style>
