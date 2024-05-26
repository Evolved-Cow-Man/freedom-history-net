<script lang="ts">
    let is_start = false;

    let hour = 0;
    let minute = 0;
    let second = 0;

    function pad(num:number, size:number): string {
    let s = num+"";
    while (s.length < size) s = "0" + s;
    return s;
    }

    let hour_display = pad(hour, 2);
    let minute_display = pad(minute, 2);
    let second_display = pad(second, 2);

    function update_display() {
        hour_display = pad(hour, 2);
        minute_display = pad(minute, 2);
        second_display = pad(second, 2);
    }

    function mod_hour(time: number) {
        let hour_check = hour + time;
        if (hour_check <= 23 && hour_check >= 0) {
            hour += time;
        }
        update_display()
    }

    function mod_minute(time: number) {
        let minute_check = minute + time;
        if (minute_check <= 59 && minute_check >= 0) {
            minute += time;
        }
        update_display()
    }

    function mod_second(time: number) {
        let second_check = second + time;
        if (second_check <= 59 && second_check >= 0) {
            second += time;
        }
        update_display()
    }

    let set_hour = hour;
    let set_minute = minute;
    let set_second = second;

    function start() {
        console.log("start");
        is_start = true;
        set_hour = hour;
        set_minute = minute;
        set_second = second;
    }

    function stop() {
        console.log("stop");
        is_start = false;
    }

    function reset() {
        console.log("reset");
        if (hour == set_hour && minute == set_minute && second == set_second) {
            is_start = false
        }
        hour = set_hour;
        minute = set_minute;
        second = set_second;
        update_display()
    }

    function zero_reset() {
        console.log("zero reset");
        is_start = false;
        hour = 0;
        minute = 0;
        second = 0;
        update_display()
    }

    setInterval(() => {
        if (is_start != true) {
            return;
        }

        if (hour == 0 && minute == 0 && second == 0) {
            let audio = new Audio("/audio/4-tone-westminster-chime.m4a");
            audio.play();
            reset();
            return;
        }

        if (second > 0) {
            second -= 1;
        } else if (minute > 0) {
            minute -= 1;
            second = 59;
        } else if (hour > 0) {
            hour -= 1;
            minute = 59;
            second = 59;
        }
        update_display()
    }, 1000);
</script>

<hgroup>
    <h1 style="max-width: fit-content; margin-left: auto; margin-right: auto;"><a data-sveltekit-reload href="/">↩</a> Timer</h1>
    <p style="max-width: fit-content; margin-left: auto; margin-right: auto;">An auto-resetting timer.</p>
</hgroup>

<article id="article">
    <p style="margin-bottom: 0px" class="grid">
        <h1 style="max-width: fit-content; margin-left: auto; margin-right: auto; margin-top: 20px; font-size:1000%;">{hour_display}:{minute_display}:{second_display}</h1>
</article>

<div style="width: 60%; margin-left: auto; margin-right: auto; margin-bottom: 20px; display: flex">
    <div style="margin-left: 20px; margin-right: 20px; width: 100%;">
        <button on:click={start} style="width:100%;" class="contrast">Start</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%;">
        <button on:click={stop} style="width:100%;">Stop</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%;">
        <button on:click={reset} on:dblclick={zero_reset} style="width:100%;" class="secondary" >Reset</button>
    </div>
</div>

<hr>

<div style="width: 60%; margin-left: auto; margin-right: auto; margin-bottom: 20px; display: flex">
    <div style="margin: 0 20px; width: 100%; display: flex;">
        <p style="margin: 0; text-align: center; width: 100%;">Hour</p>
    </div>
    <div style="margin: 0 20px; width: 100%; display: flex;">
        <p style="margin: 0; text-align: center; width: 100%;">Minute</p>
    </div>
    <div style="margin: 0 20px; width: 100%; display: flex;">
        <p style="margin: 0; text-align: center; width: 100%;">Second</p>
    </div>
</div>

<div style="width: 60%; margin-left: auto; margin-right: auto; margin-bottom: 20px; display: flex">
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_hour(1)} style="width:100%;" class="contrast">+1</button>
        <button on:click={() => mod_hour(-1)} style="width:100%;">-1</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_minute(1)} style="width:100%;" class="contrast">+1</button>
        <button on:click={() => mod_minute(-1)} style="width:100%;">-1</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_second(1)} style="width:100%;" class="contrast">+1</button>
        <button on:click={() => mod_second(-1)} style="width:100%;">-1</button>
    </div>
</div>

<div style="width: 60%; margin-left: auto; margin-right: auto; margin-bottom: 20px; display: flex">
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_hour(5)} style="width:100%;" class="contrast">+5</button>
        <button on:click={() => mod_hour(-5)} style="width:100%;">-5</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_minute(5)} style="width:100%;" class="contrast">+5</button>
        <button on:click={() => mod_minute(-5)} style="width:100%;">-5</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_second(5)} style="width:100%;" class="contrast">+5</button>
        <button on:click={() => mod_second(-5)} style="width:100%;">-5</button>
    </div>
</div>

<div style="width: 60%; margin-left: auto; margin-right: auto; margin-bottom: 20px; display: flex">
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_hour(15)} style="width:100%;" class="contrast">+15</button>
        <button on:click={() => mod_hour(-15)} style="width:100%;">-15</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_minute(15)} style="width:100%;" class="contrast">+15</button>
        <button on:click={() => mod_minute(-15)} style="width:100%;">-15</button>
    </div>
    <div style="margin-left: 20px; margin-right: 20px; width: 100%; display: flex;">
        <button on:click={() => mod_second(15)} style="width:100%;" class="contrast">+15</button>
        <button on:click={() => mod_second(-15)} style="width:100%;">-15</button>
    </div>
</div>

<p style="max-width: fit-content; margin-left: auto; margin-right: auto;">Hint: Double-click 'Reset' to zero reset.</p>
