<script>
    import { scrollTo } from "svelte-scrollto";
    import { MetaTags } from "svelte-meta-tags";
    import GithubSvg from "$lib/components/github-svg.svelte";
    import DownloadSvg from "$lib/components/download-svg.svelte";
    import DiscordSvg from "$lib/components/discord-svg.svelte";

    let url;

    const download = async () => {
        if (!url) {
            try {
                const response = await fetch("https://phoenixlauncher.github.io/phoenix/appcast.xml");
                const dataobject = await response.text();

                const parser = new DOMParser();
                const xmlDoc = parser.parseFromString(dataobject, "application/xml");

                const enclosureElement = xmlDoc.querySelector('enclosure');
                url = enclosureElement.getAttribute('url');
            } catch (error) {
                console.error(error);
            }
        }
        // Open the URL in a new tab
        window.open(url, '_blank');
    };
</script>

<MetaTags
  title="Phoenix"
  description="A beautiful macOS game launcher made with SwiftUI."
  openGraph={{
    url: 'https://www.phoenixlauncher.app',
    title: 'Phoenix',
    description: 'A beautiful macOS game launcher made with SwiftUI.',
    images: [
        {
            url: '/images/phoenix-banner.jpg',
            width: 128,
            height: 128,
            alt: 'Phoenix Icon'
        }
    ],
    site_name: 'Phoenix'
  }}
  twitter={{
    handle: '@diskutility',
    cardType: 'summary_large_image',
    title: 'Phoenix',
    description: 'A beautiful macOS game launcher made with SwiftUI.',
    image: '/images/phoenix-banner.jpg',
    imageAlt: 'Phoenix Icon'
  }}
/>

<div class="font-apple bg-white dark:bg-offdarkergray w-screen snap-y snap-mandatory flex flex-col overflow-y-scroll" id="main">
    <div class="w-screen h-screen bg-gradient-to-b from-orange-200 dark:from-orange-900 snap-start">
        <div class="h-[93vh] flex flex-col lg:flex-row justify-evenly items-center">
            <div class="justify-center p-16 flex">
                <img src="/images/phoenix-light-triple.webp" alt="" class="block dark:hidden w-[400px] lg:w-[50vw] drop-shadow-sm">
                <img src="/images/phoenix-dark-triple.webp" alt="" class="hidden dark:block w-[400px] lg:w-[50vw] drop-shadow-sm">
            </div>
            <div class="flex flex-col justify-center space-y-6">  
                <div class="space-y-3">
                    <h2 class="text-4xl lg:text-[2.5rem] leading-[45px] font-semibold text-center sm:text-left text-orange-600 w-96">A beautiful macOS game launcher</h2>
                    <p class="text-xl lg:text-[1.2rem] font-semibold text-center sm:text-left text-orange-600 w-96">Completely open source, built with SwiftUI, and optimized for macOS.</p>
                </div>
                <div class="flex flex-row space-x-2 items-start justify-center sm:justify-start">
                    <button class="rounded-full w-40 h-12 bg-orange-700 dark:bg-orange-500 inline-flex flex-row items-center justify-center space-x-3 fill-white dark:fill-darkergray" on:click={download}>
                        <DownloadSvg/>
                        <h1 class="text-[1rem] font-semibold text-center text-white dark:text-darkergray">
                            Download
                        </h1>
                    </button>
                    <button class="rounded-full w-12 h-12 bg-orange-700 dark:bg-orange-500 inline-flex flex-row items-center justify-center fill-white dark:fill-darkergray" on:click={() => {
                        window.open('https://github.com/PhoenixLauncher/Phoenix/')
                    }}>
                        <GithubSvg/>
                    </button>
                    <button class="rounded-full w-12 h-12 bg-orange-700 dark:bg-orange-500 inline-flex flex-row items-center justify-center fill-white dark:fill-darkergray" on:click={() => {
                        window.open('https://discord.gg/m8uvhDMzrK')
                    }}>
                        <DiscordSvg/>
                    </button>
                </div>
            </div>
        </div>
        <div class="w-screen flex justify-center items-center">
            <button class="bg-none items-center text-center flex flex-col fill-orange-600 text-orange-700 -translate-y-5" on:click={() => {scrollTo({element: "#page1"})}}>
                see more
                <svg xmlns="http://www.w3.org/2000/svg" class="w-8 h-8" viewBox="0 0 24 24"><path d="m12 16.175l3.9-3.875q.275-.275.688-.288t.712.288q.275.275.275.7t-.275.7l-4.6 4.6q-.15.15-.325.213t-.375.062q-.2 0-.375-.063T11.3 18.3l-4.6-4.6q-.275-.275-.288-.687T6.7 12.3q.275-.275.7-.275t.7.275l3.9 3.875Zm0-6L15.9 6.3q.275-.275.688-.287t.712.287q.275.275.275.7t-.275.7l-4.6 4.6q-.15.15-.325.213t-.375.062q-.2 0-.375-.062T11.3 12.3L6.7 7.7q-.275-.275-.288-.688T6.7 6.3q.275-.275.7-.275t.7.275l3.9 3.875Z"/></svg>
            </button>
        </div>
    </div>
    <div class="h-screen flex flex-col items-center justify-start snap-start relative" id="page1">
        <div class="h-[93vh] flex flex-col justify-center items-center p-10">  
            <div class="justify-center flex p-16">
                <img src="/images/phoenix-laptop.webp" alt="" class="block dark:hidden w-[400px] lg:w-[55vw] drop-shadow-4xl-orange">
                <img src="/images/phoenix-laptop-dark.webp" alt="" class="hidden dark:block w-[400px] lg:w-[55vw] drop-shadow-4xl-orange">
            </div>
            <h2 class="font-semibold tracking-tight text-center text-3xl md:text-4xl xl:text-5xl text-orange-600 w-[75vw]">
                Open source. Apple silicon native. Built with SwiftUI.
                <br/>
                What's not to like?
            </h2>
        </div>
        <div class="w-screen flex justify-center items-center">
            <button class="bg-none items-center text-center flex flex-col fill-orange-600 text-orange-700 -translate-y-5" on:click={() => {scrollTo({element: "#page2"})}}>
                see more
                <svg xmlns="http://www.w3.org/2000/svg" class="w-8 h-8" viewBox="0 0 24 24"><path d="m12 16.175l3.9-3.875q.275-.275.688-.288t.712.288q.275.275.275.7t-.275.7l-4.6 4.6q-.15.15-.325.213t-.375.062q-.2 0-.375-.063T11.3 18.3l-4.6-4.6q-.275-.275-.288-.687T6.7 12.3q.275-.275.7-.275t.7.275l3.9 3.875Zm0-6L15.9 6.3q.275-.275.688-.287t.712.287q.275.275.275.7t-.275.7l-4.6 4.6q-.15.15-.325.213t-.375.062q-.2 0-.375-.062T11.3 12.3L6.7 7.7q-.275-.275-.288-.688T6.7 6.3q.275-.275.7-.275t.7.275l3.9 3.875Z"/></svg>
            </button>
        </div>
    </div>
    <div class="h-screen items-center" id="page2">
        <div class="h-[93vh] flex flex-col-reverse lg:flex-row justify-evenly items-center">  
            <h2 class="font-semibold tracking-tight text-center lg:text-left text-4xl lg:text-5xl text-orange-600 w-[80vw] lg:w-auto">
                A lightweight and 
                <br/>
                beautiful macOS interface.
            </h2>
            <div class="justify-center flex p-16">
                <img src="/images/phoenix-side.webp" alt="" class="block dark:hidden w-[350px] lg:w-[45vw] drop-shadow-sm">
                <img src="/images/phoenix-side-dark.webp" alt="" class="hidden dark:block w-[350px] lg:w-[45vw] drop-shadow-sm">
            </div>
        </div>
        <div class="w-screen flex justify-center items-center">
            <button class="bg-none items-center text-center flex flex-col fill-orange-600 text-orange-700 -translate-y-5" on:click={() => {scrollTo({element: "#footer"})}}>
                download
                <svg xmlns="http://www.w3.org/2000/svg" class="w-8 h-8" viewBox="0 0 24 24"><path d="m12 16.175l3.9-3.875q.275-.275.688-.288t.712.288q.275.275.275.7t-.275.7l-4.6 4.6q-.15.15-.325.213t-.375.062q-.2 0-.375-.063T11.3 18.3l-4.6-4.6q-.275-.275-.288-.687T6.7 12.3q.275-.275.7-.275t.7.275l3.9 3.875Zm0-6L15.9 6.3q.275-.275.688-.287t.712.287q.275.275.275.7t-.275.7l-4.6 4.6q-.15.15-.325.213t-.375.062q-.2 0-.375-.062T11.3 12.3L6.7 7.7q-.275-.275-.288-.688T6.7 6.3q.275-.275.7-.275t.7.275l3.9 3.875Z"/></svg>
            </button>
        </div>
    </div>
    <div id="footer" class="h-[50vh] flex flex-col lg:flex-row justify-evenly items-center snap-start relative">
        <h2 class="font-semibold tracking-tight text-center lg:text-left text-3xl lg:text-4xl text-orange-600 p-32 w-[80vw] lg:w-auto">
            Download today
            or contribute on GitHub
        </h2>
        <div class="justify-center items-center inline-flex flex-row space-x-10 lg:space-x-20 -translate-y-10 lg:translate-y-0">
            <button class="rounded-full w-40 h-12 bg-orange-600 inline-flex flex-row items-center justify-center space-x-2 fill-white dark:fill-darkergray" on:click={download}>
                <DownloadSvg/>
                <h1 class="text-[1rem] font-semibold text-center text-white dark:text-darkergray">
                    Download
                </h1>
            </button>
            <button class="rounded-full w-40 h-12 bg-orange-600 inline-flex flex-row items-center justify-center space-x-2 fill-white dark:fill-darkergray" on:click={() => {
                window.open('https://github.com/PhoenixLauncher/Phoenix/')
            }}>
                <GithubSvg/>
                <h1 class="text-[1rem] font-semibold text-center text-white dark:text-darkergray">
                    Contribute
                </h1>
            </button>
        </div>
    </div>
</div>

<style>
    #main {
        -webkit-overflow-scrolling: touch;
    }
    * {
		box-sizing: border-box;
		margin: 0;
		padding: 0;
	}
</style>
