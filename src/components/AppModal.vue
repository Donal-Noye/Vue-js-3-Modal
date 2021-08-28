<template>
   <transition name="modal-animation">
      <div v-show="modalActive" class="modal">
         <transition name="modal-animation-inner">
            <div v-show="modalActive" class="modal-inner">
               <i @click="close" class="far fa-times-circle"></i>
               <slot />
               <button @click="close" type="button">Close</button>
            </div>
         </transition>
      </div>
   </transition>
</template>

<script>
export default {
   props: ['modalActive'],
   setup(_, {emit}) {
      const close = () => {
         emit('close')
      }

      return {close}
   }
}
</script>

<style lang="scss" scoped>
.modal-animation-enter-active,
.modal-animation-leave-active {
   transition: opacity .3s cubic-bezier(.52, .02, .19, 1.02);
}

.modal-animation-inner-enter-active {
   transition: all .3s cubic-bezier(.52, .02, .19, 1.02) .15s;
}

.modal-animation-inner-leave-active {
   transition: all .3s cubic-bezier(.52, .02, .19, 1.02);
}

.modal-animation-inner-enter-from {
   opacity: 0;
   transform: scale(.8);
}

.modal-animation-inner-leave-to {
   transform: scale(.8);
}

.modal-animation-enter-from,
.modal-animation-leave-to {
   opacity: 0;
}

.modal {
   display: flex;
   justify-content: center;
   align-items: center;

   width: 100vw;
   height: 100vh;

   background-color: rgba(#fff, .7);

   position: fixed;
   top: 0;
   left: 0;

   &-inner {
      position: relative;
      max-width: 640px;
      width: 80%;
      box-shadow: 0 4px 6px -1px rgba(#000, .1), 0 2px 4px -1px rgba(#000, .06);
      background-color: #fff;
      padding: 64px 16px;

      i {
         position: absolute;
         top: 15px;
         right: 15px;
         font-size: 20px;
         cursor: pointer;

         &:hover {
            color: crimson;
         }
      }
   }
}
</style>