<template>
  <div>
    
    <div class="row mb-2">
      <div class="col">
        <transition appear name="weight">
          <div class="card h-100">
            <div class="card-body">
              <h4 class="text-danger text-center mb-0">Вес, гр.</h4>
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
    </div>

    <div class="row my-3">
      <div class="col">
        <transition appear name="goldcontent">
          <div class="card">
            <div class="card-body">
              <h4 class="text-danger text-center mb-0">Проба / цена за гр.</h4>
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
      <div class="col-lg-3 col-sm-6 my-1">
        <transition appear name="total">
          <div class="card h-100 bg-primary text-white">
            <div class="card-body p-3">
              <p class="font-weight-bold">Сумма на руки, руб.</p>
              <p class="display-4">{{ total }}</p>
            </div>
          </div>
        </transition>
      </div>
      <div class="col-lg-3 col-sm-6 my-1">
        <transition appear name="interestRate">
          <div class="card h-100 bg-light">
            <div class="card-body p-3">
              <p class="font-weight-bold">Процентная ставка</p>
              <p class="mb-0 text-danger"><span class="badge badge-danger">С промо-кодом:</span></p><h2 class="mb-1 font-weight-light text-danger">{{ interestRate.withPromoCode }} %</h2>
              <p class="mb-0"><span class="badge badge-dark">Без промо-кода:</span></p><h2 class="mb-0 font-weight-light">{{ interestRate.withoutPromoCode }} %</h2>
            </div>
          </div>
        </transition>
      </div>
      <div class="col-lg-3 col-sm-6 my-1">
        <transition appear name="dailypayment">
          <div class="card h-100 bg-light">
            <div class="card-body p-3">
              <p class="font-weight-bold">Ежедневный платёж, руб.</p>
              <h2 class="mb-1 font-weight-light text-danger">{{ dailyPaymentWithPromoCode }}</h2>
              <h2 class="mb-0 font-weight-light">{{ dailyPaymentWithoutPromoCode }}</h2>
            </div>
          </div>
        </transition>
      </div>
      <div class="col-lg-3 col-sm-6 my-1">
        <transition appear name="totalinterest">
          <div class="card h-100 bg-light">
            <div class="card-body p-3">
              <p class="font-weight-bold">Сумма процентов на весь срок, руб.</p>
              <h2 class="mb-1 font-weight-light text-danger">{{ totalInterestWithPromoCode }}</h2>
              <h2 class="mb-0 font-weight-light">{{ totalInterestWithoutPromoCode }}</h2>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import VueSlideBar from "vue-slide-bar";

export default {
  name: "Calcpawnshop",
  components: {
    VueSlideBar
  },
  data() {
    return {
      interestRate: {
        withoutPromoCode: 0.39,
        withPromoCode: 0.38
      },
      loanTerm: 31,
      sliderWeight: {
        value: 5,
        lineHeight: 15,
        processStyle: {
          backgroundColor: "#333"
        }
      },
      sliderGoldContent: {
        value: 1875,
        data: [930, 1250, 1465, 1875, 2125, 2250, 2395],
        range: [
          { label: "375" },
          { label: "500" },
          { label: "583" },
          { label: "750" },
          { label: "850" },
          { label: "900" },
          { label: "958" }
        ]
      }
    };
  },
  computed: {
    total() {
      return this.sliderWeight.value * this.sliderGoldContent.value;
    },
    dailyPaymentWithPromoCode() {
      return (
        this.total *
        this.interestRate.withPromoCode /
        this.loanTerm
      ).toFixed(2);
    },
    dailyPaymentWithoutPromoCode() {
      return (
        this.total *
        this.interestRate.withoutPromoCode /
        this.loanTerm
      ).toFixed(2);
    },
    totalInterestWithPromoCode() {
      return (this.total * this.interestRate.withPromoCode).toFixed(2);
    },
    totalInterestWithoutPromoCode() {
      return (this.total * this.interestRate.withoutPromoCode).toFixed(2);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.goldcontent-enter-active,
.goldcontent-leave-active {
  transition: opacity 1s .25s;
}
.goldcontent-enter,
.goldcontent-leave-to {
  opacity: 0;
}

.total-enter-active,
.total-leave-active {
  transition: all 1s ease .5s;
}
.total-enter,
.total-leave-to {
  transform: translateX(10px);
  opacity: 0;
}

.interestRate-enter-active,
.interestRate-leave-active {
  transition: all 1s ease 0.75s;
}
.interestRate-enter,
.interestRate-leave-to {
  transform: translateX(10px);
  opacity: 0;
}

.dailypayment-enter-active,
.dailypayment-leave-active {
  transition: all 1s ease 1s;
}
.dailypayment-enter,
.dailypayment-leave-to {
  transform: translateX(10px);
  opacity: 0;
}

.totalinterest-enter-active,
.totalinterest-leave-active {
  transition: all 1s ease 1.25s;
}
.totalinterest-enter,
.totalinterest-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
</style>
