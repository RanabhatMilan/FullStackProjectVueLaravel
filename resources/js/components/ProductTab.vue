<template>
<div>  <div>    
          <ul>
            <span class="tab" :class="{ activeTab: selectedTab === tab }"
                  v-for="(tab, index) in tabs" 
                  @click="selectedTab = tab" 
            >{{ tab }}</span>
          </ul> 
        </div>
	 <div v-show="selectedTab === 'Reviews'">
                <p >There are no reviews yet.</p>
                <ul>
                    <li v-for="(review, index) in reviews" :key="index">
                      <p>{{ review.name }}</p>
                      <p>Rating:{{ review.rating }}</p>
                      <p>{{ review.review }}</p>
                    </li>
                </ul>
            </div>
   	
    <div v-show="selectedTab === 'Make a Review'">
     <product-reviews></product-reviews>
     </div>
     </div>
	</template>

  <script>
  export default{
   props: {
      reviews: {
        type: Array,
        required: false
      }
    },  
      data() {
        return {
          tabs: ['Reviews', 'Make a Review'],
          selectedTab: 'Reviews'  // set from @click
        }
      }
      };
  </script>