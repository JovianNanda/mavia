<script setup>
import { ref } from 'vue'
import { onClickOutside } from '@vueuse/core'
const modal = ref('modal')
const emit = defineEmits(['close-comments'])
onClickOutside(modal, event => {
  emit('close-comments')
})

defineProps(['comments'])
const repliesData = ref([

])
const replies = ref(null)
</script>
<template>
  <Transition name="modal">
    <div class="my-modal">
      <div class="modal-box" ref="modal">
        <div class="header">
          <div class="close-box"></div>
          <div class="fs-5 fw-semibold m-auto">Comments</div>
          <button type="button" class="btn-close" aria-label="Close" @click="$emit('close-comments')"></button>
        </div>
        <div class="content">
          <div class="comment" v-for="comment in comments">
            <img :src="`https://ui-avatars.com/api/?name=${comment.name.replace(' ', '+')}`" alt="user">
            <div class="flex-grow-1">
              <div class="user-info">
                <div>
                  <div class="fw-semibold">{{ comment.username }}</div>
                  <div class="">{{ comment.comment }}</div>
                  <div class="mb-1">
                    <small>6m</small>
                    <small class="text-body-secondary ms-3 fw-semibold">Reply</small>
                  </div>
                </div>
                <div class="text-center">
                  <i class="fa-regular fa-heart mt-3 d-block"></i>
                  <small class="text-center">120</small>
                </div>
              </div>
              <div class="replies w-100">
                <div class="comment" v-if="comment.replies" v-for="c in replies">
                  <img :src="`https://ui-avatars.com/api/?name=${c.name.replace(' ', '+')}`" alt="user">
                  <div class="flex-grow-1">
                    <div class="user-info">
                      <div>
                        <div class="fw-semibold">{{ c.username }}</div>
                        <div class="">{{ c.comment }}</div>
                        <div class="mb-1">
                          <small>6m</small>
                          <small class="text-body-secondary ms-3 fw-semibold">Reply</small>
                        </div>
                      </div>
                      <div class="text-center">
                        <i class="fa-regular fa-heart mt-3 d-block"></i>
                        <small class="text-center">120</small>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <small class="text-body-secondary cursor-pointer" v-if="!replies && comment.replies"
                @click="replies = comment.replies">View
                replies
                (2)</small>
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

.comment {
  display: flex;
  gap: 16px;
  margin-top: 16px;
  width: 100%;
}

.comment:nth-child(1) {
  margin-top: 0;
}

.comment .user-info {
  display: flex;
  gap: 8px;
  justify-content: space-between;
  width: 100%;
}

.comment img {
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
    width: 75%;
  }

  .my-modal .content {
    max-height: calc(100vh - 13.25rem);
  }
}

@media (min-width: 768px) {
  .my-modal .modal-box {
    width: 65%;
  }
}

@media (min-width: 1024px) {
  .my-modal .modal-box {
    width: 45%;
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
</style>