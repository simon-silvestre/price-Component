<template>
  <div id="app" :style='{ background: "url(" + background + ") no-repeat top right hsl(230, 100%, 99%)"}'>
    <div class="title" :style='{ background: "url(" + titleBackground + ") no-repeat center"}'>
      <h1>Simple, traffic based pricing</h1>
      <p>Sign-up for our 30 days trial. No credit card required</p>
    </div>
    <div class="card">

      <div class="top">
        <div class="infos">
          <p>100K pageviews</p>
          <p><span>$16.00</span>/ month</p>
        </div>
        <div class="slider">

        </div>
        <div class="abbonement">
          <p>Monthly Billing</p>
          <input type="checkbox" name="switch">
          <small>25% discount</small>
        </div>
      </div>

      <div class="bottom">
        <div class="left">
          <p><span>logo</span> Unlimited websites</p>
          <p><span>logo</span> 100% data ownership</p>
          <p><span>logo</span> Email reports</p>
        </div>
        <div class="right">
          <button>Start my trial</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      background: require('@/assets/bg-pattern.svg'),
      titleBackground: require('@/assets/pattern-circles.svg')
    }
  }
}
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
    width: 100vw;
    position: absolute;
  }
  .title {
    margin: 75px auto;
    width: fit-content;
    text-align: center;
    font-weight: 800;
    height: 150px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    p {
      margin-top: 15px;
      color:  hsl(225, 20%, 60%);
      font-weight: 600;
      font-size: 15px;
    }
  }
  .card {
    width: 540px;
    height: 400px;
    background-color: hsl(0, 0%, 100%);
    margin: 0 auto;
    padding: 50px;
    border-radius: 8px;
    box-shadow: #63636333 0px 6px 30px 0px;

    .infos, .abbonement, .bottom {
      display: flex;
      justify-content: space-between;
    }
    .top {
      margin-bottom: 30px;
      border-bottom: 1px solid hsl(225, 20%, 60%);
    }
    .bottom {
      align-items: center;
      
    
    }
  }
</style>
