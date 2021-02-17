<template>
  <div id="app" :style='{ background: "url(" + background + ") no-repeat top right hsl(230, 100%, 99%)"}'>
    <div class="title" :style='{ background: "url(" + titleBackground + ") no-repeat center"}'>
      <h1>Simple, traffic based pricing</h1>
      <p>Sign-up for our 30 days trial. No credit card required</p>
    </div>
    <div class="card">

      <div class="top">
        <div class="infos">
          <p class="pageviews">100K pageviews</p>
          <p class="month"><span class="price">${{ price }}.00</span> / month</p>
        </div>
        <div class="sliderContainer">
          <input type="range" min="1" max="30" value="16" class="slider" @input="price = $event.target.value, progressBarWidth = $event.target.value * 3.3">
          <div class="progressBar" :style="{ width: progressBarWidth + '%' }"></div>
        </div>
        <div class="abbonement">
          <p>Monthly Billing</p>
          <label class="switch">
            <input type="checkbox">
            <span class="switchSlider round"></span>
          </label>
          <p class="year">yearly Billing <small>25% discount</small></p>
        </div>
      </div>

      <div class="bottom">
        <div class="left">
          <p><img src="@/assets/icon-check.svg" alt="check icon"> Unlimited websites</p>
          <p><img src="@/assets/icon-check.svg" alt="check icon"> 100% data ownership</p>
          <p><img src="@/assets/icon-check.svg" alt="check icon"> Email reports</p>
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
      titleBackground: require('@/assets/pattern-circles.svg'),
      price: 16,
      progressBarWidth: 50
    }
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@600;800&display=swap');
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    overflow-x: hidden;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 100vw;
    position: absolute;
    color:  hsl(225, 20%, 60%);
    font-family: 'Manrope', sans-serif;
  }
  p {
    font-weight: 600;
      font-size: 15px;
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
    padding: 20px;

    h1 {
      color: hsl(227, 35%, 25%);
    }
    p {
      margin-top: 10px;
    }
  }
  .card {
    max-width: 540px;
    height: auto;
    background-color: hsl(0, 0%, 100%);
    margin: 0 auto 100px auto;
    border-radius: 10px;
    box-shadow: #63636333 0px 6px 30px 0px;

    .infos, .abbonement, .bottom {
      display: flex;
      justify-content: space-between;
    }
    .top {
      border-bottom: 1px solid hsl(224, 65%, 95%);
      padding: 60px 45px 35px 45px;

      .pageviews {
        text-transform: uppercase;
        font-weight: 800;
        letter-spacing: 1px;
      }
      .month {
        display: flex;
        align-items: center;
        font-weight: 800;
        margin-top: -20px;
      }
      .price {
        color: hsl(227, 35%, 25%);
        font-weight: 800;
        font-size: 40px;
        margin: 0 10px 0 0;
      }
      .sliderContainer {
        width: 100%;
        position: relative;
        margin: 35px 0 50px 0;
      }
      .slider {
        width: 100%;
        -webkit-appearance: none;
        border: none;
        background: hsl(224, 65%, 95%);
        border-radius: 5px;
        outline: none;
        height: 8px;

        &::-webkit-slider-thumb {
          -webkit-appearance: none;
          appearance: none;
          width: 40px;
          height: 40px;
          border-radius: 50%; 
          background: hsl(174, 86%, 45%);
          box-shadow: hsl(174, 77%, 80%) 0px 15px 30px 5px;
          cursor: pointer;
          position: relative;
          z-index: 10;
          transition: .2s ease;
        }
        &::-moz-range-thumb {
          width: 40px;
          height: 40px;
          border-radius: 50%; 
          background: hsl(174, 86%, 45%);
          box-shadow: hsl(174, 77%, 80%) 0px 15px 30px 5px;
          cursor: pointer;
          position: relative;
          transition: .5s ease;
          border: none;
        }
      }
      .progressBar {
        height: 8px;
        border-radius: 5px;
        background: hsl(174, 86%, 45%);
        position: absolute;
        top: 9px;
        left: 0;
      }
      .abbonement {
        justify-content: flex-end;
        align-items: center;

        .year {
          display: flex;
          flex-wrap: wrap;
        }
        p {
          font-size: 13px;
        }
        .switch {
          margin: 0 20px;
          position: relative;
          display: inline-block;
          width: 50px;
          height: 25px;

          .switchSlider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: hsl(224, 35%, 85%);
            -webkit-transition: .4s;
            transition: .4s;
            height: 100%;
          }
          .switchSlider:before {
            position: absolute;
            content: "";
            height: 19px;
            width: 19px;
            left: 4px;
            bottom: 3px;
            background-color: white;
            -webkit-transition: .4s;
            transition: .4s;
          }
          input {
            display: none;
          }
          input:checked + .switchSlider {
            background-color: hsl(174, 86%, 45%);
          }

          input:focus + .switchSlider {
            box-shadow: 0 0 1px hsl(174, 86%, 45%);
          }
          input:checked + .switchSlider:before {
            -webkit-transform: translateX(110%);
            -ms-transform: translateX(110%);
            transform: translateX(110%);
          }
          .switchSlider.round {
            border-radius: 34px;
          }
          .switchSlider.round:before {
            border-radius: 50%;
          }
        }
        small {
          width: 78px;
          height: 18px;
          display: flex;
          justify-content: center;
          align-items: center;
          font-size: 10px;
          background: hsl(14, 92%, 95%);
          color:  hsl(15, 100%, 70%);
          border-radius: 8px;
          font-weight: 800;
          margin-left: 10px;
        }
      }
    }
    .bottom {
      align-items: center;
      padding: 27px 45px;

      .left {
        display: flex;
        flex-direction: column;

        p {
          font-size: 13px;
          margin: 5px 0 5px 0;
        }
      }
      button {
          width: 165px;
          height: 40px;
          background: hsl(227, 35%, 25%);
          color: hsl(226, 100%, 87%);
          border: none;
          outline: none;
          cursor: pointer;
          border-radius: 25px;
          font-weight: 800;
          transition: .5s ease;

          &:hover {
            color: hsl(230, 100%, 99%)
          }
        }
    }
  }

  @media screen and (max-width: 540px) {
    .card {
      margin: 0 25px;
      .top {
        padding: 60px 20px 35px 20px;
      }
      .infos, .bottom {
        flex-direction: column;
        text-align: center;
      }
      .infos .month {
        justify-content: center;
        margin-top: 5px;
      }
      .top .abbonement {
      justify-content: center;

        .year {
          width: 100px;
        }
        small {
          margin: 5px 0 0 0;
        }
      }
      .bottom {
        padding: 27px 20px;
        .right {
          margin-top: 15px;
        }
      }
    }
  }
</style>
