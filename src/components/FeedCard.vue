<template>
    <div class="flex flex-col md:flex-row mb-8 p-8 rounded-lg w-full bg-gray-900 shadow-md">
        <div 
            class="w-full h-64 mb-6 md:h-auto md:w-72 md:mb-0 rounded-lg bg-gray-600 bg-center bg-cover"
            :style="`background-image: url(${repo.owner.avatar_url})`"
        >
        </div>
        <div class="flex-grow md:pl-8">
            <h2 
                class="mb-2 text-3xl font-bold text-white"
            >
                {{ repo.name }}
            </h2>
            <p class="mb-10 text-base font-normal text-gray-600">
                {{ repo.description }}
            </p>
            <div class="mb-4">
                <div class="inline-block p-2 px-4 rounded-md border border-gray-200 bg-gray-600 text-sm">
                    <span>Stars </span>
                    <span>{{ repo.stargazers_count }}</span>
                </div>
                <div class="inline-block ml-6 p-2 px-4 rounded-md border border-red-200 bg-red-500 text-sm">
                    <span>Issues </span>
                    <span>{{ repo.open_issues_count }}</span>
                </div>
            </div>
            <div class="text-sm text-gray-600">
                {{ `Submitted on ${createAt} by` }}
                <a 
                    :href="repo.owner.html_url"
                    class="hover:text-teal"
                    target="_blank"
                >
                    {{ `@${repo.owner.login}` }}
                </a>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'FeedCard',

        props: {
            repo: {
                type: Object, 
                required: true
            }
        },

        computed: {
            createAt() {
                return this.repo.pushed_at.split('T')[0];
            }
        }
    }
</script>