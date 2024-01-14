<template>
  <section class="py-24 lg:py-28 bg-white overflow-hidden m-auto max-w-6xl">
    <div class="container px-4 mx-auto">
      <div class="flex flex-wrap -m-8">
        <div class="w-full md:w-1/2 p-8">
          <div class="flex flex-col justify-between max-w-lg h-full">
            <div class="mb-12">
              <h2
                class="font-heading mb-6 text-4xl text-rhino-600 text-gray-700 tracking-tighter"
              >
                Manufacturing Address
              </h2>
              <p class="text-xl tracking-tight pb-4 border-b">
                Amritsar, 143001, Punjab, India.
              </p>
              <h2
                class="font-heading mt-6 text-2xl text-gray-700 tracking-tighter"
              >
                Mr. Anil Sharma
              </h2>
              <p>(Managing Director)</p>
              <h2
                class="font-heading text-xl text-gray-700 tracking-tighter pb-4 border-b"
              >
              +91 8194800871
              </h2>

              <h2
                class="font-heading mt-6 text-2xl text-gray-700 tracking-tighter"
              >
                Mr. Anil Sharma
              </h2>
              <p>(Managing Director)</p>
              <h2
                class="font-heading text-xl text-gray-700 tracking-tighter pb-4 border-b"
              >
                +91 00000-00000
              </h2>
              <h2
                class="font-heading mt-6 text-2xl text-gray-700 tracking-tighter"
              >
                Mr. Anil Sharma
              </h2>
              <p>(Managing Director)</p>
              <h2
                class="font-heading text-xl text-gray-700 tracking-tighter pb-4 border-b"
              >
                +91 00000-00000
              </h2>

              <h2
                class="font-heading mt-6 text-2xl text-gray-700 tracking-tighter"
              >
                Email:
              </h2>
              <p class="pb-4 border-b">madanenggworks@gmail.com</p>
            </div>

            <div class="inline-block">
              <p class="mb-6 tracking-tight">
                For More Details, Do not hesitate to contact our customer
                Relationship team. We are Available 24 X 7 to serve you and your
                requirements.
              </p>
              <div class="flex flex-wrap items-center -m-2">
                <div class="w-auto p-2">
                  <img
                    src="https://github.dev/basko-assets/images/contact/avatar.png"
                    alt=""
                  />
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="w-full md:w-1/2 p-8">
          <h1 class="font-heading mb-6 text-2xl text-gray-700 tracking-tighter"> Contact Us</h1>
          <div class="p-6 md:max-w-lg mx-auto bg-white rounded-2xl shadow-xl">
            <form
              @submit.prevent="submitForm"
              class="flex flex-wrap -m-2"
              id="contactForm"
              action="#"
            >
              <div class="w-full p-2">
                <label class="block">
                  <span class="inline-block mb-2 font-medium tracking-tight"
                    >Your Name</span
                  >
                  <input
                    v-model="name"
                    type="text"
                    id="name"
                    name="name"
                    class="p-4 w-full text-gray-500 tracking-tight placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg transition duration-200"
                    placeholder="Your Name"
                  />
                </label>
              </div>
              <div class="w-full p-2">
                <label class="block">
                  <span class="inline-block mb-2 font-medium tracking-tight"
                    >Email Address</span
                  >
                  <input
                    v-model="email"
                    type="email"
                    id="email"
                    name="email"
                    class="p-4 w-full text-gray-500 tracking-tight placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg transition duration-200"
                    placeholder="Email Address"
                  />
                </label>
              </div>
              <div class="w-full p-2">
                <label class="block">
                  <span class="inline-block mb-2 font-medium tracking-tight"
                    >Phone</span
                  >
                  <input
                    v-model="phone"
                    type="text"
                    id="phone"
                    name="phone"
                    class="p-4 w-full text-gray-500 tracking-tight placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg transition duration-200"
                    placeholder="Phone Number"
                  />
                </label>
              </div>
              <div class="w-full p-2">
                <label class="block">
                  <span class="inline-block mb-2 font-medium tracking-tight"
                    >Message</span
                  >
                  <textarea
                    v-model="message"
                    id="message"
                    name="message"
                    rows="7"
                    class="block p-4 w-full text-gray-500 placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg resize-none transition duration-200"
                    placeholder="Reason to Contact"
                  ></textarea>
                </label>
              </div>
              <div class="w-full p-2">
                <button
                  type="submit"
                  class="px-4 py-2 bg-green-500 text-white rounded-md"
                >
                  Send Message
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<!-- ... your template code ... -->

<script setup>
import { ref } from "vue";

const name = ref("");
const email = ref("");
const phone = ref("");
const message = ref("");

const submitForm = () => {
  const formData = {
    from_name: name.value,
    email_id: email.value,
    phone: phone.value,
    message: message.value,
  };

  // Store form data in local storage
  localStorage.setItem("quoteFormData", JSON.stringify(formData));

  // Send email using EmailJS (or another email service)
  // Note: This example uses EmailJS; you need to sign up and get your service credentials.
  // Replace 'user_id', 'service_id', and 'template_id' with your actual values.

  const emailjsParams = {
    service_id: "service_smwcr1s",
    template_id: "template_gf4comp",
    user_id: "jdn7ZQVQqpM1377K3",
    template_params: formData,
  };

  // Send email using EmailJS
  fetch("https://api.emailjs.com/api/v1.0/email/send", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify(emailjsParams),
  })
    .then((response) => {
      if (response.ok) {
        console.log("Email sent successfully");
        alert("Thank you! We will get back to you soon.");
      } else {
        console.error("Failed to send email. Status:", response.status);
        alert("Failed to send email. Please try again later.");
      }
    })
    .catch((error) => {
      console.error("Error sending email:", error);
      alert("Failed to send email. Please try again later.");
    });
};
</script>
