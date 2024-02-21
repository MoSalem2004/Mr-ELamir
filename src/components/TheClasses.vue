<template>
  <div id="TheClasses" class="TheClasses">
    <div class="container">
      <div class="main_title"></div>
      <div class="title mb-10">
        <h1>الصفوف الدراسية</h1>
      </div>
      <div class="contain-0">
        <router-link class="box" to="/Main_Class">
          <img
            src="../assets/_0cc046a2-0ac5-4639-9563-ce8a5ec588b9.jpg"
            alt=""
          />
          <div class="p">الصف الأول الثانوي</div>
        </router-link>
        <router-link class="box" to="/Main_Class">
          <img
            src="../assets/_694d8fe1-6024-4fa3-8e5e-4825dfe24b36.jpg"
            alt=""
          />
          <div class="p">الصف الثاني الثانوي</div>
        </router-link>
        <router-link class="box" to="/Main_Class">
          <img
            src="../assets/_a2f95eaa-c968-4762-a388-01ebe6b7fc42.jpg"
            alt=""
          />
          <div class="p">الصف الثالث الثانوي</div>
        </router-link>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "TheClasses",
  mounted() {
    this.select();
  },
  data() {
    return {
      type: "",
      lang: "",
      class: "",
    };
  },

  methods: {
    select() {
      document.querySelectorAll(".contain-0 > a").forEach((e) => {
        e.onclick = () => {
          console.log(e.querySelector(".p").innerHTML);
          localStorage.setItem("updateClass", e.querySelector(".p").innerHTML);
        };
      });
    },
  },
};
</script>
<style lang="scss" scoped>
.contain-0 {
  display: flex;
  gap: 10px;
  justify-content: space-between;
  align-items: center;
  .box {
    width: 32%;
    transition: 0.3s;
    cursor: pointer;
    &:hover {
      transform: scale(1.03);
    }
    img {
      border-radius: 5px;
    }
  }
}
.p {
  position: relative;
  padding: 10px 20px;
  background: #fff;
  border-radius: 10px;
  top: -36px;
  background: #ffffff;
  font-size: 20px;
  color: var(--main-color);
  font-weight: bold;
  width: 95%;
  margin: 0 auto;
  border-bottom: 1px solid var(--main-color);
}
.body {
  background-color: #3498db;
  overflow: hidden;
  height: 400px;
  width: 100%;
  margin: 0;
  border-radius: 5px;
}

.div {
  margin: 175px auto;
}

.drop {
  position: relative;
  width: 20px;
  height: 20px;
  top: -30px;
  margin: 0 auto;
  background: #fff;
  -moz-border-radius: 20px;
  -webkit-border-radius: 20px;
  border-radius: 20px;
  -moz-animation-name: drip;
  -webkit-animation-name: drip;
  animation-name: drip;
  -moz-animation-timing-function: cubic-bezier(1, 0, 0.91, 0.19);
  -webkit-animation-timing-function: cubic-bezier(1, 0, 0.91, 0.19);
  animation-timing-function: cubic-bezier(1, 0, 0.91, 0.19);
  -moz-animation-duration: 2s;
  -webkit-animation-duration: 2s;
  animation-duration: 2s;
  -moz-animation-iteration-count: infinite;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

.drop:before {
  content: "";
  position: absolute;
  width: 0;
  height: 0;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-bottom: 30px solid rgba(255, 255, 255, 1);
  top: -22px;
}

.wave {
  position: relative;
  opacity: 0;
  top: 0;
  width: 2px;
  height: 1px;
  border: #fff 7px solid;
  -moz-border-radius: 300px / 150px;
  -webkit-border-radius: 300px / 150px;
  border-radius: 300px / 150px;
  -moz-animation-name: ripple;
  -webkit-animation-name: ripple;
  animation-name: ripple;
  -moz-animation-delay: 2s;
  -webkit-animation-delay: 2s;
  animation-delay: 2s;
  -moz-animation-duration: 2s;
  -webkit-animation-duration: 2s;
  animation-duration: 2s;
  -moz-animation-iteration-count: infinite;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

.wave:after {
  content: "";
  position: absolute;
  opacity: 0;
  top: -5px;
  left: -5px;
  width: 2px;
  height: 1px;
  border: #fff 5px solid;
  -moz-border-radius: 300px / 150px;
  -webkit-border-radius: 300px / 150px;
  border-radius: 300px / 150px;
  -moz-animation-name: ripple-2;
  -webkit-animation-name: ripple-2;
  animation-name: ripple-2;
  -moz-animation-duration: 2s;
  -webkit-animation-duration: 2s;
  animation-duration: 2s;
  -moz-animation-iteration-count: infinite;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

@keyframes ripple {
  from {
    opacity: 1;
  }
  to {
    width: 600px;
    height: 300px;
    border-width: 1px;
    top: -100px;
    opacity: 0;
  }
}

@keyframes ripple-2 {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
  100% {
    width: 200px;
    height: 100px;
    border-width: 1px;
    top: 100px;
    left: 200px;
  }
}

@keyframes drip {
  to {
    top: 190px;
  }
}

.title h1 {
  font-size: 34px;
  font-weight: 500;
  text-transform: uppercase;
  direction: rtl;
}
.title h1:before {
  background-color: var(--main-color);
  border-radius: 0.25rem;
  content: "";
  display: block;
  height: 0.25rem;
  width: 42px;
  margin-bottom: 1.25rem;
}

.v-avatar.v-avatar--density-default {
  width: 30px;
  height: 30px;
  border-radius: 5px;
  background: var(--main-color) !important;
  color: #fff;
}
.v-card-title {
  display: flex;
  justify-content: flex-start !important;
  align-items: center;
  gap: 10px;
}
.selecte {
  & > span {
    color: var(--main-color);
    font-weight: bold;
    font-size: 16px;
    width: 46% !important;
    font-family: system-ui;
    text-align: center;
  }
}
@media (min-width: 1200px) {
}

@media (min-width: 768px) and (max-width: 1199px) {
}

@media (max-width: 767px) {
  .selecte_1,
  .selecte_2,
  .selecte_3 {
    flex-direction: column;
    span {
      width: 95% !important;
      margin: auto;
    }
  }

  .contain-0 {
    flex-direction: column;
    .box {
      width: 100%;
    }
  }
}
</style>
