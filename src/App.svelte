<script>
	let subtitle = "父母会より";
	let title = "さん";
	let nameString = `かまど　たんじろう
かまど　ねずこ
あがつま　ぜんいつ
はしびら　いのすけ
つゆり　かなを
しなずがわ　げんや
とみおか　ぎゆう
うずい　てんげん
ときとう　むいちろう
こちょう　しのぶ
いぐろ　おばない
ひめじま　ぎょうめい
しなずがわ　さねみ
うぶやしき　かがや
うぶやしき　きりや
かんざき　あおい
かんろじ　みつり
うろこだき　さこんじ`;
	let names = nameString.split('\n');
	let animals = [
		'cat',
		'crow',
		'dog',
		'dove',
		'dragon',
		'fish',
		'hippo',
		'horse',
		'kiwi-bird',
		'otter',
		'paw',
		'shrimp'
	];

	function color(i, darker=false){
		return `hsl(${i*(360/(names.length+1))} ${darker? "50% 40%" : "70% 50%"})`;
	}
</script>

<h1>カラフル名前タグ</h1>
<div>
	Ctrl + P で以下枠線のA4用紙サイズの印刷が可能です。
</div>
<div class=page>
	<div class=container>
		{#each names as name, i}
			<div class=item style:border-color={color(i)}>
				<div class=sub-title>{ subtitle }</div>
				<div class=name>
					<i class="fa-solid fa-{animals[i%animals.length]}" style:color={color(i, true)}></i>
					<span>{name}</span>
					<span>{title}</span>
				</div>	
			</div>
		{/each}
	</div>
</div>

<style>
	:global(body){
		width:210mm;
		margin:auto;
	}
	.page{
		border:1px solid lightgrey;
		margin:12px 0 0 0;
	}
	.container{
		display:flex;
		justify-content: middle;
		align-items:center;
		flex-direction:column;
		flex-wrap:wrap;		
		width: 205mm;
    	height: 290mm;
	}
	.item{
		margin:15px 0;
		width:350px;
		height:70px;
		font-size:1.6em;
		font-weight:600;
		border-radius:35px;
		border-width:10px;
		border-style: solid;
	}
	.item > .sub-title{
		margin:3px 0 -3px 50px;
		font-size:.5em;
	}
	.item > .name{
		display:flex;
		justify-content:center;
		align-items:center;
	}
	.item > .name > i{
		margin-right:9px;
	}
	.item > .name > span:last-child{
		display:inline-block;
		margin-left:6px;
		font-size:.75em;
		font-weight:400;
	}

	@media print {
		*:not(.page, .page *) {
			display:none;
		}
		.page{
			border:none;
		}
	}
</style>

<svelte:head>
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</svelte:head>