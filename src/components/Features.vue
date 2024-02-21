<template>
  <div class="Features">
    <div
      class="animation container"
      style="
        display: flex;
        align-items: center;
        gap: 10px;
        justify-content: space-between;
        width: 90%;
        margin: 45px auto 0;
      "
    ></div>
    <div
      class="section"
      style="margin-top: -45px; background: #a231ff; padding: 30px 10px 50px"
    >
      <div class="container flex align-center justify-center feat_container">
        <div
          class="feat flex align-center justify-center flex-col w-32 animated-div-1"
        >
          <img
            src="../assets/_96f54fef-ee67-4c08-8acf-b9c399cda9a0.jpg"
            alt="exam"
            class="img"
          />
          <div class="caption_1">شاهد دروسك اكثر من مرة</div>
        </div>
        <div
          class="feat flex align-center justify-center flex-col w-32 animated-div-2"
        >
          <img
            src="../assets/_245d1ad2-94b1-4d5c-afea-0cc76b086816.jpg"
            alt="test"
            class="img"
          />
          <div class="caption_2">وفر وقت المواصلات و السنتر</div>
        </div>
        <div
          class="feat flex align-center justify-center flex-col w-32 animated-div-3"
        >
          <img
            src="../assets/_972574ad-e2e2-406c-845a-ed4502d7c140.jpg"
            alt="clock"
            class="img"
          />
          <div class="caption_3">امتحانات دورية و مستمرة</div>
        </div>
      </div>
    </div>

    <div
      class="container-0"
      style="margin-top: -43px; z-index: 99; position: relative"
    >
      <div
        class="test-tube"
        style="margin-top: -43px; z-index: 1; position: relative"
      >
        <div class="line-top">
          <span class="line-top__line1"></span>
          <span class="line-top__line2"></span>
        </div>

        <div class="top"></div>

        <div class="liquid">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
            <path
              fill="#a231ff"
              fill-opacity="1"
              d="M0,192L80,208C160,224,320,256,480,234.7C640,213,800,139,960,117.3C1120,96,1280,128,1360,144L1440,160L1440,320L1360,320C1280,320,1120,320,960,320C800,320,640,320,480,320C320,320,160,320,80,320L0,320Z"
            ></path>
          </svg>
          <div class="liquid__bottom">
            <div v-for="color in AllColor" :key="color" class="color"></div>
          </div>
        </div>

        <div class="tube"></div>
      </div>
      <a href="https://dribbble.com/myacode" class="dribbble" target="_blank"
        ><ion-icon name="logo-dribbble"></ion-icon
      ></a>
      <img
        src="../assets/_a5414e18-965b-4c41-9d96-575e60c5e625.jpg"
        alt=""
        style="
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 95%;
          z-index: 0;
        "
      />

      <!-- partial:index.partial.html -->
      <div class="holder">
        <div class="candle">
          <div class="blinking-glow"></div>
          <div class="thread"></div>
          <div class="glow"></div>
          <div class="flame"></div>
        </div>
      </div>
      <!-- partial -->
      <img
        src="../assets/walnut wood texture.jpg"
        style="
          width: 100%;
          height: 50px;
          position: relative;
          top: -35px;
          z-index: 1;
        "
        alt=""
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "TheFeatures",

  data() {
    return {
      isScrollingUp: false,
      isScrollingDown: false,
      scrollPosition: 0,
      elementColor: "#3498db",
      AllColor: 30,
    };
  },
  mounted() {
    // setTimeout(() => {
    function hslColors() {
      let colors = [];
      let hue = Math.floor(Math.random() * (320 - 153) + 153);
      let saturation = Math.floor(Math.random() * (100 - 90) + 90);
      let lightness = Math.floor(Math.random() * (80 - 70) + 70);
      colors.push(`hsl(${hue},${saturation}%, ${lightness}%)`);
      return colors;
    }
    // function width() {

    // animation: move-1 10s infinite;

    // }
    // function colors() {}
    let colors = document.querySelectorAll(".color");
    let i;
    for (i = 0; i < colors.length; i++) {
      let width = Math.floor(Math.random() * (40 - 6 + 1)) + 6;
      let bottom = Math.floor(Math.random() * (60 - 6 + 1)) + 15;
      let left = Math.floor(Math.random() * (80 - 6 + 1)) + 6;
      colors[i].style.cssText = `
background: ${hslColors()}; width: ${width}px ;height:${width}px; bottom: ${bottom}px;
  left: ${left}px ;border-radius: 50%;
  position: absolute;animation-delay: ${-1 * 0.2}s;
`;
      //       let template = `
      //     <div class="color" style="background: ${hslColors()}; width: ${width}px ;height:${width}px; bottom: ${bottom}px;
      //   left: ${left}px ;border-radius: 50%;
      //   position: absolute;animation-delay: ${
      //     -1 * 0.2
      //   }s;animation: move-1 10s infinite;@keyframes move-1 {
      //   100% {
      //     transform: translateY(calc(random(30) * -1rem));opacity: 0;
      //   }
      // }">       </div>
      //     `;
      // container.innerHTML += template;
    }
    // }, 2000);
    window.addEventListener("scroll", () => {
      if (
        window.scrollY >= 580 &&
        document.querySelectorAll(".feat_container .feat > div")[0]
      ) {
        document
          .querySelectorAll(".feat_container .feat > div")
          .forEach((e) => {
            e.style.cssText = `top: 10px !important;transform: rotate(0deg)!important`;
          });
        // document.querySelectorAll(
        //   ".feat_container .feat > div"
        // )[0].style.background = "rgb(255 108 100);";
        document.querySelectorAll(
          ".feat_container .feat > div  "
        )[0].style.color = " #fe7566 !important";
        // document.querySelectorAll(
        //   ".feat_container .feat > div"
        // )[1].style.background = " #017296 ";
        document.querySelectorAll(
          ".feat_container .feat > div"
        )[1].style.color = "  #fff ";
        ("#fff5f5");
        // document.querySelectorAll(
        //   ".feat_container .feat > div"
        // )[2].style.background = " #4a98f7 ";
        document.querySelectorAll(
          ".feat_container .feat > div"
        )[2].style.color = "  #fff ";
        document
          .querySelectorAll(".feat_container .feat > div")
          .forEach((e) => {
            e.style.cssText = `backgroundColor:#fff`;
          });
      } else if (window.scrollY < 580) {
        document
          .querySelectorAll(".feat_container .feat > div")
          .forEach((e) => {
            e.style.cssText = `transform: rotate(7deg)!important`;
          });
        if (document.querySelector(".caption_2")) {
          document.querySelector(
            ".caption_2"
          ).style.cssText = `transform: rotate(-7deg)!important`;
        }
      }
    });
  },
};
</script>
<style lang="scss" scoped>
.Features {
  // background-image: url("../assets/seamless-chemical-pattern-chemical-glassware-and-vector-6012334.jpg");
  // background-size: cover;
  // background-position: center top;
  // background-attachment: fixed;
  width: 100%;
  z-index: 200;
  // height: 500px;
}
@import url("https://fonts.googleapis.com/css?family=Ubuntu:400,400i,700,700i");

header,
footer {
  display: block;
}

a,
a:link,
a:visited {
  text-decoration: none;
}

img {
  border: 0;
}

ul {
  list-style: none;
}

.center {
  width: 1170px;
  margin: 20px auto 0;
}

.holder {
  margin: 12rem auto 0;
  width: 100%;
  height: 253px;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
}

.holder *,
.holder *:before,
.holder *:after {
  position: absolute;
  content: "";
}

.candle {
  bottom: 0;
  width: 150px;
  height: 239px;
  border-radius: 150px / 40px;
  box-shadow: inset 20px -30px 50px 0 rgba(0, 0, 0, 0.4),
    inset -20px 0 50px 0 rgba(0, 0, 0, 0.4);
  background: #190f02;
  background: -moz-linear-gradient(
    #e48825,
    #e78e0e,
    #833c03,
    #4c1a03 50%,
    #1c0900
  );
  background: -webkit-linear-gradient(
    #e48825,
    #e78e0e,
    #833c03,
    #4c1a03 50%,
    #1c0900
  );
  background: -o-linear-gradient(
    #e48825,
    #e78e0e,
    #833c03,
    #4c1a03 50%,
    #1c0900
  );
  background: -ms-linear-gradient(
    #e48825,
    #e78e0e,
    #833c03,
    #4c1a03 50%,
    #1c0900
  );
  background: linear-gradient(#e48825, #e78e0e, #833c03, #4c1a03 50%, #1c0900);
}

.candle:before {
  width: 100%;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #d47401;
  background: #b86409;
  background: -moz-radial-gradient(#eaa121, #8e4901 45%, #b86409 80%);
  background: -webkit-radial-gradient(#eaa121, #8e4901 45%, #b86409 80%);
  background: -o-radial-gradient(#eaa121, #8e4901 45%, #b86409 80%);
  background: -ms-radial-gradient(#eaa121, #8e4901 45%, #b86409 80%);
  background: radial-gradient(#ffef80, #b86409 60%);
  background: radial-gradient(#eaa121, #8e4901 45%, #b86409 80%);
}

.candle:after {
  width: 34px;
  height: 10px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 50%;
  top: 14px;
  box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.5);
  background: -moz-radial-gradient(rgba(0, 0, 0, 0.6), transparent 45%);
  background: -webkit-radial-gradient(rgba(0, 0, 0, 0.6), transparent 45%);
  background: -o-radial-gradient(rgba(0, 0, 0, 0.6), transparent 45%);
  background: -ms-radial-gradient(rgba(0, 0, 0, 0.6), transparent 45%);
  background: radial-gradient(rgba(0, 0, 0, 0.6), transparent 45%);
}

.thread {
  width: 6px;
  height: 36px;
  top: -17px;
  left: 50%;
  z-index: 1;
  border-radius: 40% 40% 0 0;
  transform: translateX(-50%);
  background: #121212;
  background: -moz-linear-gradient(
    #d6994a,
    #4b232c,
    #121212,
    black,
    #e8bb31 90%
  );
  background: -webkit-linear-gradient(
    #d6994a,
    #4b232c,
    #121212,
    black,
    #e8bb31 90%
  );
  background: -o-linear-gradient(#d6994a, #4b232c, #121212, black, #e8bb31 90%);
  background: -ms-linear-gradient(
    #d6994a,
    #4b232c,
    #121212,
    black,
    #e8bb31 90%
  );
  background: linear-gradient(#d6994a, #4b232c, #121212, black, #e8bb31 90%);
}

.flame {
  width: 24px;
  height: 120px;
  left: 50%;
  transform-origin: 50% 100%;
  transform: translateX(-50%);
  bottom: 100%;
  border-radius: 50% 50% 20% 20%;
  background: rgba(255, 255, 255, 1);
  background: -moz-linear-gradient(white 80%, transparent);
  background: -webkit-linear-gradient(white 80%, transparent);
  background: -o-linear-gradient(white 80%, transparent);
  background: -ms-linear-gradient(white 80%, transparent);
  background: linear-gradient(white 80%, transparent);
  animation: moveFlame 6s linear infinite, enlargeFlame 5s linear infinite;
}

.flame:before {
  width: 100%;
  height: 100%;
  border-radius: 50% 50% 20% 20%;
  box-shadow: 0 0 15px 0 rgba(247, 93, 0, 0.4),
    0 -6px 4px 0 rgba(247, 128, 0, 0.7);
}

@keyframes moveFlame {
  0%,
  100% {
    transform: translateX(-50%) rotate(-2deg);
  }
  50% {
    transform: translateX(-50%) rotate(2deg);
  }
}

@keyframes enlargeFlame {
  0%,
  100% {
    height: 120px;
  }
  50% {
    height: 140px;
  }
}

.glow {
  width: 26px;
  height: 60px;
  border-radius: 50% 50% 35% 35%;
  left: 50%;
  top: -48px;
  transform: translateX(-50%);
  background: rgba(0, 133, 255, 0.7);
  box-shadow: 0 -40px 30px 0 #dc8a0c, 0 40px 50px 0 #dc8a0c,
    inset 3px 0 2px 0 rgba(0, 133, 255, 0.6),
    inset -3px 0 2px 0 rgba(0, 133, 255, 0.6);
}

.glow:before {
  width: 70%;
  height: 60%;
  left: 50%;
  transform: translateX(-50%);
  bottom: 0;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.35);
}

.blinking-glow {
  width: 100px;
  height: 180px;
  left: 50%;
  top: -55%;
  transform: translateX(-50%);
  border-radius: 50%;
  background: #ff6000;
  -webkit-filter: blur(50px);
  -moz-filter: blur(60px);
  -o-filter: blur(60px);
  -ms-filter: blur(60px);
  filter: blur(60px);
  animation: blinkIt 0.1s infinite;
}

@keyframes blinkIt {
  50% {
    opacity: 0.8;
  }
}

.test-tube {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.line-top {
  height: 0.6rem;
  width: 10rem;
  margin-bottom: -0.6rem;
  background: #645c6b;
  z-index: 500;
  position: relative;

  &::before,
  &::after {
    content: "";
    position: absolute;
    height: 0.6rem;
    width: 1.4rem;
    background: #645c6b;
    top: 2.4rem;
    border-radius: 1rem;
  }

  &::before {
    left: -0.4rem;
  }
  &::after {
    left: 9rem;
  }

  &__line1,
  &__line2 {
    position: absolute;
    top: 12rem;
    left: 1.8rem;
    height: 10rem;
    width: 0.6rem;
    background: #ffffff;
    opacity: 0.5;
    border-radius: 1rem;
  }

  &__line2 {
    top: 10rem;
    height: 1.5rem;
  }
}

.top {
  width: 14.2rem;
  height: 3rem;
  margin-bottom: -0.7rem;
  border-radius: 4rem;
  border: 0.6rem solid #645c6b;
  z-index: 100;
  background: var(--main-color);
}

.liquid {
  width: 7.8rem;
  height: 20rem;
  margin-bottom: -24.7rem;
  margin-top: 4.8rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  z-index: 300;

  &__bottom {
    position: absolute;
    top: -79px;
    height: 397px;
    width: inherit;
    border-bottom-left-radius: 8rem;
    border-bottom-right-radius: 8rem;
    background: #a231ff;
    background: linear-gradient(360deg, #6a22d6 0%, #a231ff 100%);
  }
}

.tube {
  width: 10.2rem;
  height: 25.8rem;
  border-bottom-left-radius: 8rem;
  border-bottom-right-radius: 8rem;
  border: 0.6rem solid #645c6b;
  border-top: 0.6rem solid #f5f6fa;
  z-index: 200;
}
/* إعادة تكرار الأنميشن لكل العناصر حتى العنصر رقم 30 */
/* bubbles */
.color:nth-child(1) {
  animation: move-1 10s infinite;
  animation-delay: calc(-1 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-1 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(2) {
  position: absolute;
  animation: move-2 10s infinite;
  animation-delay: calc(-2 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-2 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(3) {
  position: absolute;
  animation: move-3 10s infinite;
  animation-delay: calc(-3 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-3 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(4) {
  position: absolute;
  animation: move-4 10s infinite;
  animation-delay: calc(-4 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-4 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(5) {
  position: absolute;
  animation: move-5 10s infinite;
  animation-delay: calc(-5 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-5 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(6) {
  position: absolute;
  animation: move-6 10s infinite;
  animation-delay: calc(-6 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-6 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(7) {
  position: absolute;
  animation: move-7 10s infinite;
  animation-delay: calc(-7 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-7 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(8) {
  position: absolute;
  animation: move-8 10s infinite;
  animation-delay: calc(-8 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-8 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(9) {
  position: absolute;
  animation: move-9 10s infinite;
  animation-delay: calc(-9 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-9 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(10) {
  position: absolute;
  animation: move-10 10s infinite;
  animation-delay: calc(-10 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-10 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(11) {
  position: absolute;
  animation: move-11 10s infinite;
  animation-delay: calc(-11 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-11 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(12) {
  position: absolute;
  animation: move-12 10s infinite;
  animation-delay: calc(-12 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-12 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(13) {
  position: absolute;
  animation: move-13 10s infinite;
  animation-delay: calc(-13 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-13 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(14) {
  position: absolute;
  animation: move-14 10s infinite;
  animation-delay: calc(-14 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-14 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(15) {
  position: absolute;
  animation: move-15 10s infinite;
  animation-delay: calc(-15 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-15 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(16) {
  position: absolute;
  animation: move-16 10s infinite;
  animation-delay: calc(-16 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-16 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(17) {
  position: absolute;
  animation: move-17 10s infinite;
  animation-delay: calc(-17 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-17 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(18) {
  position: absolute;
  animation: move-18 10s infinite;
  animation-delay: calc(-18 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-18 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(19) {
  position: absolute;
  animation: move-19 10s infinite;
  animation-delay: calc(-19 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-19 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(20) {
  position: absolute;
  animation: move-20 10s infinite;
  animation-delay: calc(-20 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-20 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(21) {
  position: absolute;
  animation: move-21 10s infinite;
  animation-delay: calc(-21 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-21 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(22) {
  position: absolute;
  animation: move-22 10s infinite;
  animation-delay: calc(-22 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-22 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(23) {
  position: absolute;
  animation: move-23 10s infinite;
  animation-delay: calc(-23 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-23 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(24) {
  position: absolute;
  animation: move-24 10s infinite;
  animation-delay: calc(-24 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-24 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(25) {
  position: absolute;
  animation: move-25 10s infinite;
  animation-delay: calc(-25 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-25 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(26) {
  position: absolute;
  animation: move-26 10s infinite;
  animation-delay: calc(-26 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-26 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(27) {
  position: absolute;
  animation: move-27 10s infinite;
  animation-delay: calc(-27 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-27 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(28) {
  position: absolute;
  animation: move-28 10s infinite;
  animation-delay: calc(-28 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-28 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(29) {
  position: absolute;
  animation: move-29 10s infinite;
  animation-delay: calc(-29 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-29 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
/* bubbles */
.color:nth-child(30) {
  position: absolute;
  animation: move-30 10s infinite;
  animation-delay: calc(-30 * 0.2s);
  /* تغيير هنا */
  z-index: 400;
}
@keyframes move-30 {
  100% {
    transform: translateY(calc(random(30) * -1rem));
    opacity: 0;
  }
}
.feat_container > div:first-child {
  animation: move-up 3s infinite;
}
.feat_container > div:nth-child(2) {
  animation: move-up 3s infinite;
  animation-delay: calc(0.5s);
}
.feat_container > div:last-child {
  animation: move-up 3s infinite;
  animation-delay: calc(1.5s);
}
@keyframes move-up {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(10px);
  }
  100% {
    transform: translateY(0px);
  }
}

ion-icon {
  position: fixed;
  font-size: 36px;
  right: 20px;
  bottom: 20px;
  color: #ea4c89;
}

.img {
  height: 200px;
  border-radius: 6px;
}

.container:first-child {
  gap: 20px;
}
.animation > img {
  width: 100px;
}
.feat {
  > div {
    background: #fff;
    padding: 10px;
    width: 260px;
    border-radius: 5px;
    text-align: center;
    color: var(--main-color);
    font-weight: bold;
    font-family: system-ui;
    position: relative;
    top: -5px;
    transition: 1.3s;
    // transform: rotate(7deg);
    box-shadow: 0 0 1px var(--main-color);

    &.caption_1 {
      color: #fe7566;
    }
    &.caption_2 {
      color: #e2c7b6;
    }
    &.caption_3 {
      color: #f4b92a;
    }
  }
}

@media (max-width: 767px) {
  .section {
    .container {
      flex-direction: column;
      gap: 60px;

      .feat {
        width: 100%;

        > div {
          top: 0;
          transform: rotate(0);
        }
      }
    }
  }
}
</style>
