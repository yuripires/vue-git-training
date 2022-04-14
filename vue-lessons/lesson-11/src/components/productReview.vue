<template>
    <form style="text-align: center" @submit.prevent="onSubmit">
        <p v-if="errors.length">
            <b>Please correct the following error(s):</b>
            <ul>
                <li v-for="error in errors" :key="error">{{error}}</li>
            </ul>
        </p>
        <p>
            <label for="productReview.name">Name:</label>
            <input id="productReview.name" v-model="productReview.name">
        </p>
        <p>
            <label for="productReview.review">Review:</label>
            <input id="productReview.review" v-model="productReview.review">
        </p>
        <p>
            <label for="productReview.rating">Rating:</label>
            <select id="productReview.rating" v-model="productReview.rating">
                <option>5 Stars</option>
                <option>4 Stars</option>
                <option>3 Stars</option>
                <option>2 Stars</option>
                <option>1 Stars</option>
            </select>
        </p>
        <p>
            <label for="productReview.recomend">Would you reccomend this product?</label>
            <select id="productReview.recomend" v-model="productReview.recomend">
                <option>YES</option>
                <option>NO</option>
            </select>
        </p>
        <p>
            <input type="submit" value="Submit">
        </p>
    </form>
</template>

<script>
import { eventBus } from '@/main'
export default {
    data(){
        return{
         productReview:{
            name: null,
            review: null,
            rating: null,
            recomend: null,
         },
         errors:[],
        }
        
    },
    methods:{
        onSubmit(){
          if (this.productReview.name && this.productReview.review && this.productReview.rating && this.productReview.recomend){
            eventBus.$emit('review-submitted',this.productReview)
           
          
        }else{
            if(!this.productReview.name) this.errors.push("Name required.")
            if(!this.productReview.review) this.errors.push("Review required.")
            if(!this.productReview.rating) this.errors.push("Rating required.")
            if(!this.productReview.recomend) this.errors.push("Reccomend required.")
        }
        },
        
    },
}
</script>
