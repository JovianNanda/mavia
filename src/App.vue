<script setup>
import { ref } from 'vue'
import Modal from './components/Modal.vue'
import LikesList from './components/LikesList.vue'
const userList = ref(null)
const users = ref([
  {
    username: 'mdadityaa',
    name: 'Made Aditya'
  },
  {
    username: 'joviannanda',
    name: 'Jovian Nanda Sismawan'
  },
  {
    username: 'adiadrian708',
    name: 'Adrian'
  },
])
const users2 = ref([
  {
    username: 'gungadi_tamvan',
    name: 'Gung Adi'
  },
  {
    username: 'mangsu',
    name: 'Komang Suadnyana'
  },
])
// const showModal = ref(false)

</script>
<template>
  <div class="container">
    <div class="my-3">
      <h3>Postingan 1</h3>
      <i class="fa-regular fa-heart"></i>
      <a href="#" class="ms-2 no-link" @click.prevent="userList = users">103 Likes</a>
    </div>
    <div class="my-3">
      <h3>Postingan 2</h3>
      <i class="fa-regular fa-heart"></i>
      <a href="#" class="ms-2 no-link" @click.prevent="userList = users2">102 Likes</a>
    </div>
    <!-- <button class="btn btn-primary" @click="showModal = true">Modal</button> -->
    <LikesList v-show="userList?.length > 0" :users="userList" @close-modal="userList = null" />
    <!-- <Modal v-show="showModal" @close-modal="showModal = false">
                        <template #modal-header>
                          <div class="fs-4 text-center m-auto">Modal</div>
                        </template>
                        <template #modal-content>
                          <p>Lorem, ipsum dolor.</p>
                        </template>
                      </Modal> -->
    <!-- <button class="btn btn-primary" @click="">Likes</button>
                                                                  <LikesList v-show="userList" /> -->
  </div>
</template>