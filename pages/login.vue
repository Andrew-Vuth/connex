<template>
  <div class="h-screen md:flex">
    <div
      class="relative overflow-hidden md:flex w-1/2 bg-gradient-to-tr from-blue-800 to-purple-700 i justify-around items-center hidden"
    >
      <div class="px-10">
        <h1 class="text-white font-bold text-4xl font-sans">
          Start connexting with people around the world with Connex
        </h1>
        <p class="text-white mt-4">
          A platform where people with similar hobby can enjoy together company
          and build a healthy community
        </p>
        <div>
          <img
            src="~/static/intro-page-pic.png"
            alt=""
            srcset=""
            class="w-1/2 h-1/2 ml-24 mt-5"
          />
        </div>
      </div>
      <div
        class="absolute -bottom-32 -left-40 w-80 h-80 border-4 rounded-full border-opacity-30 border-t-8"
      ></div>
      <div
        class="absolute -bottom-40 -left-20 w-80 h-80 border-4 rounded-full border-opacity-30 border-t-8"
      ></div>
      <div
        class="absolute -top-40 -right-0 w-80 h-80 border-4 rounded-full border-opacity-30 border-t-8"
      ></div>
      <div
        class="absolute -top-20 -right-20 w-80 h-80 border-4 rounded-full border-opacity-30 border-t-8"
      ></div>
    </div>
    <div class="flex md:w-1/2 justify-center py-10 items-center bg-white">
      <form class="bg-white" @submit.prevent="login()">
        <h1 class="text-gray-800 font-bold text-2xl mb-1">Connex</h1>
        <p class="text-sm font-normal text-gray-600 mb-7">Start Connexting</p>
        <div class="flex items-center border-2 py-2 px-3 rounded-2xl mb-4">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 text-gray-400"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M16 12a4 4 0 10-8 0 4 4 0 008 0zm0 0v1.5a2.5 2.5 0 005 0V12a9 9 0 10-9 9m4.5-1.206a8.959 8.959 0 01-4.5 1.207"
            />
          </svg>
          <input
            v-model="email"
            class="pl-2 outline-none border-none"
            type="email"
            name=""
            id=""
            placeholder="Email Address"
            required
          />
        </div>
        <div class="flex items-center border-2 py-2 px-3 rounded-2xl">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 text-gray-400"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M5 9V7a5 5 0 0110 0v2a2 2 0 012 2v5a2 2 0 01-2 2H5a2 2 0 01-2-2v-5a2 2 0 012-2zm8-2v2H7V7a3 3 0 016 0z"
              clip-rule="evenodd"
            />
          </svg>
          <input
            v-model="password"
            class="pl-2 outline-none border-none"
            type="password"
            name=""
            id=""
            placeholder="Password"
            required
          />
        </div>
        <button
          type="submit"
          class="block w-full bg-indigo-600 mt-4 py-2 rounded-2xl text-white font-semibold mb-2"
        >
          {{ !loading ? 'Log In' : 'Loading....' }}
        </button>
        <nuxt-link
          to="/signup"
          class="text-sm hover:text-blue-500 cursor-pointer"
          >Don't have an account?</nuxt-link
        >
      </form>

      CHAT
    </div>
  </div>
</template>

<script>
export default {
  head: {
    title: 'Login',
  },
  data() {
    return {
      loading: false,
      email: '',
      password: '',
    }
  },
  created() {
    const token = this.$cookies.get('token')
    if (token) {
      this.$router.push('/')
    }
  },
  methods: {
    async login() {
      this.loading = true
      const { email, password } = this
      const formData = {
        email,
        password,
      }
      await this.$store.dispatch('users/login', formData)
      try {
      } catch (error) {}
    },
  },
}
</script>
