<template>
	<div class="container mx-auto mt-10">
        <div class="mb-20 py-4 flex flex-row justify-end">
            <div class="flex flex-shrink">
                <div
                    class="h-8 w-8 p-1-1/2 mr-3"
                >
                    <img 

                        src="/assets/icons/calendar.svg" 
                    >
                </div>
                <datepicker
                    class="h-6 text-gray-800"
                    v-model="date"
                    :disabledDates="disabledDates"
                >
                </datepicker>
            </div>
        </div>
        <TheFeed
            :date="date"
        />
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
            date: new Date(),
            disabledDates: {
                from: new Date()
            }
        }
    },

    created() {
        // set the date to yesterday
        const today = new Date()
        const yesterday = new Date(today.setDate(today.getDate() - 1));

        this.date = yesterday;
        this.disabledDates.from = yesterday;
    },
};
</script>

<style>
.vdp-datepicker input[type="text"] {
    padding: 0.5rem;
    height: 2rem;
    border: 1px solid #011627;
    border-top-left-radius: 0.5rem;
    border-bottom-left-radius: 0.5rem;
    border-radius: 0.25rem;
}
.vdp-datepicker input[type="text"]:focus {
    outline: none;
}
</style>
