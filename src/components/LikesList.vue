<script setup>
import { ref } from 'vue'
import { onClickOutside } from '@vueuse/core'
const modal = ref('modal')
const emit = defineEmits(['close-modal'])
onClickOutside(modal, event => {
  emit('close-modal')
})
defineProps(['users'])
</script>
<template>
  <Transition name="modal">
    <div class="my-modal">
      <div class="modal-box" ref="modal">
        <div class="header">
          <div class="close-box"></div>
          <div class="fs-5 fw-semibold m-auto">Likes</div>
          <button type="button" class="btn-close" aria-label="Close" @click="$emit('close-modal')"></button>
        </div>
        <div class="content">
          <div class="text-body-secondary px-2" v-if="users">{{ users.length }} Likes</div>
          <hr class="my-1">
          <div class="user" v-for="user in users">
            <img :src="`https://ui-avatars.com/api/?name=${user.name.replace(' ', '+')}`" alt="user">
            <div class="user-info">
              <div class="fw-semibold">{{ user.username }}</div>
              <small class="text-body-secondary">{{ user.name }}</small>
            </div>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>
<style scoped>
.my-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  padding: 5rem 0 3rem 0;
  z-index: 50;
}

.my-modal .modal-box {
  background: #fff;
  margin: auto;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  transition: all 300ms;
}

.my-modal .header {
  padding: 12px 18px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* gap: 24px; */
}

.my-modal .content {
  max-height: calc(100vh - 5rem - 54px);
  overflow-y: auto;
}

.close-box {
  width: 36px;
  height: 36px;
  padding: 6px;
  margin: -6px;
}

.close-btn {
  border-radius: 4px;
  cursor: pointer;
  text-align: center;
}

.close-btn i {
  font-size: 20px;
}

.close-btn:hover {
  background-color: #f9fafb;
}

.user {
  display: flex;
  gap: 16px;
  align-items: center;
  margin-top: 16px;
}

.user:nth-child(1) {
  margin-top: 0;
}

.user img {
  width: 48px;
  height: 48px;
  border-radius: 50%;
}

.my-modal .content,
.my-modal .footer {
  padding: 20px;
  border-top: 1px solid #d1d5db;
}

.my-modal .footer {
  text-align: right;
}

@media (min-width: 640px) {
  .my-modal .modal-box {
    width: 70%;
  }

  .my-modal .content {
    max-height: calc(100vh - 13.25rem);
  }
}

@media (min-width: 768px) {
  .my-modal .modal-box {
    width: 60%;
  }
}

@media (min-width: 1024px) {
  .my-modal .modal-box {
    width: 40%;
  }
}

@media (max-width: 640px) {
  .my-modal .modal-box {
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
  }

  .my-modal .modal-box {
    height: calc(100vh - 5rem);
  }
}

.modal-enter-active,
.modal-leave-active {
  transition: all 150ms ease;
}

/* .modal-enter-active {
  transition: all 150ms ease;
} */

.modal-leave-active {
  /* transition-delay: 400ms; */
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(1.10);
}

.modal-enter-active .modal-box,
.modal-leave-active .modal-box {
  transition: all 150ms ease-in-out;
}

/* .modal-enter-active .modal-box {
  transition-delay: 200ms;
}

.modal-enter-from .modal-box,
.modal-leave-to .modal-box {
  opacity: 0;
  transform: translateY(-48px);
}

.modal-enter-to .modal-box,
.modal-leave-from .modal-box {
  opacity: 1;
  transform: translateY(0);
} */
</style>