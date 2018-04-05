<template>
  <div class="container my-5">
    <div class="row">
      <div class="col">
        <div class="card">
          <div class="card-body">

            <div class="row">
              <transition appear name="weight">
                <div class="col text-center">
                  <ul class="list-inline">
                    <li class="list-inline-item"><h3><span class="badge badge-danger">Золото</span></h3></li>
                    <li class="list-inline-item"><h3><span class="badge badge-light"><a href="#" @click.prevent>Скупка</a></span></h3></li>
                  </ul>
                </div>
              </transition>
            </div>

            <div class="row mb-2">
              <div class="col-lg-6">
                <transition appear name="weight">
                  <div class="card h-100">
                    <div class="card-body">
                      <h4 class="text-danger text-center mb-0">Вес, г.</h4>
                      <VueSlideBar
                        v-model="sliderWeight.value"
                        :min="1"
                        :max="10"
                        :processStyle="sliderWeight.processStyle"
                        :lineHeight="sliderWeight.lineHeight"
                        :tooltipStyles="{ backgroundColor: 'red', borderColor: 'red' }">
                      </VueSlideBar>
                    </div>
                  </div>
                </transition>
              </div>
              <div class="col-lg-6">
                <transition appear name="loanterm">
                  <div class="card h-100">
                    <div class="card-body">
                      <h4 class="text-danger text-center mb-4">Срок займа</h4>
                      <div class="row">
                        <div class="col text-center">
                          <div class="form-check form-check-inline">
                            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" value="31" v-model="loanTerm">
                            <label class="form-check-label lead mt-1" for="inlineRadio1">31 день</label>
                          </div>
                        </div>
                        <div class="col text-center">
                          <div class="form-check form-check-inline">
                            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" value="51" v-model="loanTerm">
                            <label class="form-check-label lead mt-1" for="inlineRadio2">51 день</label>
                          </div>
                        </div>
                      </div>                    
                    </div>
                  </div>
                </transition>
              </div>
            </div>

            <div class="row my-3">
              <div class="col">
                <transition appear name="goldcontent">
                  <div class="card">
                    <div class="card-body">
                      <h4 class="text-danger text-center mb-0">Проба</h4>
                      <VueSlideBar
                        v-model="sliderGoldContent.value"
                        :data="sliderGoldContent.data"
                        :range="sliderGoldContent.range"
                        :min="1"
                        :max="10"
                        :processStyle="sliderWeight.processStyle"
                        :lineHeight="sliderWeight.lineHeight"
                        :tooltipStyles="{ backgroundColor: 'red', borderColor: 'red' }">
                      </VueSlideBar>
                    </div>
                  </div>
                </transition>
              </div>
            </div>

            <div class="row my-3">
              <div class="col-md-4">
                <transition appear name="dailypayment">
                  <div class="card h-100 bg-dark text-white">
                    <div class="card-body">
                      <h5>Ежедневный платёж, руб.</h5>
                      <p class="display-4 mb-0">{{ dailyPayment }}</p>
                    </div>
                  </div>
                </transition>
              </div>
              <div class="col-md-4">
                <transition appear name="total">
                  <div class="card h-100 bg-primary text-white">
                    <div class="card-body">
                      <h5>Сумма, руб.</h5>
                      <p class="display-4 mb-0">{{ total }}</p>
                    </div>
                  </div>
                </transition>
              </div>
              <div class="col-md-4">
                <transition appear name="interestRate">
                  <div class="card h-100 bg-danger text-white">
                    <div class="card-body">
                      <h5>Процентная ставка</h5>
                      <p class="display-4 mb-0">{{ interestRate }} %</p>
                    </div>
                  </div>
                </transition>
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
      loanTerm: 31,
      sliderWeight: {
        value: 5,
        lineHeight: 15,
        processStyle: {
          backgroundColor: '#333'
        }
      },
      sliderGoldContent: {
        value: 750,
        data: [
          375,
          500,
          583,
          750,
          850,
          900,
          958
        ],
        range: [
          { label: '375' },
          { label: '500' },
          { label: '583' },
          { label: '750' },
          { label: '850' },
          { label: '900' },
          { label: '958' }
        ]
      }
    }
  },
  computed: {
    dailyPayment() {
      return this.sliderWeight.value * 1 + parseInt(this.loanTerm) + this.sliderGoldContent.value
    },
    total() {
      return this.sliderWeight.value * 2 + parseInt(this.loanTerm) + this.sliderGoldContent.value
    },
    interestRate() {
      return this.sliderWeight.value * 3 + parseInt(this.loanTerm) + this.sliderGoldContent.value
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.weight-enter-active, .weight-leave-active {
  transition: opacity 1.5s;
}
.weight-enter, .weight-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}

.loanterm-enter-active, .loanterm-leave-active {
  transition: opacity 1.5s .5s;
}
.loanterm-enter, .loanterm-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}

.goldcontent-enter-active, .goldcontent-leave-active {
  transition: opacity 1.5s 1s;
}
.goldcontent-enter, .goldcontent-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}


.dailypayment-enter-active, .dailypayment-leave-active {
  transition: all 1.5s ease 1.5s;
}
.dailypayment-enter, .dailypayment-leave-to
/* .slide-fade-leave-active до версии 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

.total-enter-active, .total-leave-active {
  transition: all 1.5s ease 2s;
}
.total-enter, .total-leave-to
/* .slide-fade-leave-active до версии 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

.interestRate-enter-active, .interestRate-leave-active {
  transition: all 1.5s ease 2.5s;
}
.interestRate-enter, .interestRate-leave-to
/* .slide-fade-leave-active до версии 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>
