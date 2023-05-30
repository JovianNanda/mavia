<script setup>
import { ref } from 'vue'
import Modal from './components/Modal.vue'
import LikesList from './components/LikesList.vue'
import Comments from './components/Comments.vue'
const showLikes = ref(false)
const userList = ref(null)
const showComments = ref(false)
const commentList = ref(null)
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
    username: 'joviannanda',
    name: 'Jovian Nanda Sismawan'
  },
  {
    username: 'adiadrian708',
    name: 'Adrian'
  },
  {
    username: 'adiadrian708',
    name: 'Adrian'
  },
  {
    username: 'mdadityaa',
    name: 'Made Aditya'
  },
  {
    username: 'adiadrian708',
    name: 'Adrian'
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
const comments = ref([
  {
    username: 'mdadityaa',
    name: 'Made Aditya',
    comment: 'Lorem ipsum dolor sit amet cons.',
    replies: [
      {
        username: 'adiadrian708',
        name: 'Adi Adriana',
        comment: 'Lorem ipsum dolor',
      }
    ],
    replies_count: 1
  },
  {
    username: 'joviannanda',
    name: 'Jovian Nanda Sismawan',
    comment: 'Lorem ipsum dolor sit amet',
    replies_count: 0
  },
])
function openLikes(data) {
  showLikes.value = true
  userList.value = data
}
function openComments(data) {
  showComments.value = true
  commentList.value = data
}
// const showModal = ref(false)

</script>
<template>
  <div class="container">
    <div class="my-3">
      <h3>Postingan 1</h3>
      <span>
        <i class="fa-regular fa-heart"></i>
        <a href="#" class="ms-2 no-link" @click.prevent="openLikes(users)">103 Likes</a>
      </span>
      <span class="ms-3">
        <i class="fa-regular fa-comment"></i>
        <a href="#" class="ms-2 no-link" @click.prevent="openComments(comments)">3 Comments</a>
      </span>
    </div>
    <div class="my-3">
      <h3>Postingan 2</h3>
      <i class="fa-regular fa-heart"></i>
      <a href="#" class="ms-2 no-link" @click.prevent="openLikes(users2)">102 Likes</a>
    </div>
    <!-- <button class="btn btn-primary" @click="showModal = true">Modal</button> -->
    <LikesList v-show="showLikes && userList?.length > 0" :users="userList" @close-modal="showLikes = false" />
    <Comments v-show="showComments" :comments="commentList" @close-comments="showComments = false" />
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