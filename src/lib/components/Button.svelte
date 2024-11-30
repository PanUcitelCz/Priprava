<script>
	// Typové argumenty pro props
	let { href, color, children } = $props();

	let buttonClass = $derived(`${color} button`);
</script>

<a {href} class={buttonClass}>
	{@render children()}
</a>

<style>
    .button{
        width: 90px;
        height: 50px;
        padding: 15px;
        text-align: center;
        text-decoration:  none;
        font-weight: 500;
        font-family: Arial, Helvetica, sans-serif;
        border-radius: 10px;
        transition: ease .3s;
    }

    .blue{
        background-color: blue;
        color: white;
    }

    .green{
        background-color: green;
        color: white;
    }

    .blue:hover, .green:hover{
        color: black;
        background-color: white;
        border: 1px solid black;
    }

</style>