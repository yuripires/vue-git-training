<template>
    <div>
        <span class="tab" 
        v-for="(tab, index) in tabs" 
        :class="{activeTab: selectedTab === tab}" 
        :key="index"
        @click="selectedTab = tab"> {{tab}}  </span> 
    
    <div v-show="selectedTab === 'Reviews'">
      <h2>Reviews:</h2>
      <p v-if="!reviews.lenght"> There are no reviews yet.</p>
      <ul>
        <li v-for="review in reviews" :key="review.name">
          <p> Name: {{review.name}} </p>
          <p> Review: {{review.review}} </p>
          <p> Rating: {{review.rating}} </p>
          <p> Is this product recomended? {{review.recomend}}</p>

        </li>
      </ul>
    </div>
    
    <product-review  v-show="selectedTab === 'Make a Review'"></product-review>
    
    </div>
</template>

<script>
import productReview from './productReview.vue'

export default {
    props:{
        reviews:{
            type: Array,
            required: true,
        }
    },
    components: { productReview },
    data() {
        return {
            tabs:['Reviews','Make a Review'],
            selectedTab: 'Reviews',
        }
    },
    methods:{

    }
}
</script>

<style>
.activeTab{
    text-decoration: underline;
    cursor: pointer;
    color: blue;
}
.tab:hover{
    text-decoration: underline;
    cursor: pointer;
}

</style>