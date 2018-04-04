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
                    <h4 class="text-danger">Вес</h4>
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
export default {
  name: 'Calc',
  data () {
    return {
      //
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
