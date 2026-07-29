<script lang="ts">
    import confetti from "canvas-confetti";

    function copyEmail() {
        navigator.clipboard.writeText("vishwajeet@example.com"); // Placeholder
        confetti({
            particleCount: 100,
            spread: 70,
            origin: { y: 0.6 },
            colors: ["#d946ef", "#06b6d4", "#f43f5e"],
        });
    }
</script>

<section
    class="min-h-[80vh] flex flex-col items-center justify-center bg-black text-white relative"
>
    <h2
        class="text-[10vw] font-bold leading-none tracking-tighter text-transparent bg-clip-text bg-gradient-to-b from-fuchsia-400 to-cyan-600 drop-shadow-[0_0_20px_rgba(217,70,239,0.8)] text-center select-none"
    >
        LET'S TALK
    </h2>

    <button
        class="mt-10 px-8 py-4 bg-transparent border-2 border-cyan-400 text-cyan-400 shadow-[0_0_15px_rgba(6,182,212,0.6)] hover:bg-cyan-400 hover:text-black hover:shadow-[0_0_30px_rgba(6,182,212,1)] transition-all font-bold uppercase tracking-widest rounded-full hover:scale-110 active:scale-95"
        on:click={copyEmail}
    >
        Copy Email
    </button>

    <div class="absolute bottom-10 text-gray-500 font-mono text-xs">
        System Status: ONLINE // Region: IND
    </div>
</section>
