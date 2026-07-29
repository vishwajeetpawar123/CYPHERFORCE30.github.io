<script lang="ts">
    import { onMount } from "svelte";
    import gsap from "gsap";
    import { ScrollTrigger } from "gsap/dist/ScrollTrigger";

    let sectionRef: HTMLElement;

    const skills = [
        "SvelteKit", "Three.js", "TypeScript", "Tailwind CSS",
        "React", "Next.js", "Node.js", "Python",
        "WebGL", "GSAP", "Figma", "UI/UX Design"
    ];

    onMount(() => {
        const items = gsap.utils.toArray(".skill-card");

        gsap.fromTo(items,
            { opacity: 0, y: 30, scale: 0.9 },
            {
                opacity: 1,
                y: 0,
                scale: 1,
                duration: 0.6,
                stagger: 0.05,
                ease: "back.out(1.7)",
                scrollTrigger: {
                    trigger: sectionRef,
                    start: "top 75%"
                }
            }
        );
    });
</script>

<section
    bind:this={sectionRef}
    class="min-h-[60vh] flex flex-col justify-center bg-black text-white px-4 md:px-20 py-20 relative overflow-hidden"
>
    <div class="relative z-10 w-full max-w-6xl mx-auto text-center md:text-left">
        <h2 class="text-xs font-mono text-fuchsia-500 tracking-[0.5em] uppercase mb-4">
            Tech Arsenal
        </h2>
        <h3 class="text-3xl md:text-5xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-white to-gray-500 mb-12">
            Skills Matrix
        </h3>

        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4 md:gap-8">
            {#each skills as skill}
                <div class="skill-card bg-gray-900/80 backdrop-blur-sm border border-fuchsia-500/30 p-4 md:p-6 rounded-xl flex items-center justify-center text-center cursor-pointer transition-all hover:-translate-y-2 hover:border-cyan-400 hover:shadow-[0_0_20px_rgba(6,182,212,0.4)] group">
                    <span class="text-gray-300 font-mono text-sm md:text-lg group-hover:text-cyan-300 transition-colors">
                        {skill}
                    </span>
                </div>
            {/each}
        </div>
    </div>
</section>
