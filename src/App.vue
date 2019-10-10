<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes">

        </app-header>
        <app-new-quote @newquote="newQuote">

        </app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote">

        </app-quote-grid>

        <div class="d-flex justify-content-around">
            <div class="alert alert-info">
                Info: Click on a Quote to delete it!
            </div>
        </div>

    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/header.vue';
    export default {
        data: function() {
            return {
                maxQuotes: 10,
                quotes: ['Sample quote']
            }
        },
        methods: {
            newQuote(quote) {
                if(this.quotes.length >= this.maxQuotes) {
                    return alert('plz delete some quotes. max is 10')
                }
                this.quotes.push(quote);
            },
            deleteQuote(index) {
                this.quotes.splice(index, 1);
            }
        },
        components: {
            'app-quote-grid': QuoteGrid,
            'app-new-quote': NewQuote,
            'app-header': Header
        }
    }
</script>

<style>
</style>
