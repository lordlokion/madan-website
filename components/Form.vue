<template>
    <div class="w-full md:w-1/2 p-8">
      <div class="p-6 md:max-w-lg mx-auto bg-white rounded-2xl shadow-xl">
        <form @submit.prevent="submitForm" class="flex flex-wrap -m-2" id="contactForm" action="#">
          <div class="w-full p-2">
            <label class="block">
              <span class="inline-block mb-2 font-medium tracking-tight">Your Name</span>
              <input v-model="name" type="text" id="name" name="name" class="p-4 w-full text-gray-500 tracking-tight placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg transition duration-200" placeholder="Your Name" />
            </label>
          </div>
          <div class="w-full p-2">
            <label class="block">
              <span class="inline-block mb-2 font-medium tracking-tight">Email Address</span>
              <input v-model="email" type="email" id="email" name="email" class="p-4 w-full text-gray-500 tracking-tight placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg transition duration-200" placeholder="Email Address" />
            </label>
          </div>
          <div class="w-full p-2">
            <label class="block">
              <span class="inline-block mb-2 font-medium tracking-tight">Phone</span>
              <input v-model="phone" type="text" id="phone" name="phone" class="p-4 w-full text-gray-500 tracking-tight placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg transition duration-200" placeholder="Phone Number" />
            </label>
          </div>
          <div class="w-full p-2">
            <label class="block">
              <span class="inline-block mb-2 font-medium tracking-tight">Message</span>
              <textarea v-model="message" id="message" name="message" rows="7" class="block p-4 w-full text-gray-500 placeholder-gray-500 outline-none border border-gray-300 focus:border-gray-700 rounded-lg resize-none transition duration-200" placeholder="Reason to Contact"></textarea>
            </label>
          </div>
          <div class="w-full p-2">
            <button type="submit" class="px-4 py-2 bg-green-500 text-white rounded-md">Get Quote</button>
          </div>
        </form>
      </div>
    </div>
  </template>
  
  
  <script setup>
  import { ref } from 'vue';
  
  const name = ref('');
  const email = ref('');
  const phone = ref('');
  const message = ref('');
  
  const submitForm = () => {
    const formData = {
      from_name: name.value,
      email_id: email.value,
      phone: phone.value,
      message: message.value,
    };
  
    // Store form data in local storage
    localStorage.setItem('quoteFormData', JSON.stringify(formData));
  
    // Send email using EmailJS (or another email service)
    // Note: This example uses EmailJS; you need to sign up and get your service credentials.
    // Replace 'user_id', 'service_id', and 'template_id' with your actual values.
  
    const emailjsParams = {
      service_id: 'service_smwcr1s',
      template_id: 'template_gf4comp',
      user_id: 'jdn7ZQVQqpM1377K3',
      template_params: formData,
    };
  
    // Send email using EmailJS
    fetch('https://api.emailjs.com/api/v1.0/email/send', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(emailjsParams),
  })
    .then(response => {
      if (response.ok) {
        console.log('Email sent successfully');
        alert('Thank you! We will get back to you soon.');
      } else {
        console.error('Failed to send email. Status:', response.status);
        alert('Failed to send email. Please try again later.');
      }
    })
    .catch(error => {
      console.error('Error sending email:', error);
      alert('Failed to send email. Please try again later.');
    });
  
  };
  </script>
  