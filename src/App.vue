<template>
  <div class="component">
    <Header :quoteCount="quotes.length" :maxQuotes="maxQuotes" />
    <NewQuote @quoteAdded="newQuote"></NewQuote>
    <QuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote" />
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to Delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import NewQuote from './components/NewQuote.vue'
import Header from './components/Header.vue'

export default {
  data: function(){
    return{
      quotes:['A quote'],
      maxQuotes: 10
    }
  },
  methods: {
    newQuote(quote){
      if(this.quotes.length >= this.maxQuotes){
        return alert('Please delete Quotes first!')
      }
      this.quotes.push(quote)
    },
    deleteQuote(index){
      this.quotes.splice(index, 1)
    }
  },
  components: {
    QuoteGrid,
    NewQuote,
    Header
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
