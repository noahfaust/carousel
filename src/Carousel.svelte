<script>
    import { onMount } from 'svelte'
    import { quintOut } from 'svelte/easing'
    import { crossfade } from 'svelte/transition'
    import { flip } from 'svelte/animate';

    export let items

    let maxVisible = 3
    let firstSlide = 0
    let lastSlide = firstSlide + maxVisible

    const [send, receive] = crossfade({
		duration: 2000,

		fallback(node, params) {
            console.log('params', params)
			const transform = params.transition == 'in' ? 'translateX(-100%)' : 'translateX(100%)'

			return {
				duration: 1000,
				easing: quintOut,
				css: t => `
					transform: ${transform};
					opacity: 1
				`
			};
		}
    });
    
    const next = () => {

        firstSlide++
        lastSlide++
    }
    const prev = () => {
        firstSlide--
        lastSlide--
    }
    
</script>

<section>

    {#each items.slice(0, firstSlide) as item (item.id)}

        <div class='prev'
            in:receive={{key: item.id}}
            out:send={{key: item.id}}
            animate:flip={{duration: 1000}}
            >
            <h1>
                {item.title}
            </h1>
            <p>
                Status: {item.status}
            </p>
        </div>

    {/each}

    {#each items.slice(firstSlide, lastSlide) as item (item.id)}

        <div class='visible'
            in:receive={{key: item.id, transition: 'in'}}
            out:send={{key: item.id, transition: 'out'}}
            animate:flip={{duration: 1000}}
            >
            <h1>
                {item.title}
            </h1>
            <p>
                Status: {item.status}
            </p>
        </div>

    {/each}

    {#each items.slice(lastSlide) as item (item.id)}

        <div class='next'
            in:receive={{key: item.id, transition: 'in'}}
            out:send={{key: item.id, transition: 'out'}}
            animate:flip={{duration: 1000}}
            >
            <h1>
                {item.title}
            </h1>
            <p>
                Status: {item.status}
            </p>
        </div>

    {/each}

</section>

<button on:click={prev}>Previous</button>
<button on:click={next}>Next</button>

<style>

    section {
        display: flex;
        justify-content: center;
    }

    div.visible {
        background-color: #fff;
        border: 1px solid;
        opacity: 1;
        padding: 1rem 4rem;
        text-align: center;
        z-index: 200;
        transition: transform 2s, opacity 1s, z-index 2s;
    }

    div.prev {
        position: absolute;
        left: 0;
        opacity: 0;
        z-index: 100;
    }

    div.next {
        position: absolute;
        right: 0;
        opacity: 0;
        z-index: 100;
    }

</style>