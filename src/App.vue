<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"/>
        <app-new-quote @quoteAdded="newQuote"/>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"/>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a quote to delete it!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Header from './components/Header.vue';
    import NewQuote from './components/NewQuote.vue';
    import QuoteGrid from './components/QuoteGrid.vue';
    
    export default {
        components: {
            appHeader: Header,
            appNewQuote: NewQuote,
            appQuoteGrid: QuoteGrid
        },
        
        data: () => {
            return {
                quotes: [
                    'Just a quote to see something'
                ],
                maxQuotes: 10
            }
        },
        
        methods: {
            newQuote(quote) {
                if ( this.quotes.length >= this.maxQuotes) {
                    return alert('Please delete quotes first');
                }
                
                this.quotes.push(quote);
            },
            
            deleteQuote(index) {
                this.quotes.splice(index, 1);
            }
        }
    }
</script>

<style>
</style>
