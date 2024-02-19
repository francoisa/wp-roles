<script setup lang="ts">
import { ref, watch } from 'vue'

// const base_url = 'https://wordpress.org/documentation/article/roles-and-capabilities/#'
const baseUrl = window.location.href + 'capabilities.html#'
defineEmits(['enlarge-text'])
const props = defineProps({ capability: { type: String, required: true } })

props.capability

const description = ref('')

watch(props, () => {
  description.value = '<h3 id="delete_posts" class="is-toc-heading wp-block-heading" tabindex="-1"><a href="#delete_posts">delete_posts</a></h3>'
  const xhr = new XMLHttpRequest()
  xhr.responseType = 'document'
  xhr.open("GET", baseUrl, true)
  xhr.onload = (e) => {
    if (xhr.readyState === XMLHttpRequest.DONE) {
      if (xhr.status === 200) {
        const element = xhr.response.getElementById(props.capability)
        description.value = element.outerHTML + element.nextElementSibling.outerHTML
      } 
      else {
        console.error(xhr.statusText)
      }
    }
  }
  xhr.onerror = (e) => {
    console.error(xhr.statusText)
  }
  xhr.send(null)
})
</script>

<template>
  <div class="modal-content">
    <div class="modal-header">
      <h5 class="modal-title" id="exampleModalLabel">{{ capability }}</h5>
      <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
    </div>
    <div class="modal-body" v-html="description"></div>
    <div class="modal-footer">
      <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
    </div>
  </div>
</template>
