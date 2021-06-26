<script context="module">
    import { readable } from 'svelte/store'

    export const breakpoint = readable(3, (set)=>{
        const breakpoints = [
            { value: 0, mediaquery: window.matchMedia("(max-width:  479px)") },
            { value: 1, mediaquery: window.matchMedia("(min-width:  480px) and (max-width:  719px)") },
            { value: 2, mediaquery: window.matchMedia("(min-width:  720px) and (max-width:  959px)") },
            { value: 3, mediaquery: window.matchMedia("(min-width:  960px) and (max-width: 1439px)") },
            { value: 4, mediaquery: window.matchMedia("(min-width: 1440px) and (max-width: 1919px)") },
            { value: 5, mediaquery: window.matchMedia("(min-width: 1920px)") },
        ];

        for (let key in breakpoints) {
            let breakpoint = breakpoints[key];

            //set the current breakpoint
            if (breakpoint.mediaquery.matches === true) {
                // EventBus.$emit("breakpoint", breakpoint.value);
                set(breakpoint.value)
            }
            breakpoint.mediaquery.addEventListener('change',(event) => {
                if (event.matches === true) {
                    // EventBus.$emit("breakpoint", breakpoint.value);
                    set(breakpoint.value)
                }
            });
        }
    });
</script>
