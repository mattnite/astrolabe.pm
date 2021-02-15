<script>
	import { Router, Route, createHistory } from "svelte-navigator";
	import PackageList from "../components/PackageList.svelte";

	export let fetchData;

        async function filterTags(tag) {
                return (await fetchData).filter(_ => _.tags.includes(tag))
        }
</script>

<Route path=":tag" let:params>
	<div class="tag-page">
                <h2>#{params.tag}</h2>

                {#await filterTags(params.tag)}
                        <h1>Fetching Package...</h1>
                {:then packages}
                        <PackageList {packages} />
                {:catch error}
                        <p>Error: <code>{error}</code></p>
                {/await}
	</div>
</Route>

<style lang="scss">
	.tag-page {
		position: relative;
		padding: 20px;
	}

	h2 {
		margin: 0;
		font-size: 40pt;
	}

	h3 {
		font-weight: 300;
		font-size: 14pt;
	}

	p {
		font-size: 14pt;
	}
</style>
