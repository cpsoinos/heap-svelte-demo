<script lang="ts">
	import Header from './Header.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<script type="text/javascript">
		(window.heapReadyCb = window.heapReadyCb || []),
			(window.heap = window.heap || []),
			(heap.load = function (e, t) {
				(window.heap.envId = e),
					(window.heap.clientConfig = t = t || {}),
					(window.heap.clientConfig.shouldFetchServerConfig = !1);
				var a = document.createElement('script');
				(a.type = 'text/javascript'),
					(a.async = !0),
					(a.src = 'https://cdn.us.heap-api.com/config/' + e + '/heap_config.js');
				var r = document.getElementsByTagName('script')[0];
				r.parentNode.insertBefore(a, r);
				var n = [
						'init',
						'startTracking',
						'stopTracking',
						'track',
						'resetIdentity',
						'identify',
						'getSessionId',
						'getUserId',
						'getIdentity',
						'addUserProperties',
						'addEventProperties',
						'removeEventProperty',
						'clearEventProperties',
						'addAccountProperties',
						'addAdapter',
						'addTransformer',
						'addTransformerFn',
						'onReady',
						'addPageviewProperties',
						'removePageviewProperty',
						'clearPageviewProperties',
						'trackPageview'
					],
					i = function (e) {
						return function () {
							var t = Array.prototype.slice.call(arguments, 0);
							window.heapReadyCb.push({
								name: e,
								fn: function () {
									heap[e] && heap[e].apply(heap, t);
								}
							});
						};
					};
				for (var p = 0; p < n.length; p++) heap[n[p]] = i(n[p]);
			});

		// const searchParams = new URLSearchParams(window.location.search);
		// const shouldCompressCookies = searchParams.get('compressCookies') === 'true';

		heap.load('660636389', {
			// compressCookies: shouldCompressCookies
		});
	</script>
</svelte:head>

<div class="app">
	<Header />

	<main>
		{@render children()}
	</main>

	<footer>
		<p>
			visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to learn about SvelteKit
		</p>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
