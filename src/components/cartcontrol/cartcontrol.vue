<template>
    <div class="cartcontrol">
        <transition name="decrease">
            <div class="cart-cartcontrol icon-remove_circle_outline" v-show="food.count>0" @click="reduce"></div>           
        </transition>
        <div class="cart-count" v-show="food.count>0">{{food.count}}</div>
        <div class="cart-add icon-add_circle" @click="add"></div>
    </div>
</template>

<script>
import Vue from 'vue'
export default {
    
    props:{
        food:{
            type:Object
        }
    },
    methods:{
        add(){
            if(!this.food.count){
                Vue.set(this.food,'count',1)
            }else{
                this.food.count++
            }
            this.$emit('add-cart',event.target)
        },
        reduce(){
            if(this.food.count){
                this.food.count--                
            }
        }
    }
 
}
</script>

<style scoped lang="stylus">
                  
    .cartcontrol
        font-size 0
        .decrease-enter
            opacity: 0
            transform translate3d(24px,0,0)
            transform rotate(0)
        .decrease-enter-active
            transition all .5s ease
        .decrease-enter-to
            opacity: 1
            transform translate3d(0,0,0) 
            transform rotate(180deg)                   
        .decrease-leave
            opacity: 1
            transform translate3d(0,0,0) 
            transform rotate(0)                                                 
        .decrease-leave-active
            transition all .5s linear    
        .decrease-leave-to
            opacity:0; 
            transform translate3d(48px,0,0)
            transform rotate(180deg)  
        .cart-cartcontrol, .cart-add
            display inline-block
            padding 6px
            font-size 24px
            line-height 24px
            color rgb(0,160,220)
        .cart-count
            display inline-block 
            vertical-align: top
            width: 12px
            padding-top: 6px
            line-height: 24px
            text-align: center
            font-size: 10px
            color: rgb(147, 153, 159)           
        .cart-add
            display inline-block
        
</style>
