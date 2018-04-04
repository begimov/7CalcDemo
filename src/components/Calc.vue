<template>
  <div class="container my-5">
    <div class="row">
      <div class="col">
        <div class="card">
          <div class="card-body">

            <div class="row">
              <div class="col">
                <ul class="list-inline">
                  <li class="list-inline-item"><h3><span class="badge badge-danger">Золото</span></h3></li>
                  <li class="list-inline-item"><h3><span class="badge badge-light"><a href="#" @click.prevent>Скупка</a></span></h3></li>
                </ul>
              </div>
            </div>

            <div class="row mb-2">
              <div class="col">
                <div class="card">
                  <div class="card-body">
                    <h4 class="text-danger mb-0">Вес</h4>
                    <VueSlideBar
                      v-model="weight"
                      :min="1"
                      :max="10"
                      :processStyle="slider.processStyle"
                      :lineHeight="slider.lineHeight"
                      :tooltipStyles="{ backgroundColor: 'red', borderColor: 'red' }">
                    </VueSlideBar>
                  </div>
                </div>
              </div>
            </div>

            <div class="row mb-2">
              <div class="col">
                <div class="card">
                  <div class="card-body">
                    <h4 class="text-danger">Срок займа</h4>
                  </div>
                </div>
              </div>
            </div>

            <div class="row mb-2">
              <div class="col">
                <div class="card">
                  <div class="card-body">
                    <h5>Ежедневный платёж</h5>
                  </div>
                </div>
              </div>
              <div class="col">
                <div class="card">
                  <div class="card-body">
                    <h5>Сумма</h5>
                  </div>
                </div>
              </div>
              <div class="col">
                <div class="card">
                  <div class="card-body">
                    <h5>Процентная ставка</h5>
                  </div>
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueSlideBar from 'vue-slide-bar'

export default {
  name: 'Calc',
  components: {
    VueSlideBar
  },
  data () {
    return {
      weight: 5,
      slider: {
        lineHeight: 15,
        processStyle: {
          backgroundColor: '#333'
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
