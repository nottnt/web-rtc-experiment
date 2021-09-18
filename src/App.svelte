<script>
	import adapter from 'webrtc-adapter';
	import VideoRecord from './VideoRecord.svelte'

	const userAgent = navigator.userAgent;
	const detectOpenWebOnLineApp = () => {
		const userAgentSplitToArr = userAgent.split(' ');
		const userAgentSplitToArrLast = userAgentSplitToArr[userAgentSplitToArr.length - 1]

		return userAgentSplitToArrLast.includes('Line')
	}

	if (window.location.href.includes('?openExternalBrowser=1')) {
		window.location.href = window.location.href.replace('/?openExternalBrowser=1', '');
	}

	export const getCurrentWebOpen = () => {
		return detectOpenWebOnLineApp() ? 'Line Application' : 'Itself';
	}

	export let name;
	$: adapter
</script>
<link rel="stylesheet" href="main.css" />

<header>
	WebRTC Experiment🧪
</header>
<main>
	<div class="flex-container">
		<div class="row"> 
			<VideoRecord />
			<div class="div-table">
				<div class="div-table-row">
					<div class="div-table-col header" align="center">Browser</div>
					<div class="div-table-col header">Version</div>
					<div class="div-table-col header">Run On</div>
				</div>
				<div class="div-table-row">
					<div class="div-table-col">{adapter.browserDetails.browser}</div>
					<div class="div-table-col">{adapter.browserDetails.version}</div>
					<div class="div-table-col">{getCurrentWebOpen()}</div>
				</div>
			</div>
		</div>
	</div>
</main>

<footer>
	Copyright © 2021 Nottnt. 
	<img src="/sad-cat.png" alt="Girl in a jacket" width="25" height="25">
</footer>