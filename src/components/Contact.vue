<template>
  <div class="bg-gray-950 text-white min-h-screen">

    <!-- HEADER -->
    <section class="py-24 text-center">
      <h1 class="text-5xl font-bold">
        Contact <span class="text-yellow-500">Us</span>
      </h1>
      <p class="text-gray-400 mt-4">
        Have questions? Get in touch with our team.
      </p>
    </section>

    <section class="max-w-6xl mx-auto px-6 py-16 grid md:grid-cols-2 gap-16">

      <!-- FORM -->
      <form class="bg-gray-900 p-10 rounded-2xl space-y-6" @submit.prevent="sendWhatsApp">

        <div>
          <label class="text-sm text-gray-400">Name</label>
          <input v-model="name" type="text"
            class="w-full mt-2 p-3 bg-gray-800 rounded-lg outline-none focus:ring-2 focus:ring-yellow-500" />
        </div>

        <div>
          <label class="text-sm text-gray-400">Email</label>
          <input v-model="email" type="email"
            class="w-full mt-2 p-3 bg-gray-800 rounded-lg outline-none focus:ring-2 focus:ring-yellow-500" />
        </div>

        <div>
          <label class="text-sm text-gray-400">Message</label>
          <textarea v-model="message" rows="4"
            class="w-full mt-2 p-3 bg-gray-800 rounded-lg outline-none focus:ring-2 focus:ring-yellow-500"></textarea>
        </div>

        <p v-if="error" class="text-yellow-500 text-sm">{{ error }}</p>

        <button type="submit" class="w-full py-3 bg-yellow-500 rounded-xl font-semibold hover:bg-yellow-600 transition">
          Send Message
        </button>

      </form>

      <!-- CONTACT INFO -->
      <div class="space-y-8">

        <div>
          <h3 class="text-xl font-semibold mb-2">Address</h3>
          <p class="text-gray-400">
            Shree Sidhivinayak Encave Shop No. 6,7,8, <br>
            near Dayanand Anglo Vedic School, Sector-9, <br>
            New Panvel East, Panvel, Maharashtra 410206
          </p>
        </div>

        <div>
          <h3 class="text-xl font-semibold mb-2">Phone</h3>
          <p class="text-gray-400">
            +91 098337 69885
          </p>
        </div>

        <!-- <div>
          <h3 class="text-xl font-semibold mb-2">Email</h3>
          <p class="text-gray-400">
            contact@Bobs Gymgym.com
          </p>
        </div> -->

      </div>

    </section>

  </div>
</template>


<script>

export default {
  data() {
    return {
      name: "",
      email: "",
      message: "",
      error: ""
    }
  },
  methods: {
    sendWhatsApp() {
      this.error = ""

      // Empty validation
      if (!this.name || !this.email || !this.message) {
        this.error = "All fields are requiyellow."
        return
      }

      // Email validation
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/

      if (!emailRegex.test(this.email)) {
        this.error = "Please enter a valid email address."
        return
      }

      const phone = "9109833769885"

      const text =
        `New Contact Request

Name: ${this.name}
Email: ${this.email}

Message:
${this.message}`

      const url = `https://wa.me/${phone}?text=${encodeURIComponent(text)}`

      window.open(url, "_blank")

      this.name = ""
      this.email = ""
      this.message = ""
    }
  }
}
</script>