<script lang="ts">
    import { onMount } from "svelte";
    import gsap from "gsap";
    import { ScrollTrigger } from "gsap/dist/ScrollTrigger";

    let sectionRef: HTMLElement;

    const experiences = [
        {
            year: "2023 - Present",
            title: "Senior UI/UX Architect",
            company: "Cyber Systems",
            desc: "Leading design and implementation of next-gen digital interfaces."
        },
        {
            year: "2021 - 2023",
            title: "Creative Developer",
            company: "Neon Matrix Studio",
            desc: "Developed immersive 3D web experiences using WebGL and Three.js."
        },
        {
            year: "2019 - 2021",
            title: "Frontend Engineer",
            company: "Tech Frontier",
            desc: "Built scalable frontend architectures and responsive web apps."
        }
    ];

    onMount(() => {
        const items = gsap.utils.toArray(".exp-item");

        items.forEach((item: any, i) => {
            gsap.fromTo(item,
                { opacity: 0, x: -50 },
                {
                    opacity: 1,
                    x: 0,
                    duration: 0.8,
                    delay: i * 0.2,
                    ease: "power2.out",
                    scrollTrigger: {
                        trigger: sectionRef,
                        start: "top 70%"
                    }
                }
            );
        });
    });
</script>

<section
    bind:this={sectionRef}
    class="min-h-screen flex flex-col justify-center bg-gray-950 text-white px-4 md:px-20 py-20 relative overflow-hidden"
>
    <div class="relative z-10 w-full max-w-6xl mx-auto">
        <h2 class="text-xs font-mono text-fuchsia-500 tracking-[0.5em] uppercase mb-4">
            Career Timeline
        </h2>
        <h3 class="text-3xl md:text-5xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-white to-gray-500 mb-16">
            Experience Protocol
        </h3>

        <div class="flex flex-col gap-8 relative before:absolute before:inset-y-0 before:left-[15px] md:before:left-1/2 before:w-[2px] before:bg-gradient-to-b before:from-fuchsia-500/50 before:to-cyan-500/10">
            {#each experiences as exp, i}
                <div class="exp-item flex flex-col md:flex-row w-full relative z-10">
                    <div class="md:w-1/2 flex items-center md:justify-end pl-12 md:pl-0 md:pr-12 relative">
                        <!-- Timeline Dot -->
                        <div class="absolute left-0 md:left-auto md:-right-[6px] top-1/2 -translate-y-1/2 w-8 h-8 rounded-full bg-black border-2 border-fuchsia-500 flex items-center justify-center shadow-[0_0_15px_rgba(217,70,239,0.5)]">
                            <div class="w-3 h-3 rounded-full bg-cyan-400"></div>
                        </div>
                        <span class="text-fuchsia-400 font-mono text-xl md:text-2xl font-bold bg-black/50 px-4 py-2 rounded-lg border border-fuchsia-500/30">
                            {exp.year}
                        </span>
                    </div>
                    <div class="md:w-1/2 pl-12 mt-4 md:mt-0 flex flex-col justify-center">
                        <div class="bg-black/60 backdrop-blur-md border border-fuchsia-500/30 p-6 rounded-2xl shadow-[0_0_20px_rgba(217,70,239,0.15)] hover:border-fuchsia-500/80 hover:shadow-[0_0_25px_rgba(217,70,239,0.4)] transition-all">
                            <h4 class="text-2xl md:text-3xl font-bold mb-2 text-white">{exp.title}</h4>
                            <h5 class="text-cyan-400 text-lg mb-4 font-mono">{exp.company}</h5>
                            <p class="text-gray-400 text-base md:text-lg leading-relaxed">{exp.desc}</p>
                        </div>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>
