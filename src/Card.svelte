<script>
	export let name;
	export let picture;
</script>

<div class="card" style="background:url({picture}) 50% 0%; background-size:cover">
	<span>{name}</span>
</div>

<style>
	.card{
		width: 200px;
		height: 200px;
		border-radius: 100%
	}
	span{
		position: relative;
		top:170px;
		background: #ccccccb3;
		margin:2px;
		border-radius: 2px;
	}

</style>