<script>
        import marked from 'marked'

        const about = "# About" 
</script>

<div class="about-page">{@html marked(about)}</div>

<style lang="scss">
	.about-page {
		position: relative;

		padding: 20px;
	}
	
	h2 {
		margin: 0;

		font-size: 40pt;
	}
</style>
