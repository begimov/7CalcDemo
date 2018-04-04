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
                    <div class="form-check form-check-inline">
                      <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" value="option1">
                      <label class="form-check-label lead mt-1" for="inlineRadio1">31 день</label>
                    </div>
                    <div class="form-check form-check-inline">
                      <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" value="option2">
                      <label class="form-check-label lead mt-1" for="inlineRadio2">51 день</label>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <div class="row mb-2">
              <div class="col-md-4">
                <div class="card h-100 bg-dark text-white">
                  <div class="card-body">
                    <h5>Ежедневный платёж</h5>
                    <p class="lead mb-0">{{ dailyPayment }}</p>
                  </div>
                </div>
              </div>
              <div class="col-md-4">
                <div class="card h-100 bg-primary text-white">
                  <div class="card-body">
                    <h5>Сумма</h5>
                    <p class="lead mb-0">{{ total }}</p>
                  </div>
                </div>
              </div>
              <div class="col-md-4">
                <div class="card h-100 bg-danger text-white">
                  <div class="card-body">
                    <h5>Процентная ставка</h5>
                    <p class="lead mb-0">{{ interestRate }}</p>
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
  },
  computed: {
    dailyPayment() {
      return this.weight * 1
    },
    total() {
      return this.weight * 2
    },
    interestRate() {
      return this.weight * 3
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
