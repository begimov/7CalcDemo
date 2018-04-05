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
                        <span :class="{
                            'badge': true, 
                            'badge-danger': activeComponent == 'pawnshop',
                            'badge-light': activeComponent == 'purchase'
                          }">
                          <a href="#" 
                            :class="{'text-white': activeComponent == 'pawnshop'}" 
                            @click.prevent="activeComponent = 'pawnshop'">Золото</a>
                        </span>
                      </h3>
                    </li>
                    <li class="list-inline-item">
                      <h3>
                        <span :class="{
                            'badge': true, 
                            'badge-danger': activeComponent == 'purchase',
                            'badge-light': activeComponent == 'pawnshop'
                          }">
                          <a href="#" 
                            :class="{'text-white': activeComponent == 'purchase'}" 
                            @click.prevent="activeComponent = 'purchase'">Скупка</a>
                        </span>
                      </h3>
                    </li>
                  </ul>
                </div>
              </transition>
            </div>

            <Calcpawnshop v-if="activeComponent == 'pawnshop'"/>
            <Calcpurchase v-if="activeComponent == 'purchase'"/>

          </div>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import Calcpawnshop from './components/Calcpawnshop'
import Calcpurchase from './components/Calcpurchase'

export default {
  name: 'App',
  components: {
    Calcpawnshop,
    Calcpurchase
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
