<template>
  <div class="home">
    <app-modal @close="toggleModal" :modalActive="modalActive">
      <div class="modal-content">
        <h1>This is Modal Header</h1>
        <p>YThis is a modal Message</p>
      </div>
    </app-modal>
    <button @click="toggleModal" type="button">Open Modal</button>
  </div>
</template>

<script>
import AppModal from "@/components/AppModal";
import { ref } from "vue";

export default {
  setup() {
    const modalActive = ref(false);

    const toggleModal = () => {
      modalActive.value = !modalActive.value
    }

    return {
      modalActive,
      toggleModal,
    }
  },
  components: { AppModal },
};
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  justify-content: center;
  align-items: center;

  height: 100vh;

  background: rgba(0, 176, 234, .5);

  .modal-content {
    display: flex;
    flex-direction: column;

    h1, p {
      margin-bottom: 16px;
    }

    h1 {
      font-size: 32px;
    }

    p {
      font-size: 18px;
    }
  }
}
</style>