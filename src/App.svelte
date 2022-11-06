<script>
    import ButtonGroup from "./lib/components/ButtonGroup.svelte";
    import { tweened } from "svelte/motion";
    import Timer from "./lib/components/Timer.svelte";

    let original = 1 * 60;
    let timer = tweened(original);

    // ------ dont need to modify code below
    setInterval(() => {
        if ($timer > 0) $timer--;
    }, 1000);

    $: minutes = Math.floor($timer / 60);
    $: seconds = Math.floor($timer - minutes * 60);
</script>

<main class="bg-[#1E2240] min-h-screen w-full text-slate-100 text-center flex justify-center">
    <div class="max-w-lg space-y-10">
        <h1 class="text-3xl pt-10">pomodoro</h1>
        <ButtonGroup />
        <progress value={$timer / original} />
        <Timer time={`${minutes}:${seconds.toString().padStart(2, "0")}`} />
    </div>
</main>
