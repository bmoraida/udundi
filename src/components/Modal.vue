<template>
  <Teleport to="body">
    <Transition name="modal-outer">
      <div
        v-show="modalActive"
        class="absolute w-full h-screen top-0 left-0 flex flex-col justify-center px-8"
      >
        <Transition name="modal-inner">
          <div
            v-if="modalActive"
            class="p-12 bg-white self-start max-w-prose max-h-[80%] shadow-md overflow-scroll md:overflow-hidden modal"
          >
            <div class="flex justify-end">
              <button class="fg-explore-primary" @click="$emit('close-modal')">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 384 512"
                  class="text-explore-primary icon"
                >
                  <path
                    d="M376.6 84.5c11.3-13.6 9.5-33.8-4.1-45.1s-33.8-9.5-45.1 4.1L192 206 56.6 43.5C45.3 29.9 25.1 28.1 11.5 39.4S-3.9 70.9 7.4 84.5L150.3 256 7.4 427.5c-11.3 13.6-9.5 33.8 4.1 45.1s33.8 9.5 45.1-4.1L192 306 327.4 468.5c11.3 13.6 31.5 15.4 45.1 4.1s15.4-31.5 4.1-45.1L233.7 256 376.6 84.5z"
                  />
                </svg>
              </button>
            </div>
            <div class="text-black">
              <h2
                class="text-5xl font-bold mb-4 text-explore-primary font-serif"
              >
                Explore
              </h2>
              <p class="mb-2">
                Sed ut perspiciatis unde omnis iste natus error sit voluptatem
                accusantium doloremque laudantium, totam rem aperiam, eaque ipsa
                quae ab illo inventore veritatis et quasi architecto beatae
                vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia
                voluptas sit aspernatur aut odit aut fugit, sed quia
                consequuntur magni dolores eos qui ratione voluptatem sequi
                nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor
                sit amet, consectetur, adipisci velit, sed quia non numquam eius
                modi tempora incidunt ut labore et dolore magnam aliquam quaerat
                voluptatem. Ut enim ad minima veniam, quis nostrum
                exercitationem ullam corporis suscipit laboriosam, nisi ut
                aliquid ex ea commodi consequatur?
              </p>
            </div>
            <button
              class="text-white mt-4 py-2 px-6 read-more"
              @click="$emit('close-modal')"
            >
              Read More
            </button>
          </div>
        </Transition>
      </div>
    </Transition>
  </Teleport>
</template>

<script setup>
defineEmits(["close-modal"]);
defineProps({
  modalActive: {
    type: Boolean,
    default: false,
  },
});
</script>

<style scoped>
/* Modal container */
.modal-outer-enter-from,
.modal-outer-leave-to {
  opacity: 0;
}
.modal-outer-enter-active {
  transition: opacity 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-outer-leave-active {
  transition: opacity 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02) 1s;
}

/* Modal Inner */
@media (width >= 1250px) {
  .modal {
    position: absolute;
    bottom: 10%;
    left: 10%;
    translate: (50%, 50%);
  }
}
@media (width <= 1250px) {
  .icon-container {
    stroke: green;
  }
}

.modal-inner-enter-from,
.modal-inner-leave-to {
  opacity: 0;
  transform: scale(0.1);
  border-radius: 10rem;
}

.modal-inner-enter-active {
  transition: all 0.7s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.1s,
    border-radius 0.7s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.1s;
  /* border-radius: 0%; */
}

.modal-inner-leave-active {
  transition: all 0.7s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.1s;
}

/* Modal Button */
.read-more {
  /* background-color: explore-primary; */
  background: linear-gradient(90deg, #611818 0%, #a36754 100%);
}

/* Close Icon */
.icon {
  width: 1em;
  height: 1em;
  vertical-align: 0.125em;
  fill: #611818;
}
</style>
