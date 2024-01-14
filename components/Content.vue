<template>
  <div class="relative pt-12 lg:pt-20 lg:pb-20">
    <img
      class="hidden lg:block absolute inset-0 w-full"
      src="https://shuffle.dev/atis-assets/background/lines.svg"
      alt=""
    />
    <div
      class="hidden lg:block absolute inset-0 w-full bg-cover"
      style="
        background-image: url('https://shuffle.dev/atis-assets/background/lines.svg');
        z-index: -1;
      "
    ></div>

    <div class="container mx-auto relative z-10">
      <div class="flex flex-wrap">
        <div class="w-full px-4 mb-12 flex items-center">
          <div class="w-full text-center justify-center">
            <h2 class="mb-3 text-4xl lg:text-5xl font-bold font-heading">
              <span>Printing, Packaging, and Die Punching </span>
              <span class="text-green-600">Machinery</span>
            </h2>
            <p class="mb-6 text-gray-400 leading-loose">
              We stand as the foremost manufacturers and exporters of
              cutting-edge Printing, Packaging, and Die Punching Machinery.
            </p>

            <div class="max-w-sm mx-auto">
              <div>
                <nuxt-link
                  to="/quote"
                  class="inline-block mb-3 lg:mb-0 lg:mr-3 w-full lg:w-auto py-2 px-6 leading-loose bg-green-600 hover:bg-green-700 text-white font-semibold rounded-l-xl rounded-t-xl transition duration-200"
                  >Get A Quotation</nuxt-link
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Your existing code for navbar-menu -->
    <div
      class="hidden navbar-menu fixed top-0 left-0 bottom-0 w-5/6 max-w-sm z-50"
    >
      <nav
        class="relative flex flex-col py-6 px-6 h-full w-full bg-white border-r overflow-y-auto"
      ></nav>
    </div>
  </div>
</template>
