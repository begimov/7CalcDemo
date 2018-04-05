<template>
  <div id="app">
    <div class="container my-5">
    <div class="row">
      <div class="col">
        <div class="card">
          <div class="card-body">
            
            <div class="row">
              <transition appear name="weight">
                <div class="col text-center">
                  <ul class="list-inline">
                    <li class="list-inline-item">
                      <h3>
                        <span class="badge badge-danger">
                          <a href="#" class="text-white" @click.prevent="activeComponent = 'pawnshop'">Золото</a>
                        </span>
                      </h3>
                    </li>
                    <li class="list-inline-item">
                      <h3>
                        <span class="badge badge-light">
                          <a href="#" @click.prevent="activeComponent = 'purchase'">Скупка</a>
                        </span>
                      </h3>
                    </li>
                  </ul>
                </div>
              </transition>
            </div>

            <Calcpawnshop v-if="activeComponent == 'pawnshop'"/>

          </div>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import Calcpawnshop from './components/Calcpawnshop'

export default {
  name: 'App',
  components: {
    Calcpawnshop
  },
  data() {
    return {
      activeComponent: 'pawnshop'
    }
  }
}
</script>

<style>
.weight-enter-active,
.weight-leave-active {
  transition: opacity 1s;
}
.weight-enter,
.weight-leave-to {
  opacity: 0;
}
</style>
