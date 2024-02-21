<template>
  <div id="ContactUs" class="ContactUs bg-[#eee] mt-20">
    <div class="container flex flex-col justify-center items-center">
      <div class="body">
        <div class="container-0">
          <div class="box box-1">
            <div class="cover">
              <img
                style="background: #ec2828"
                src="../assets/Logo_Emblem_Youtube_Red_background_529384_1920x1080.jpg"
                alt=""
              />
            </div>
            <button><div></div></button>
          </div>
          <div class="box box-2">
            <div class="cover">
              <img src="../assets/instagram-logo_1199-122.png" alt="" />
            </div>
            <button><div></div></button>
          </div>
          <div class="box box-3">
            <div class="cover">
              <img
                src="../assets/apps.37935.9007199266245907.b029bd80-381a-4869-854f-bac6f359c5c9.png"
                alt=""
              />
            </div>
            <button><div></div></button>
          </div>
        </div>
      </div>
      <div
        style="
          width: 100%;
          display: flex;
          gap: 20px;
          flex-wrap: wrap;
          justify-content: space-between;
          margin-bottom: 10px;
        "
      >
        <div
          style="
            width: 100%;
            display: flex;
            flex-direction: row-reverse;
            justify-content: space-between;
            align-items: center;
            margin-top: 20px;
            border-top: 1px solid #fff;
            padding-top: 30px;
          "
        >
          <div>
            <a
              class="text-reset fw-bold"
              href="https://www.facebook.com/profile.php?id=61551365201853"
            >
              <img
                src="../assets/SalemTeamLogo_2-removebg-preview.png"
                alt="SalemTeam"
                id="SalemTeam"
                style="height: 60px; background: #fff; padding: 3px"
              />
            </a>
            <div style="color: #fff; margin-top: 10px">
              " جودة تستحق التجربة "
            </div>
          </div>
          <ul
            class="social mt-2.5"
            style="padding: 0; display: flex; gap: 10px"
          >
            <li>
              <a
                class="bg-[#1877f2] rounded"
                href="https://www.facebook.com/profile.php?id=61551365201853"
                style="
                  color: #fff !important;
                  display: inline-flex;
                  justify-content: center;
                  align-items: center;
                  width: 50px;
                  height: 50px;
                  font-size: 20px;
                  transition: all 0.3s ease 0s;
                "
              >
                <!-- <font-awesome-icon :icon="['fab', 'facebook-f']" /> -->
                <font-awesome-icon
                  :icon="['fab', 'facebook-f']"
                  class="text-4xl bg-[#1877f2]"
                  style="font-size: 24px"
                />
              </a>
            </li>
            <li>
              <a
                class="bg-[#E4405F] rounded"
                href="https://www.instagram.com/salem_team_company"
                style="
                  color: #fff !important;
                  display: inline-flex;
                  justify-content: center;
                  align-items: center;
                  width: 50px;
                  height: 50px;
                  font-size: 20px;
                  transition: all 0.3s ease 0s;
                "
              >
                <!-- <font-awesome-icon :icon="['fab', 'instagram']" /> -->
                <font-awesome-icon
                  :icon="['fab', 'instagram']"
                  class="text-4xl bg-[#E4405F]"
                  style="font-size: 24px"
                />
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
  <div
    class="copyright p-2.5 text-center text-[var(--main-color)]"
    style="
      font-weight: bold;
      padding: 10px;
      background: var(--main-color);
      color: #fff;
    "
  >
    <div style="width: 90%; margin: auto">
      &copy; جميع الحقوق محفوظة Salem Team
    </div>
  </div>
</template>
<script>
export default {
  name: "ContactUs",
};
</script>
<style lang="scss" scoped>
.body,
ol,
ul,
h1,
h2,
h3,
h4,
h5,
h6,
p,
th,
td,
dl,
dd,
form,
fieldset,
legend,
input,
textarea,
i,
select {
  margin: 0;
  padding: 0;
}

.body {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  background-color: #2c3138;
  -webkit-perspective: 90rem;
  perspective: 90rem;
  -webkit-perspective-origin: 34% 61%;
  perspective-origin: 34% 61%;
}

img {
  width: 160px;
}

button {
  cursor: pointer;
  outline: 0;
  width: 180px;
  height: 48px;
  border-radius: 8px;
  background-color: #2c3138;
  margin-top: 40px;
  overflow: hidden;
  -webkit-transform: scale(0.7);
  transform: scale(0.7);
}

button::after {
  content: "\f167";
  position: relative;
  top: -40px;
  display: block;
  width: 48px;
  height: 107%;
  background-color: #000;
  margin-top: -1px;
  margin-left: -7px;
  border-radius: 6px 0 0 6px;
  // background-image: url("https://www.svgrepo.com/show/13671/youtube.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-color: #ec2828;
  top: -85px;
  left: -111px;
}

button::before {
  content: "";
  display: block;
  width: 97px;
  height: 46px;
  margin-left: -7px;
  /* margin-top: -1px; */
  transition: all 200ms cubic-bezier(0.25, 0.75, 0.5, 1.25);
  left: 20px;
  position: relative;
}

.box-1:hover button::before {
  width: 120%;
  opacity: 0.8;
  background-color: #ec2828;
}

.box-2:hover button::before {
  width: 120%;
  opacity: 0.8;
  background-color: #d93e83;
}

.box-3:hover button::before {
  width: 120%;
  opacity: 0.8;
  background-color: #008bff;
}

.container-0 {
  gap: 20px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -ms-flex-pack: distribute;
  justify-content: space-around;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
  width: 80vw;
  // height: 100vh;
  margin-bottom: 20px;
  margin-left: 6vw;
  /* transform:rotateX(7deg) rotateZ(-4deg) rotateY(13deg) scale3d(1, 1, -0.9); */
  -webkit-transform: rotateX(23deg) rotateZ(-9deg) rotateY(15deg)
    scale3d(1, 1, -0.9);
  transform: rotateX(23deg) rotateZ(-9deg) rotateY(15deg) scale3d(1, 1, -0.9);
}

.box {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  -webkit-transition: all 0.3s ease-out;
  transition: all 0.3s ease-out;
  will-change: transform;
}

.box:hover .cover {
  -webkit-transform: translateY(-14px) scale(1.04);
  transform: translateY(-14px) scale(1.04);
}

.box-1 button {
  border: 1px solid #ec2828;
  color: #fff;
  font-size: 22px;
  text-align: right;
  padding-right: 20px;
  line-height: 40px;
}

.box-1 button::after {
  content: "";
  background-color: #ec2828;
  top: -85px;
}

.box-2 button {
  border: 1px solid #d93e83;
  color: #fff;
  font-size: 22px;
  text-align: right;
  padding-right: 20px;
  line-height: 40px;
}

.box-2 button::after {
  content: "";
  background-color: #d93e83;
  top: -85px;
}

.box-3 button {
  border: 1px solid #008bff;
  color: #fff;
  font-size: 22px;
  text-align: right;
  padding-right: 20px;
  line-height: 40px;
}

.box-3 button::after {
  content: "";
  background-color: #008bff;
  top: -85px;
}

.cover {
  -webkit-transition: all 400ms ease-in-out;
  transition: all 400ms ease-in-out;
  will-change: transform;
}

.cover img {
  -webkit-transition: all 260ms ease-in-out;
  transition: all 260ms ease-in-out;
}

.box .cover::after {
  content: "";
  z-index: -99;
  position: absolute;
  top: 20px;
  left: -20px;
  display: block;
  width: 160px;
  height: 214px;
  opacity: 0;
  background-position: center;
  background-repeat: no-repeat;
  background-size: 160px 214px;
  -webkit-filter: blur(24px);
  filter: blur(24px);
  -webkit-transition: all 260ms ease-in-out;
  transition: all 260ms ease-in-out;
  will-change: transform;
  -webkit-transform: scale(0.6);
  transform: scale(0.6);
}

.box:hover .cover::after {
  opacity: 1;
  -webkit-transform: scale(1);
  transform: scale(1);
}

.box-1 .cover::after {
  background-image: url("../assets/Logo_Emblem_Youtube_Red_background_529384_1920x1080.jpg");
}

.box-2 .cover::after {
  background-image: url("../assets/instagram-logo_1199-122.png");
}

.box-3 .cover::after {
  background-image: url("../assets/apps.37935.9007199266245907.b029bd80-381a-4869-854f-bac6f359c5c9.png");
}

img {
  height: 219px;
  border-radius: 5px;
}

.box-1 button div::before {
  content: "YouTupe";
  position: relative;
  top: -44px;
  left: -4px;
  color: #ec2828;
  font-size: 21px;
  font-weight: 300;
}

.box-1:hover button div::before {
  color: #fff;
}

.box-2 button div::before {
  content: "Instagram";
  position: relative;
  top: -44px;
  left: -6px;
  color: #d93e83;
  font-size: 21px;
  font-weight: 300;
}

.box-2:hover button div::before {
  color: #fff;
}

.box-3 button div::before {
  content: "FaceBook";
  position: relative;
  top: -44px;
  left: 3px;
  color: #008bff;
  font-size: 21px;
  font-weight: 300;
}

.box-3:hover button div::before {
  color: #fff;
}

.dr {
  position: absolute;
  bottom: 16px;
  right: 16px;
  width: 100px;
}

.ContactUs {
  padding: 10px;

  .Feat_1 {
    flex-wrap: wrap;
    gap: 10px;
    .feat {
      width: 24%;
      align-items: center;
      justify-content: center;
      border: 1px solid var(--main-color);
    }
  }
  .Feat_2 {
    width: 100%;
    margin: 10px auto 0;
    .Copyright {
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-direction: column;
      padding: 0 20px 20px 20px;
      width: 100%;
      & > div {
        display: flex;
        justify-content: space-between;
        padding: 10px;
        gap: 10px;
        align-items: center;
        padding: 10px;
        background: #fff;
        border-radius: 5px;
      }
      p {
        display: flex;
        gap: 10px;
        justify-content: space-between;
        margin: 0;
        &:first-child {
          padding-bottom: 10px;
        }
      }
      span {
        display: flex;
        align-items: flex-end;
      }
      a {
        position: relative;
      }
      strong {
        font-weight: bold;
        color: var(--main-color);
      }
      #fac {
        background: var(--main-color);
        color: #fff !important;
        padding: 10px;
        border-radius: 5px;
      }
    }
  }
}
.left svg {
  // background-color: var(--main-color);
  color: rgb(255, 255, 255);
  display: inline-flex;
  justify-content: center;
  align-items: center;
  /* width: 50px; */
  /* height: 50px; */
  font-size: 24px;
  transition: all 0.3s ease 0s;
  padding: 10px;
  border-radius: 5px;
}
.left > li > a {
  display: flex;
  align-items: center;
  gap: 10px;
  background: rgb(250 250 250 / 50%);
  padding: 10px;
  width: 100%;
  font-weight: bold;
  color: var(--main-color) !important;
  border-radius: 5px;
  box-shadow: 0 0 10px #ddd;
}
.phone {
  display: flex;
  align-content: center;
  flex-wrap: wrap;
  gap: 10px;
  > span {
    display: flex;
    gap: 10px;
    align-items: center;
    justify-content: space-between;
    border: 1px solid #dddddd;
    padding: 10px;
    border-radius: 5px;
    font-size: 14px;
    font-weight: bold;

    > .button {
      background: #eee;
      padding: 5px 15px;
      border-radius: 5px;
      cursor: pointer;
    }
  }
}
.ContactUs {
  // background-image: url("../assets/WhatsApp Image 2023-12-04 at 11.00.58 PM.jpeg");
  background-size: cover;
  background-position: center top;
  background-attachment: fixed;
  background-color: #2c3138;
}
@media (min-width: 1200px) {
}

@media (min-width: 768px) and (max-width: 1199px) {
}

@media (max-width: 767px) {
  .Copyright {
    & > div {
      flex-direction: column;
      p:last-child {
        width: 100%;
        a {
          width: 100%;
        }
      }
    }
  }
  .Feat_1 {
    flex-direction: column;
    .feat {
      width: 100% !important;
    }
  }
  .container {
    flex-direction: column;

    & > div {
      width: 100%;
    }
    .left,
    .right {
      width: 100% !important;
    }
    .phone > span {
      width: 100%;
    }
  }
}
</style>
