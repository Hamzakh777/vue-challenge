<template>
	<div class="container mx-auto mt-10">
        <div class="mb-20 py-4 flex flex-row justify-end">
            <div class="flex flex-shrink">
                <!-- <div
                    class="h-8 w-8 p-1 bg-dark-blue rounded-r-lg border border-dark-blue"
                >
                    <img src="/assets/icons/calendar.svg" >
                </div> -->
                <datepicker
                    class="h-6"
                >
                </datepicker>
            </div>
        </div>
        <TheFeed/>
    </div>
</template>

<script>
import Datepicker from 'vuejs-datepicker';
import TheFeed from './components/TheFeed';

export default {
	name: 'app',

	components: {
        Datepicker,
        TheFeed
    },

    data() {
        return {
            
        }
    },

    methods: {

    }
};
</script>

<style>
.vdp-datepicker input[type="text"] {
    padding: 0.5rem;
    height: 2rem;
    border: 1px solid #011627;
    border-top-left-radius: 0.5rem;
    border-bottom-left-radius: 0.5rem;
    border-radius: 0.5rem;
}
.vdp-datepicker input[type="text"]:focus {
    outline: none;
}
</style>
