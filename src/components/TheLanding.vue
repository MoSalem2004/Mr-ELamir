<template>
  <div id="background-wrap">
    <div class="bubble x1"></div>
    <div class="bubble x2"></div>
    <div class="bubble x3"></div>
    <div class="bubble x4"></div>
    <div class="bubble x5"></div>
    <div class="bubble x6"></div>
    <div class="bubble x7"></div>
    <div class="bubble x8"></div>
    <div class="bubble x9"></div>
    <div class="bubble x10"></div>
    <div
      class="TheLanding p-0"
      style="
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        width: 100%;
      "
    >
      <div class="container relative m-0 p-0">
        <div
          class="flex justify-center items-center h-80 contain"
          style="margin-top: 30px"
        >
          <div class="right w-1/2 relative">
            <img
              src="../assets/_90b326e1-086b-4166-b11a-3b108a0cbac7-removebg.png"
              alt=""
              class="m-auto"
            />
          </div>
          <div class="left w-1/2 flex flex-col justify-center gap-2.5">
            <!-- <h2 class="title" style="font-size: 35px"></h2> -->
            <h1 class="title_2" style="font-size: 46px; color: #fff">
              <div class="word">
                <!-- <span>DR</span> -->
                <!-- <span>/</span> -->
                <span>E</span>
                <span>L</span>
                <span>A</span>
                <span>M</span>
                <span>E</span>
                <span>R</span>
              </div>
            </h1>
            <p
              style="
                font-size: 19px;
                color: #fff;
                font-weight: bold;
                font-family: system-ui;
              "
            >
              منصة د / الأمير منصة تعليمية متخصصة لتدريس
              <strong> الكيمياء </strong>
              للمراحل الثانوية
            </p>
          </div>
        </div>
      </div>

      <!--Waves Container-->
      <div style="width: 100%">
        <svg
          class="waves"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          viewBox="0 24 150 28"
          preserveAspectRatio="none"
          shape-rendering="auto"
        >
          <defs>
            <path
              id="gentle-wave"
              d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z"
            />
          </defs>
          <g class="parallax">
            <use
              xlink:href="#gentle-wave"
              x="48"
              y="0"
              fill="rgba(255,255,255,0.7"
            />
            <use
              xlink:href="#gentle-wave"
              x="48"
              y="3"
              fill="rgba(255,255,255,0.5)"
            />
            <use
              xlink:href="#gentle-wave"
              x="48"
              y="5"
              fill="rgba(255,255,255,0.3)"
            />
            <use xlink:href="#gentle-wave" x="48" y="7" fill="#a231ff" />
          </g>
        </svg>
      </div>
      <!--Waves end-->
    </div>
  </div>
</template>
<script>
export default {
  name: "TheLanding",

  data() {
    return {
      dialog: false,
      dialog_2: false,
      data_1: [
        "معيدا بالكلية ( دكتور جامعي )",
        "الهيئات القضائية",
        "مجلس الدولة",
        "النيابة العامة",
        "النيابة الادارية",
        "هيئة قضايا الدولة",
        " كلية الشرطة ( ضباط متخصصين )",
        "الكلية الحربية ( النيابة العسكرية ) ",
        "مأذون شرعي",
        "وزارة الخارجية ( سفير )",
        "وزارة التموين والتجارة الداخلية",
        "الرقابة الإدارية",
        "الجهاز المركزي للمحاسبات",
        "مصلحة الضرائب",
        "الشئون القانونية",
        "المحاماة",
        "وظائف اخري بقطاعات عامة و خاصة",
        "وزارة الأوقاف",
        "وزير",
      ],
    };
  },
  mounted() {
    setTimeout(() => {
      this.Words();
    }, 1000);
  },
  methods: {
    Words() {
      const spans = document.querySelectorAll(".word span");

      spans.forEach((span, idx) => {
        span.addEventListener("click", (e) => {
          e.target.classList.add("active");
        });
        span.addEventListener("animationend", (e) => {
          e.target.classList.remove("active");
        });

        // Initial animation
        setTimeout(() => {
          span.classList.add("active");
        }, 750 * (idx + 1));
      });
    },
  },
};
</script>
<style lang="scss" scoped>
strong {
  font-size: 35px;
  color: var(--main-color);
  font-weight: bold;
  font-family: system-ui;
}
@keyframes showup {
  0% {
    opacity: 0;
  }
  20% {
    opacity: 1;
  }
  80% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

@keyframes slidein {
  0% {
    margin-left: -750px;
  }
  20% {
    margin-left: -750px;
  }
  35% {
    margin-left: 0px;
  }
  100% {
    margin-left: 0px;
  }
}

@keyframes reveal {
  0% {
    opacity: 0;
    width: 0px;
  }
  20% {
    opacity: 1;
    width: 0px;
  }
  30% {
    width: 355px;
  }
  80% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    width: 355px;
  }
}

@import url("https://fonts.googleapis.com/css?family=Anton|Roboto");

.word {
  font-family: "Anton", sans-serif;
  perspective: 750px;
  direction: ltr;
}

.word span {
  cursor: pointer;
  display: inline-block;
  font-size: 100px;
  user-select: none;
  line-height: 0.8;
}

.word span:nth-child(1).active {
  animation: balance 1.5s ease-out;
  transform-origin: bottom left;
}

@keyframes balance {
  0%,
  100% {
    transform: rotate(0deg);
  }

  30%,
  60% {
    transform: rotate(-45deg);
  }
}

.word span:nth-child(2).active {
  animation: shrinkjump 1s ease-in-out;
  transform-origin: bottom center;
}

@keyframes shrinkjump {
  10%,
  35% {
    transform: scale(2, 0.2) translate(0, 0);
  }

  45%,
  50% {
    transform: scale(1) translate(0, -150px);
  }

  80% {
    transform: scale(1) translate(0, 0);
  }
}

.word span:nth-child(3).active {
  animation: falling 2s ease-out;
  transform-origin: bottom center;
}

@keyframes falling {
  12% {
    transform: rotateX(240deg);
  }

  24% {
    transform: rotateX(150deg);
  }

  36% {
    transform: rotateX(200deg);
  }

  48% {
    transform: rotateX(175deg);
  }

  60%,
  85% {
    transform: rotateX(180deg);
  }

  100% {
    transform: rotateX(0deg);
  }
}

.word span:nth-child(4).active {
  animation: rotate 1s ease-out;
}

@keyframes rotate {
  20%,
  80% {
    transform: rotateY(180deg);
  }

  100% {
    transform: rotateY(360deg);
  }
}

.word span:nth-child(5).active {
  animation: toplong 1.5s linear;
}
.word span:nth-child(6).active {
  animation: rotate 1s ease-out;
}
.word span:nth-child(7).active {
  animation: falling 2s ease-out;
  transform-origin: bottom center;
}

@keyframes toplong {
  10%,
  40% {
    transform: translateY(-48vh) scaleY(1);
  }

  90% {
    transform: translateY(-48vh) scaleY(4);
  }
}

/* Other styles */

.fixed {
  position: fixed;
  top: 40px;
  left: 50%;
  transform: translateX(-50%);
}

footer {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  text-align: center;
  letter-spacing: 1px;
}

footer i {
  color: red;
}

footer a {
  color: #3c97bf;
  text-decoration: none;
}

#background-wrap {
  // background: #00b4ff;
  color: #333;
  font: 100% Lato, Arial, Sans Serif;
  // height: 100vh;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

#background-wrap {
  bottom: 0;
  left: 0;
  position: fixed;
  right: 0;
  top: 0;
  z-index: -1;
}

/* KEYFRAMES */

@-webkit-keyframes animateBubble {
  0% {
    margin-top: 750px;
  }
  100% {
    margin-top: -100%;
  }
}

@-moz-keyframes animateBubble {
  0% {
    margin-top: 750px;
  }
  100% {
    margin-top: -100%;
  }
}

@keyframes animateBubble {
  0% {
    margin-top: 750px;
  }
  100% {
    margin-top: -100%;
  }
}

@-webkit-keyframes sideWays {
  0% {
    margin-left: 0px;
  }
  100% {
    margin-left: 50px;
  }
}

@-moz-keyframes sideWays {
  0% {
    margin-left: 0px;
  }
  100% {
    margin-left: 50px;
  }
}

@keyframes sideWays {
  0% {
    margin-left: 0px;
  }
  100% {
    margin-left: 50px;
  }
}

/* ANIMATIONS */

.x1 {
  -webkit-animation: animateBubble 25s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  -moz-animation: animateBubble 25s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  animation: animateBubble 25s linear infinite,
    sideWays 2s ease-in-out infinite alternate;

  left: -5%;
  top: 5%;

  -webkit-transform: scale(0.6);
  -moz-transform: scale(0.6);
  transform: scale(0.6);
}

.x2 {
  -webkit-animation: animateBubble 20s linear infinite,
    sideWays 4s ease-in-out infinite alternate;
  -moz-animation: animateBubble 20s linear infinite,
    sideWays 4s ease-in-out infinite alternate;
  animation: animateBubble 20s linear infinite,
    sideWays 4s ease-in-out infinite alternate;

  left: 5%;
  top: 80%;

  -webkit-transform: scale(0.4);
  -moz-transform: scale(0.4);
  transform: scale(0.4);
}

.x3 {
  -webkit-animation: animateBubble 28s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  -moz-animation: animateBubble 28s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  animation: animateBubble 28s linear infinite,
    sideWays 2s ease-in-out infinite alternate;

  left: 10%;
  top: 40%;

  -webkit-transform: scale(0.7);
  -moz-transform: scale(0.7);
  transform: scale(0.7);
}

.x4 {
  -webkit-animation: animateBubble 22s linear infinite,
    sideWays 3s ease-in-out infinite alternate;
  -moz-animation: animateBubble 22s linear infinite,
    sideWays 3s ease-in-out infinite alternate;
  animation: animateBubble 22s linear infinite,
    sideWays 3s ease-in-out infinite alternate;

  left: 20%;
  top: 0;

  -webkit-transform: scale(0.3);
  -moz-transform: scale(0.3);
  transform: scale(0.3);
}

.x5 {
  -webkit-animation: animateBubble 29s linear infinite,
    sideWays 4s ease-in-out infinite alternate;
  -moz-animation: animateBubble 29s linear infinite,
    sideWays 4s ease-in-out infinite alternate;
  animation: animateBubble 29s linear infinite,
    sideWays 4s ease-in-out infinite alternate;

  left: 30%;
  top: 50%;

  -webkit-transform: scale(0.5);
  -moz-transform: scale(0.5);
  transform: scale(0.5);
}

.x6 {
  -webkit-animation: animateBubble 21s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  -moz-animation: animateBubble 21s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  animation: animateBubble 21s linear infinite,
    sideWays 2s ease-in-out infinite alternate;

  left: 50%;
  top: 0;

  -webkit-transform: scale(0.8);
  -moz-transform: scale(0.8);
  transform: scale(0.8);
}

.x7 {
  -webkit-animation: animateBubble 20s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  -moz-animation: animateBubble 20s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  animation: animateBubble 20s linear infinite,
    sideWays 2s ease-in-out infinite alternate;

  left: 65%;
  top: 70%;

  -webkit-transform: scale(0.4);
  -moz-transform: scale(0.4);
  transform: scale(0.4);
}

.x8 {
  -webkit-animation: animateBubble 22s linear infinite,
    sideWays 3s ease-in-out infinite alternate;
  -moz-animation: animateBubble 22s linear infinite,
    sideWays 3s ease-in-out infinite alternate;
  animation: animateBubble 22s linear infinite,
    sideWays 3s ease-in-out infinite alternate;

  left: 80%;
  top: 10%;

  -webkit-transform: scale(0.3);
  -moz-transform: scale(0.3);
  transform: scale(0.3);
}

.x9 {
  -webkit-animation: animateBubble 29s linear infinite,
    sideWays 4s ease-in-out infinite alternate;
  -moz-animation: animateBubble 29s linear infinite,
    sideWays 4s ease-in-out infinite alternate;
  animation: animateBubble 29s linear infinite,
    sideWays 4s ease-in-out infinite alternate;

  left: 90%;
  top: 50%;

  -webkit-transform: scale(0.6);
  -moz-transform: scale(0.6);
  transform: scale(0.6);
}

.x10 {
  -webkit-animation: animateBubble 26s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  -moz-animation: animateBubble 26s linear infinite,
    sideWays 2s ease-in-out infinite alternate;
  animation: animateBubble 26s linear infinite,
    sideWays 2s ease-in-out infinite alternate;

  left: 80%;
  top: 80%;

  -webkit-transform: scale(0.3);
  -moz-transform: scale(0.3);
  transform: scale(0.3);
}

/* OBJECTS */

.bubble {
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border-radius: 50%;

  -webkit-box-shadow: 0 20px 30px rgba(0, 0, 0, 0.2),
    inset 0px 10px 30px 5px rgba(255, 255, 255, 1);
  -moz-box-shadow: 0 20px 30px rgba(0, 0, 0, 0.2),
    inset 0px 10px 30px 5px rgba(255, 255, 255, 1);
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.2),
    inset 0px 10px 30px 5px rgba(255, 255, 255, 1);

  height: 200px;
  position: absolute;
  width: 200px;
  z-index: 11;
}

.bubble:after {
  background: -moz-radial-gradient(
    center,
    ellipse cover,
    rgba(255, 255, 255, 0.5) 0%,
    rgba(255, 255, 255, 0) 70%
  ); /* FF3.6+ */
  background: -webkit-gradient(
    radial,
    center center,
    0px,
    center center,
    100%,
    color-stop(0%, rgba(255, 255, 255, 0.5)),
    color-stop(70%, rgba(255, 255, 255, 0))
  ); /* Chrome,Safari4+ */
  background: -webkit-radial-gradient(
    center,
    ellipse cover,
    rgba(255, 255, 255, 0.5) 0%,
    rgba(255, 255, 255, 0) 70%
  ); /* Chrome10+,Safari5.1+ */
  background: -o-radial-gradient(
    center,
    ellipse cover,
    rgba(255, 255, 255, 0.5) 0%,
    rgba(255, 255, 255, 0) 70%
  ); /* Opera 12+ */
  background: -ms-radial-gradient(
    center,
    ellipse cover,
    rgba(255, 255, 255, 0.5) 0%,
    rgba(255, 255, 255, 0) 70%
  ); /* IE10+ */
  background: radial-gradient(
    ellipse at center,
    rgba(255, 255, 255, 0.5) 0%,
    rgba(255, 255, 255, 0) 70%
  ); /* W3C */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#80ffffff', endColorstr='#00ffffff',GradientType=1 ); /* IE6-9 fallback on horizontal gradient */

  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border-radius: 50%;

  -webkit-box-shadow: inset 0 20px 30px rgba(255, 255, 255, 0.3);
  -moz-box-shadow: inset 0 20px 30px rgba(255, 255, 255, 0.3);
  box-shadow: inset 0 20px 30px rgba(255, 255, 255, 0.3);

  content: "";
  height: 180px;
  left: 10px;
  position: absolute;
  width: 180px;
}
.TheLanding {
  // background-image: url("../assets/WhatsApp Image 2023-12-04 at 11.00.58 PM.jpeg");
  background-size: cover;
  background-position: center top;
  background-attachment: fixed;
  background: #a231ff87;
  // height: 100vh;
}
.icon {
  bottom: 403px;
  left: 140px;
}
img {
  width: 400px;
  border-radius: 5px;
}
.law {
  width: 75px;
  filter: grayscale(1);
}
.title_1_1 {
  color: var(--main-color) !important;
  font-weight: bold;
  font-size: 20px;
}
.feat {
  display: flex;
  gap: 10px;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid var(--main-color);
  margin-bottom: 10px;
  font-size: 14px;
  span {
    width: 30px;
    background: var(--main-color);
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    border-radius: 5px;
  }
}
.left {
  font-family: system-ui;
  h1 {
    font-weight: bold;
  }
  h2,
  .title_3 {
    color: #ef4444;
    font-weight: bold;
  }
  .title_3 {
    font-size: 23px;
  }
  .title_2 {
    color: var(--main-color);
  }
  .button_1,
  .button_2 {
    padding: 10px !important;
    width: fit-content;
    border: 1px solid var(--main-color) !important;
    border-radius: 5px;
    display: flex;
    align-items: center;
    gap: 10px !important;
    font-weight: bold;
    color: var(--main-color) !important;
    cursor: pointer;
    transition: 0.3s;
    svg {
      font-size: 19px;
    }
    &:hover {
      background: var(--main-color) !important;
      color: #fff !important;
    }
  }
}
.v-card .v-card-title {
  padding: 0 !important;
}
.All_btn > button {
  border: 1px solid var(--main-color);
  border-radius: 5px;
  color: var(--main-color);
  font-weight: bold;
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  transition: 0.3s;
  &:hover {
    background: var(--main-color);
    color: #fff;
  }
}
h1 {
  font-family: "Lato", sans-serif;
  font-weight: 300;
  letter-spacing: 2px;
  font-size: 48px;
}
p {
  font-family: "Lato", sans-serif;
  letter-spacing: 1px;
  font-size: 14px;
  color: #333333;
}

.header {
  position: relative;
  text-align: center;
  background: linear-gradient(
    60deg,
    rgba(84, 58, 183, 1) 0%,
    rgba(0, 172, 193, 1) 100%
  );
  color: white;
}
.logo {
  width: 50px;
  fill: white;
  padding-right: 15px;
  display: inline-block;
  vertical-align: middle;
}

.inner-header {
  height: 65vh;
  width: 100%;
  margin: 0;
  padding: 0;
}

.flex {
  /*Flexbox for containers*/
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.waves {
  position: relative;
  width: 100%;
  height: 15vh;
  margin-bottom: -7px; /*Fix for safari gap*/
  min-height: 100px;
  max-height: 150px;
}

.content {
  position: relative;
  height: 20vh;
  text-align: center;
  background-color: white;
}

/* Animation */

.parallax > use {
  animation: move-forever 25s cubic-bezier(0.55, 0.5, 0.45, 0.5) infinite;
}
.parallax > use:nth-child(1) {
  animation-delay: -2s;
  animation-duration: 7s;
}
.parallax > use:nth-child(2) {
  animation-delay: -3s;
  animation-duration: 10s;
}
.parallax > use:nth-child(3) {
  animation-delay: -4s;
  animation-duration: 13s;
}
.parallax > use:nth-child(4) {
  animation-delay: -5s;
  animation-duration: 20s;
}
@keyframes move-forever {
  0% {
    transform: translate3d(-90px, 0, 0);
  }
  100% {
    transform: translate3d(85px, 0, 0);
  }
}
/*Shrinking for mobile*/
@media (max-width: 768px) {
  .waves {
    height: 40px;
    min-height: 40px;
  }
  .content {
    height: 30vh;
  }
  h1 {
    font-size: 24px;
  }
}
@media (min-width: 1200px) {
}

@media (min-width: 768px) and (max-width: 1199px) {
}

@media (max-width: 767px) {
  .TheLanding {
    // min-height: 150vh;
  }
  .contain {
    flex-direction: column;
    gap: 30px;
    margin: 80px auto 20px;
    > div {
      width: 100%;
    }
  }
  img.m-auto {
    // width: 145px;
  }
  .icon {
    bottom: 378px;
    left: 268px;
  }
  .container {
    flex-direction: column;
    & > div {
      width: 100%;
    }
    .box {
      width: 48% !important;
    }
  }
}
</style>
