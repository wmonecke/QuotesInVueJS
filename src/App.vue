<template>
    <div class="container">
        <appBar></appBar>
        <appQuoteInput></appQuoteInput>
        <appQuoteDiplay></appQuoteDiplay>
    </div>
</template>

<script>
    import ProgressBar  from './components/ProgressBar.vue'
    import QuoteInput   from './components/QuoteInput.vue'
    import QuoteDisplay from './components/QuoteDisplay.vue'

    export default {
        components: {
            appBar: ProgressBar,
            appQuoteInput: QuoteInput,
            appQuoteDiplay: QuoteDisplay
        }
    }
</script>

<style>
</style>
