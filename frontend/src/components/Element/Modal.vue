<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">

          <div class="modal-header">
            <slot name="header">
              <font-awesome-icon 
                @click="$emit('close-modal')"
                size="2x" 
                class="mouse-pointer text-secondary btn exit-font" 
                @mouseover="closeIcon = ['fas', 'times-circle']" 
                @mouseleave="closeIcon = ['far', 'times-circle']" 
                :icon="closeIcon" 
              />
            </slot>
          </div>

          <div class="modal-body">
            <slot name="body" :modalName="modalName">
              default body
            </slot>
          </div>

          <!-- <div class="modal-footer">
            <slot name="footer">
            </slot> -->
          <!-- </div> -->
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      modalName: "Book",
      closeIcon: ['far', 'times-circle'],
    }
  },
  methods: {
    closeModal() {
      this.$emit('close-modal')
    }
  }
}
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.315);
  display: table;
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 1000px;
  height: 800px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: rgb(255, 255, 255);
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: Helvetica, Arial, sans-serif;
  border-radius: 10px/ 10px;
  color: rgb(0, 0, 0);
}

.modal-header {
  margin-top: 0;
  color: #42b983;
  border-bottom: 0px;
  justify-content: flex-end;
  padding: 0px;
  float: right;
}

.exit-font {
  float: right; 
  width: 70px;
  height: 70px;
  z-index: 10;
}

.modal-body {
  margin: 0px;
  padding-top: 0px;
}

.modal-default-button {
  float: right;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>