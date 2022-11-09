<template>
    <div>
        <section>
        <transition-group name='fade' tag='h1'>
          <div class=" h-screen bg-cover" v-for="i in [currentIndex]" :key='i'>
            <img :src="currentImg" />
          </div>
        </transition-group>
        <a class="prev" @click="prev" href='#'>&#10094;</a>
      <a class="next" @click="next" href='#'>&#10095;</a>
      <div class="mx-auto h-screen flex text-white justify-left sm:w-4/5 items-center">
                        <div v-for="i in [currentIndex]" :key='i'  class="text-left font-montserrat mx-5 z-10">
                            <h1 class="text-6xl font-black my-10 z-10">
                                FIND THE
                                <br>
                                WORLD'S BEST
                                <br> 
                                PRODUCT SALE
                            </h1>
                            <router-link to='/explore' class="py-5 px-10 text-xl bg-green-600 z-10">
                                Search Product
                                <font-awesome-icon class="ml-3" :icon="['fas', 'arrow-right']" /> 
                            </router-link>                       
                        </div>

                        <div class="text-8xl absolute right-0 font-lato hidden sm:block font-bold overflow-y-hidden w-1/2"> 
                        <img src="../assets/82.png" alt="" class="w-full"> 
                        </div>
                    </div>
                </section>
      </div>
     
    </template>
    
    <script>
    export default {
      name: 'Slider',
      data() {
        return {
          images: [
            'https://cdn.pixabay.com/photo/2015/12/12/15/24/amsterdam-1089646_1280.jpg',
            'https://cdn.pixabay.com/photo/2016/02/17/23/03/usa-1206240_1280.jpg',
            'https://cdn.pixabay.com/photo/2015/05/15/14/27/eiffel-tower-768501_1280.jpg',
            'https://cdn.pixabay.com/photo/2016/12/04/19/30/berlin-cathedral-1882397_1280.jpg'
            ],
          timer: null,
          currentIndex: 0,
        }
      },
      
        mounted: function() {
          this.startSlide();
        },
      
        methods: {
          startSlide: function() {
            this.timer = setInterval(this.next, 900);
          },
      
      
          next: function() {
            this.currentIndex += 1
          },
          prev: function() {
            this.currentIndex -= 1
          }
        },
      
        computed: {
          currentImg: function() {
            return this.images[Math.abs(this.currentIndex) % this.images.length];
          }
        }
      
    }
    </script>
    
    <style>
    .fade-enter-active,
    .fade-leave-active {
      transition: all 0.9s ease;
      overflow: hidden;
      visibility: visible;
      position: absolute;
      width:100%;
      opacity: 1;
    }
    .fade-enter,
    .fade-leave-to {
      visibility: hidden;
      width:100%;
      opacity: 0;
    }
    img {
    height:600px;
    width:100%
      }
    .prev, .next {
      cursor: pointer;
      position: absolute;
      top: 40%;
      width: auto;
      padding: 16px;
      color: white;
      font-weight: bold;
      font-size: 18px;
      transition: 0.7s ease;
      border-radius: 0 4px 4px 0;
      text-decoration: none;
      user-select: none;
    }
    /* Position the "next button" to the right */
    .next {
      right: 0;
    }
    .prev {
      left: 0;
    }
    /* On hover, add a black background color with a little bit see-through */
    .prev:hover, .next:hover {
      background-color: rgba(0,0,0,0.9);
    }
    </style>