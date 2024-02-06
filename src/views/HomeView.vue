<script setup lang="ts">
  import { ref } from 'vue'

  const handleSubmit = (e: Event) => {
    e.preventDefault()
    if (url.value === '') {
      makeAnAlert('Please enter a URL')
      return
    }
  }

  const alertMessage = ref('')
  function makeAnAlert(message: string) {
    alertMessage.value = message
    setTimeout(() => {
      alertMessage.value = ''
    }, 3000)
  }

  function validator(url: string) {
    const regex = new RegExp(
      '^(https?:\\/\\/)?' + // protocol
        '((([a-z\\d]([a-z\\d-]*[a-z\\d])*)\\.)+[a-z]{2,}|' + // domain name
        '((\\d{1,3}\\.){3}\\d{1,3}))' + // OR ip (v4) address
        '(\\:\\d+)?(\\/[-a-z\\d%_.~+]*)*' + // port and path
        '(\\?[;&a-z\\d%_.~+=-]*)?' + // query string
        '(\\#[-a-z\\d_]*)?$',
      'i'
    ) // fragment locator
    return !!regex.test(url)
  }

  function validateURL() {
    if (!validator(url.value)) {
      makeAnAlert('Please enter a valid URL')
      return
    }
  }

  const url = ref('')
</script>

<template>
  <div class="home">
    <form action="">
      <input type="text" placeholder="URL to shorten" v-model="url" @change="validateURL" />
      <button type="submit" @click="handleSubmit">Shorten</button>
    </form>
    <div class="alert">
      <p>{{ alertMessage }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .home {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: calc(100vh - 4rem);

    form {
      display: flex;
      gap: 1rem;

      input {
        padding: 0.5rem;
        border: none;
        border-radius: 0.25rem;
        font-size: 1.2em;
        width: 30rem;
      }

      button {
        padding: 0.5rem 1rem;
        border: none;
        border-radius: 0.25rem;
        background: #80da37;
        color: #130e3d;
        font-size: 1.2em;
        cursor: pointer;
        transition: 0.3s ease-in-out;

        &:hover {
          background: #d7a21b;
          border-radius: 50px;
        }
      }
    }

    .alert {
      min-height: 2rem;
    }
  }
</style>
