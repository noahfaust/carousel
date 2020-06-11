<script>
    import Carousel from './Carousel.svelte'

    let uuid = 1

	export let items = [
        {
            id: uuid++,
            title: 'Order 1',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 2',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 3',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 4',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 5',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 6',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 7',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 8',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 9',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 10',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 11',
            status: 'In Progress',
        },
        {
            id: uuid++,
            title: 'Order 12',
            status: 'In Progress',
        },
    ]
</script>

<main>
	<Carousel {items} />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>