<template>
    <div class="flex mb-8 p-8 rounded-lg w-full bg-white shadow-md">
        <div class="w-full md:w-5/12 rounded-lg bg-gray-600">

        </div>
        <div class="flex-grow pl-8">
            <h2 class="mb-4 text-3xl font-bold text-gray-800">
                Repository name
            </h2>
            <p class="mb-10 text-base font-normal text-gray-600">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Suscipit in inventore nulla nostrum enim perspiciatis, est hic saepe consectetur. Odio quis molestiae consequatur pariatur sapiente cum eaque natus voluptatum autem. Eligendi repellendus aspernatur sed quis sunt ipsum nostrum suscipit voluptates.
            </p>
            <div class="mb-4">
                <div class="inline-block p-2 px-4 rounded-md border border-gray-600 bg-gray-200 text-sm">
                    <span>Stars: </span>
                    <span>22 k</span>
                </div>
            </div>
            <div class="text-sm text-gray-600">
                {{ `Submitted on 23/10/2100 by @fadfasdf` }}
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'FeedCard'
    }
</script>