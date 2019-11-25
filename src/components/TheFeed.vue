<template>
    <div>
        <FeedCard
            v-for="repo in repositories"
            :key="repo.id"
            :repo="repo"
        />
        <div
            class="relative py-4 h-10 rounded-lg"
        >
            <BaseLoader
                v-if="isFetchingData"
            />
        </div>
    </div>
</template>

<script>
    import FeedCard from './FeedCard';
    import BaseLoader from './Base/BaseLoader';

    export default {
        name: 'TheFeed',

        props: {
            date: {
                type: Date, 
                required: true
            }
        },

        components: {
            FeedCard,
            BaseLoader
        },

        watch: {
            date() {
                // when date changes we reset the feed
                this.repositories = [];
                this.currentPage = 1;
                this.getData();
            },
            isbottomOfPage(newVal) {
                if(newVal === true && this.currentPage !== this.totalPages && !this.isFetchingData) this.getData();
            }
        },

        data() {
            return {
                repositories: [],
                currentPage: 1,
                nextPage: 1,
                totalPages: 1,
                isbottomOfPage: false,
                isFetchingData: false
            }
        },

        created() {
            this.getData();

            window.onscroll = () => {
                this.isbottomOfPage = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;
            };
        },

        methods: {
            async getData() {
                this.showLoader();
                try {
                    const url = this.generateUrl();
                    const response = await fetch(url);
                    const data = await response.json();
                    
                    this.hideLoader();
                    this.repositories = this.repositories.concat(data.items);
                    this.updateCurrentPage();
                    this.calculateTotalPages(data.total_count);
                } catch (error) {
                    this.hideLoader();
                    console.error(error);
                }
            },

            generateUrl() {
                const year = this.date.getFullYear();
                const month = this.date.getMonth() + 1 > 9 ? this.date.getMonth() + 1 : `0${this.date.getMonth() + 1}` // we add 1 because getMonth() starts counting months from 0
                const day = this.date.getDate() > 9 ? this.date.getDate() : `0${this.date.getDate()}`;

                return `https://api.github.com/search/repositories?q=created:>${year}-${month}-${day}&sort=stars&order=desc&page=${this.currentPage + 1}`;
            },

            /**
             * @param {Number} total - total items
             */
            calculateTotalPages(total) {
                this.totalPages =  Math.trunc(total/30); 
            },

            updateCurrentPage() {
                this.currentPage += 1;
            },

            showLoader() {
                this.isFetchingData = true;
            },

            hideLoader() {
                this.isFetchingData = false;
            }
        }
    }
</script>