<template>
  <div
    id="Main_Class"
    class="Main_Class pt-2.5"
    style="margin-top: -20px; padding-bottom: 50px"
  >
    <div class="container relative" style="padding-top: 160px">
      <AddSub
        v-if="showAddSub"
        @Close="CloseAndOpenAddSub"
        @GetData="getdata"
      />
      <nav
        aria-label="breadcrumb"
        class="nav_1 flex items-center justify-between"
      >
        <nav aria-label="breadcrumb">
          <MDBBreadcrumb>
            <MDBBreadcrumbItem active>{{ Class }}</MDBBreadcrumbItem>
          </MDBBreadcrumb>
        </nav>
        <div
          @click="CloseAndOpenAddSub"
          class="flex items-center gap-2.5 p-2.5 bg-[#fff] rounded cursor-pointer hover-0"
          v-if="ShowBtnToUser === 'Admin'"
          style="
            border: 1px solid var(--main-color);
            margin: 10px;
            color: var(--main-color);
            font-weight: bold;
            font-size: 14px;
          "
        >
          <font-awesome-icon :icon="['fas', 'plus']" />
          <span>أضف مادة</span>
        </div>
      </nav>

      <div style="min-height: 58vh" class="mt-2.5">
        <div
          class="text-right my-2.5 p-2.5 text-[--main-color] font-bold"
          style="
            background: #fff;
            width: fit-content;
            border-radius: 5px;
            padding: 10px;
            box-shadow: 0 0 10px #ddd;
          "
        >
          ({{ AllData.length }}) مادة
        </div>
        <div
          class="body flex gap-2.5 items-center flex-wrap justify-between mt-2.5"
        >
          <img
            src="../assets/animation_loia37xm_small.gif"
            alt=""
            v-if="showDownloadIcon"
            class="m-auto"
          />
          <div
            style="
              background: #fff;
              width: 100%;
              padding: 10px;
              color: var(--main-color);
              font-weight: bold;
              text-align: center;
            "
            v-if="AllData.length === 0"
          >
            لا توجد مواد لعرضها
          </div>
          <div
            class="main_box w-48 border-1 p-2.5 rounded relative"
            v-for="(Data, index) in AllData"
            :key="Data"
            style="background: #ffffffa1; box-shadow: 0 0 10px #ddd"
          >
            <font-awesome-icon
              :icon="['fas', 'pen-to-square']"
              class="absolute left-[7px] top-[7px] bg-[var(--main-color)] text-white text-xs p-1 rounded-full"
              v-if="ShowBtnToUser === 'Admin'"
            />
            <span
              class="absolute left-[35px] top-[7px] bg-[var(--main-color)] text-white text-xs p-1 rounded-full cursor-pointer hidden"
              @click="Updata"
              v-if="ShowBtnToUser === 'Admin'"
              >حفظ التغييرات</span
            >
            <div class="header flex justify-between p-2.5 items-center mt-2.5">
              <div class="flex gap-2.5 items-center">
                <div
                  class="num bg-[--main-color] text-white w-6 h-6 flex items-center justify-center rounded"
                >
                  {{ index + 1 }}
                </div>
                <div class="title font-bold text-[--main-color] text-xl">
                  {{ Data.sub_name }}
                </div>
              </div>
              <div class="text-[#6e6e6e] text-xs font-bold text-sm">
                {{ Data.Season }}
              </div>
            </div>
            <div class="book flex gap-2.5 relative flex-wrap">
              <a
                :href="Data.BookLink"
                class="border-1 border-[--main-color] flex items-center justify-center gap-2.5 p-2.5 rounded hover-0 cursor-pointer w-48 mb-2.5"
              >
                <font-awesome-icon
                  :icon="['fas', 'book']"
                  class="text-[--main-color]"
                />
                <span class="text-[--main-color]">تحميل كتاب المادة</span>
              </a>

              <div
                class="cursor-pointer w-48 mb-2.5 Open_Test"
                @click="CheckAboutUser"
              >
                <router-link
                  :to="UserId ? '/Main_Testing' : ''"
                  class="border-1 border-[--main-color] flex items-center justify-center gap-2.5 p-2.5 rounded hover-0"
                >
                  <font-awesome-icon
                    :icon="['fas', 'clipboard-question']"
                    class="text-[dimgrey]"
                  />
                  <span class="text-[dimgrey]"> الإختبارات </span>
                </router-link>
              </div>
              <input
                type="text"
                placeholder="لينك كتاب المادة"
                class="border p-1 input1 pointer-events-none"
                :value="Data.BookLink"
                v-if="ShowBtnToUser === 'Admin'"
                style="
                  height: 26px;
                  width: 100%;
                  padding: 10px !important;
                  border-radius: 5px;
                "
              />
            </div>
            <div
              class="free_course flex flex-col gap-2.5 my-2.5 mt-3"
              v-if="false"
            >
              <div class="title flex gap-1 items-center">
                <font-awesome-icon
                  :icon="['fas', 'circle-check']"
                  class="text-[--main-color]"
                />

                <div class="text-lg text-[--main-color]">الكورس المجاني</div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="main_Overlay" v-if="Close" style="z-index: 101"></div>
      <div
        class="popup_2 rounded p-2.5 bg-white fixed -translate-x-1/2 -translate-y-1/2 left-1/2 top-1/2 overflow-auto z-20"
        v-if="Close"
        style="width: 90%; font-family: system-ui; z-index: 101"
      >
        <div
          class="header flex justify-between items-center p-2.5"
          style="
            font-size: 20px;
            color: var(--main-color);
            font-weight: bold;
            background: #fafafa;
            margin-bottom: 10px;
            border-radius: 5px;
          "
        >
          <div class="flex items-center gap-2.5">
            <font-awesome-icon :icon="['fas', 'file-invoice-dollar']" />
            <span>فاتورة شراء</span>
          </div>
          <font-awesome-icon :icon="['fas', 'xmark']" @click="Close = false" />
        </div>
        <div class="body">
          <table border="1" width="100%">
            <tbody>
              <tr>
                <td>الصف</td>
                <td>{{ BillClass }}</td>
              </tr>
              <tr>
                <td>الصنف</td>
                <td>{{ BillName }}</td>
              </tr>
              <tr>
                <td>السعر</td>
                <td style="flex gap-2.5 items-center">
                  {{ BillPrice || 0 }} <span>جنية مصري</span>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="footer flex flex-col">
          <div
            class="pay p-2.5 cursor-pointer text-center mt-5 hover-0"
            @click="pay1"
            style="
              width: 100%;
              gap: 10px;
              display: flex;
              align-items: center;
              justify-content: center;
              border: 1px solid var(--main-color);
              border-radius: 5px;
              color: var(--main-color);
              font-weight: bold;
              font-size: 20px;
            "
          >
            <font-awesome-icon :icon="['fas', 'credit-card']" />
            <span> شراء بالكارت الذكي </span>
          </div>
          <a
            class="steps"
            href="https://www.youtube.com/watch?v=WQsMQ9wtq_4"
            style="
              display: flex;
              align-items: center;
              gap: 10px;
              background: #fafafa;
              padding: 10px;
              margin-top: 10px;
              border-radius: 5px;
              cursor: pointer;
              color: #ff0000 !important;
              font-weight: bold;
              font-size: 14px;
            "
          >
            <font-awesome-icon :icon="['fab', 'youtube']" color="#ff0000" />
            <div>خطوات تحويل فودافون كاش لكارت ذكي لمدة 24 ساعة</div>
          </a>
        </div>
      </div>
      <section class="flex justify-between gap-2.5 mt-2.5">
        <div
          class="w-48 p-2.5 text-center cursor-pointer"
          @click="CheckAboutUser_1"
        >
          شراء اختبارات {{ Class }}
        </div>
        <div
          class="w-48 p-2.5 text-center cursor-pointer"
          @click="PayAllCourseFunction"
        >
          حجز كورسات {{ Class }}
        </div>
      </section>
      <div
        class="main_Overlay"
        v-if="PayAllCourse"
        @click="PayAllCourseFunction"
      ></div>
      <div
        v-if="PayAllCourse"
        class="PayAllCourse rounded p-2.5 bg-white fixed -translate-x-1/2 -translate-y-1/2 left-1/2 top-1/2 overflow-auto z-20"
        style="width: 90%"
      >
        <div
          class="header flex align-center justify-between bg-[#fafafa] p-2.5"
        >
          <span
            style="
              font-size: 23px;
              color: var(--main-color);
              font-weight: bold;
              font-family: system-ui;
            "
            >حجز الكورسات</span
          >
          <font-awesome-icon
            :icon="['fas', 'xmark']"
            @click="PayAllCourseFunction"
            style="
              font-size: 23px;
              color: var(--main-color);
              font-weight: bold;
              font-family: system-ui;
            "
          />
        </div>
        <div class="body flex mt-2.5 justify-between align-center">
          <div
            style="
              display: flex;
              flex-direction: column;
              gap: 10px;
              background: #fff;
              padding: 10px;
              width: 48%;
              border: 1px solid var(--main-color);
              border-radius: 5px;
              color: var(--main-color);
            "
          >
            <div
              class="title"
              style="font-size: 20px; font-weight: bold; font-family: system-ui"
            >
              حجز كورسات الأونلاين
            </div>
            <div
              class="flex align-center justify-between font-bold"
              style="background: #fafafa; padding: 10px; border-radius: 5px"
            >
              <div class="num">01012366733</div>

              <div
                class="flex color align-center justify-between gap-2.5 bg-[#fff] p-2.5 rounded cursor-pointer"
                @click="copyTextDad($event)"
              >
                <font-awesome-icon
                  :icon="['fas', 'copy']"
                  @click="copyTextSvg($event)"
                />
                <span @click="copyText($event)">نسخ الرقم</span>
              </div>
            </div>
          </div>
          <div
            style="
              display: flex;
              flex-direction: column;
              gap: 10px;
              background: #fff;
              padding: 10px;
              width: 48%;
              border: 1px solid var(--main-color);
              border-radius: 5px;
              color: var(--main-color);
            "
          >
            <div
              class="title"
              style="font-size: 20px; font-weight: bold; font-family: system-ui"
            >
              حجز كورسات الأوفلاين
            </div>
            <div
              class="flex align-center justify-between font-bold"
              style="background: #fafafa; padding: 10px; border-radius: 5px"
            >
              <div class="num">01282027633</div>
              <div
                class="flex color align-center justify-between gap-2.5 bg-[#fff] p-2.5 rounded cursor-pointer"
                @click="copyTextDad($event)"
              >
                <font-awesome-icon
                  :icon="['fas', 'copy']"
                  @click="copyTextSvg($event)"
                />
                <span @click="copyText($event)">نسخ الرقم</span>

                <v-snackbar v-model="snackbar" :timeout="timeout">
                  {{ text }}

                  <template v-slot:actions>
                    <v-btn
                      color="blue"
                      variant="text"
                      @click="snackbar = false"
                    >
                      إغلاق
                    </v-btn>
                  </template>
                </v-snackbar>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div>
    <v-snackbar v-model="snackbar1" :timeout="timeout1">
      {{ text1 }}

      <template v-slot:actions>
        <v-btn color="blue" variant="text" @click="snackbar1 = false">
          إغلاق
        </v-btn>
      </template>
    </v-snackbar>
  </div>
  <div>
    <v-snackbar v-model="snackbar2" :timeout="timeout2">
      {{ text2 }}

      <template v-slot:actions>
        <v-btn color="blue" variant="text" @click="snackbar2 = false">
          إغلاق
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import { MDBBreadcrumb, MDBBreadcrumbItem } from "mdb-vue-ui-kit";
import { ref } from "vue";
import {
  collection,
  getDocs,
  getFirestore,
  updateDoc,
  doc,
  getDoc,
  where,
  query,
} from "firebase/firestore";

import { initializeApp } from "firebase/app";
const firebaseConfig = {
  apiKey: "AIzaSyBOlDn6NmPGHHfdY-gYHvnA6MoM-y0Xbmo",
  authDomain: "elemam-center-for-training.firebaseapp.com",
  projectId: "elemam-center-for-training",
  storageBucket: "elemam-center-for-training.appspot.com",
  messagingSenderId: "253703295162",
  appId: "1:253703295162:web:927a97dbbc2276f30d7283",
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);
import AddSub from "../components/Add_Sub.vue";
export default {
  name: "Main_Class",
  emits: ["getData"],
  computed: {
    UserAdmin() {
      return this.$store.state.UserAdmin;
    },
  },
  data() {
    return {
      UserId: null,
      ShowBtnToUser: null,
      AllData: [],
      showAddSub: null,
      Ids: [],
      MainId: "",
      showDownloadIcon: null,
      Type: "",
      Lang: "",
      Class: "",
      Edit1: "",
      Admin: true,
      num: "",
      CachCourse_Video: 0,
      CachCourse_PdfPrice_1: 0,
      CachCourse_PdfPrice_2: 0,
      AllCourse: "",
      Close: false,
      BillVedio: "",
      BillName: "",
      BillPrice: "",
      BillType: "",
      BillClass: "",
      BillLang: "",
      SubName: "",
      FullName: `
       ${localStorage.getItem("username_1")} ${localStorage.getItem(
        "username_2"
      )} ${localStorage.getItem("username_3")}
       `,
      PayAllCourse: null,
      snackbar: false,
      snackbar1: false,
      snackbar2: false,
      text: "تم نسخ الرقم للحافظة",
      text1: "عليك تسجيل الدخول حتي يتم فتح الإختبار لك",
      text2: "عليك تسجيل الدخول حتي تستطيع شراء الكورسات",
      timeout: 3000,
      timeout1: 5000,
      timeout2: 5000,
      Show_Open_Test: null,
      UserAdminState: null,
    };
  },
  props: ["Main_Id"],
  components: {
    MDBBreadcrumb,
    MDBBreadcrumbItem,
    AddSub,
  },
  mounted() {
    setInterval(() => {
      if (localStorage.getItem("userid") === null) {
        this.UserId = false;
      } else {
        this.UserId = true;
      }
    }, 100);
    this.CheckAboutUserState();
    setTimeout(() => {
      location.href = `${location.href}#Main_Class`;
    }, 10);
    setTimeout(() => {
      this.getvalues();
    }, 10);
    setTimeout(() => {
      this.getdata();
    }, 100);
  },
  methods: {
    CheckAboutUser_1() {
      // setTimeout(() => {
      // this.UserId = localStorage.getItem("userid") ? true : false;
      if (localStorage.getItem("userid") === null) {
        this.UserId = false;
      } else {
        this.UserId = true;
        this.AllTest();
      }
      this.snackbar2 = !this.UserId;

      // }, 100);
    },
    CheckAboutUser() {
      // setTimeout(() => {
      // this.UserId = localStorage.getItem("userid") ? true : false;
      if (localStorage.getItem("userid") === null) {
        this.UserId = false;
      } else {
        this.UserId = true;
      }
      this.snackbar1 = !this.UserId;
      // }, 100);
    },
    async CheckAboutUserState() {
      // ShowBtnToUser
      try {
        const q_Admin = query(
          collection(db, "المشرفين"),
          where("userid", "==", localStorage.getItem("userid"))
        );
        const querySnapshot_Admin = await getDocs(q_Admin);
        if (!querySnapshot_Admin.empty) {
          // Check About Powers

          const docRef = doc(db, "المشرفين", localStorage.getItem("userid"));
          const docSnap = await getDoc(docRef);

          if (docSnap.exists()) {
            // if (docSnap.data().powers === "الكل") {
            this.ShowBtnToUser = "Admin";
            // }
          }
        }
      } catch (error) {
        error;
      }
      try {
        const q_User = query(
          collection(db, "الطلاب"),
          where("userid", "==", localStorage.getItem("userid"))
        );
        const querySnapshot_User = await getDocs(q_User);
        if (!querySnapshot_User.empty) {
          this.ShowBtnToUser = "Student";
        }
      } catch (error) {
        error;
      }
    },

    copyTextSvg(event) {
      event.stopPropagation();
      event.target.parentElement.parentElement.classList.add("green");
      setTimeout(() => {
        event.target.parentElement.parentElement.classList.remove("green");
      }, 5000);

      navigator.clipboard.writeText(
        event.target.parentElement.parentElement.children[0].innerHTML
      );
      this.snackbar = true;
    },
    copyText(event) {
      event.stopPropagation();
      event.target.parentElement.classList.add("green");
      setTimeout(() => {
        event.target.parentElement.classList.remove("green");
      }, 5000);
      navigator.clipboard.writeText(
        event.target.parentElement.parentElement.children[0].innerHTML
      );
      this.snackbar = true;
    },
    copyTextDad(event) {
      event.stopPropagation();
      event.target.classList.add("green");
      setTimeout(() => {
        event.target.classList.remove("green");
      }, 5000);
      navigator.clipboard.writeText(
        event.target.parentElement.children[0].innerHTML
      );
      this.snackbar = true;
    },
    PayAllCourseFunction() {
      this.PayAllCourse = !this.PayAllCourse;
    },
    AllTest() {
      this.SubName = `جميع اختبارات ${this.Class}`;
      this.BillPrice = 100;
      this.BillName = "جميع الإختبارات";
      this.BillType = localStorage.getItem("updateType");
      this.BillLang = localStorage.getItem("updateLang");
      this.BillClass = localStorage.getItem("updateClass");
      this.Close = true;
    },
    AllCourses() {
      this.SubName = `جميع مواد ${this.Class}`;
      this.BillPrice = 1500;
      this.BillName = "جميع المواد";
      this.BillType = localStorage.getItem("updateType");
      this.BillLang = localStorage.getItem("updateLang");
      this.BillClass = localStorage.getItem("updateClass");
      this.Close = true;
    },

    // async pay_1() {
    //   const API =
    //     "ZXlKaGJHY2lPaUpJVXpVeE1pSXNJblI1Y0NJNklrcFhWQ0o5LmV5SmpiR0Z6Y3lJNklrMWxjbU5vWVc1MElpd2ljSEp2Wm1sc1pWOXdheUk2T1RRd056UXdMQ0p1WVcxbElqb2lNVGN3TVRVeE56Z3dNUzQwTkRBek9USWlmUS5yTXlWZEl0RzUwRGJWb0R0aXlWSGFNaDBmWXVxV2R3TG4xUjVvV3ZGUXZDTTcwUzBrZ3EzTU9JY2t6dVJsVFVxVWVTbVBETXJLNXVKaTVfN0MwZWlKZw==";
    //   let Data = {
    //     api_key: API,
    //   };
    //   let request = await fetch("https://accept.paymob.com/api/auth/tokens", {
    //     method: "post",
    //     headers: { "Content-Type": "application/json" },
    //     body: JSON.stringify(Data),
    //   });

    //   let response = await request.json();

    //   if (response && response.token) {
    //     let token = response.token;
    //     this.pay_2(token);
    //   }
    //   let token = response.token;
    //   this.pay_2(token);
    // },
    // async pay_2(token) {
    //   let Data = {
    //     auth_token: token,
    //     delivery_needed: "false",
    //     amount_cents: `${this.BillPrice}00`,
    //     currency: "EGP",
    //     merchant_order_id:
    //       Date.now() + Math.floor(Math.random() * 100000000000) + 10000000000,
    //     integration_id: 4352564,
    //     lock_order_when_paid: "false",
    //     order_description: "Product description goes here", // وصف المنتج - قم بتحديثه
    //     order_items: [],
    //     items: [],
    //   };
    //   let request = await fetch(
    //     "https://accept.paymob.com/api/ecommerce/orders",
    //     {
    //       method: "post",
    //       headers: { "Content-Type": "application/json" },
    //       body: JSON.stringify(Data),
    //     }
    //   );
    //   let response = await request.json();
    //   let id = response.id;
    //   this.pay_3(token, id);
    // },

    // async pay_3(token, id) {
    //   let userid = localStorage.getItem("userid");
    //   const documentRef = doc(db, "الطلاب", userid);
    //   const documentSnapshot = await getDoc(documentRef);
    //   const fieldName = "pay";
    //   const currentFieldValue = documentSnapshot.data()[fieldName];
    //   let Data = {
    //     auth_token: token,
    //     amount_cents: `${this.BillPrice}00`,
    //     expiration: 3600,
    //     order_id: id,
    //     currency: "EGP",
    //     integration_id: 4399813,
    //     lock_order_when_paid: "false",
    //     order_description: "Product description goes here", // وصف المنتج - قم بتحديثه
    //     order_items: [],
    //     billing_data: {
    //       apartment: "803",
    //       email: documentSnapshot.data().email,
    //       floor: "42",
    //       first_name: this.FullName,
    //       street: "Ethan Land",
    //       building: "8028",
    //       phone_number: documentSnapshot.data().phone,
    //       shipping_method: "PKG",
    //       postal_code: "01898",
    //       city: "Jaskolskiburgh",
    //       country: "CR",
    //       last_name: "Nicolas",
    //       state: "Utah",
    //     },
    //   };
    //   let request = await fetch(
    //     "https://accept.paymob.com/api/acceptance/payment_keys",
    //     {
    //       method: "post",
    //       headers: { "Content-Type": "application/json" },
    //       body: JSON.stringify(Data),
    //     }
    //   );

    //   let response = await request.json();

    //   // تحقق مما إذا كانت الاستجابة تحتوي على الـ token
    //   let TheToken = response.token;

    //   let newObject = {
    //     BillName: this.BillName,
    //     BillType: this.BillType,
    //     BillLang: this.BillLang,
    //     BillClass: this.BillClass,
    //     BillPrice: `${this.BillPrice}00`,
    //     BillItem: this.SubName,
    //     Time: new Date(),
    //     order_id: id,
    //     success: null,
    //   };
    //   // إضافة الكائن الجديد إلى القيمة الحالية للحقل
    //   currentFieldValue.push(newObject);

    //   // تحديث المستند بالقيمة الجديدة
    //   await updateDoc(documentRef, {
    //     [fieldName]: currentFieldValue,
    //   });
    //   this.CardPayment_1(TheToken);
    // },
    // CardPayment_1(token) {
    //   let iframURL = `https://accept.paymob.com/api/acceptance/iframes/806158?payment_token=${token}`;
    //   location.href = iframURL;
    // },
    async pay1() {
      const API =
        "ZXlKaGJHY2lPaUpJVXpVeE1pSXNJblI1Y0NJNklrcFhWQ0o5LmV5SmpiR0Z6Y3lJNklrMWxjbU5vWVc1MElpd2ljSEp2Wm1sc1pWOXdheUk2T1RRd056UXdMQ0p1WVcxbElqb2lNVGN3TVRVeE56Z3dNUzQwTkRBek9USWlmUS5yTXlWZEl0RzUwRGJWb0R0aXlWSGFNaDBmWXVxV2R3TG4xUjVvV3ZGUXZDTTcwUzBrZ3EzTU9JY2t6dVJsVFVxVWVTbVBETXJLNXVKaTVfN0MwZWlKZw==";
      let Data = {
        api_key: API,
      };
      let request = await fetch("https://accept.paymob.com/api/auth/tokens", {
        method: "post",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(Data),
      });

      let response = await request.json();

      if (response && response.token) {
        let token = response.token;
        this.pay2(token);
      }
      let token = response.token;
      this.pay2(token);
    },
    async pay2(token) {
      let Data = {
        auth_token: token,
        delivery_needed: "false",
        amount_cents: `${this.BillPrice}00`,
        currency: "EGP",
        merchant_order_id:
          Date.now() + Math.floor(Math.random() * 100000000000) + 10000000000,
        integration_id: 4352564,
        lock_order_when_paid: "false",
        order_description: "Product description goes here", // وصف المنتج - قم بتحديثه
        order_items: [],
        items: [],
      };
      let request = await fetch(
        "https://accept.paymob.com/api/ecommerce/orders",
        {
          method: "post",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(Data),
        }
      );
      let response = await request.json();
      let id = response.id;
      this.pay3(token, id);
    },

    async pay3(token, id) {
      let userid = localStorage.getItem("userid");
      const documentRef = doc(db, "الطلاب", userid);
      const documentSnapshot = await getDoc(documentRef);
      const fieldName = "pay";
      const currentFieldValue = documentSnapshot.data()[fieldName];
      let Data = {
        auth_token: token,
        amount_cents: `${this.BillPrice}00`,
        expiration: 3600,
        order_id: id,
        currency: "EGP",
        integration_id: 4352564,
        lock_order_when_paid: "false",
        order_description: "Product description goes here", // وصف المنتج - قم بتحديثه
        order_items: [],
        billing_data: {
          apartment: "803",
          email: documentSnapshot.data().email,
          floor: "42",
          first_name: this.FullName,
          street: "Ethan Land",
          building: "8028",
          phone_number: documentSnapshot.data().phone,
          shipping_method: "PKG",
          postal_code: "01898",
          city: "Jaskolskiburgh",
          country: "CR",
          last_name: "Nicolas",
          state: "Utah",
        },
      };
      let request = await fetch(
        "https://accept.paymob.com/api/acceptance/payment_keys",
        {
          method: "post",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(Data),
        }
      );

      let response = await request.json();

      // تحقق مما إذا كانت الاستجابة تحتوي على الـ token
      let TheToken = response.token;

      let newObject = {
        BillName: this.BillName,
        BillType: this.BillType,
        BillLang: this.BillLang,
        BillClass: this.BillClass,
        BillPrice: `${this.BillPrice}00`,
        BillItem: this.SubName,
        Time: new Date(),
        order_id: id,
        success: null,
      };
      // إضافة الكائن الجديد إلى القيمة الحالية للحقل
      currentFieldValue.push(newObject);

      // تحديث المستند بالقيمة الجديدة
      await updateDoc(documentRef, {
        [fieldName]: currentFieldValue,
      });
      this.CardPayment(TheToken);
    },
    CardPayment(token) {
      let iframURL = `https://accept.paymob.com/api/acceptance/iframes/802769?payment_token=${token}`;
      location.href = iframURL;
    },

    async Updata() {
      let input1 = document.querySelectorAll(".main_box  input.input1");
      // let input2 = document.querySelectorAll(".main_box  input.input2");
      // let input3 = document.querySelectorAll(".main_box  input.input3");
      // let input4 = document.querySelectorAll(".main_box  input.input4");
      // let input5 = document.querySelectorAll(".main_box  input.input5");
      // let input6 = document.querySelectorAll(".main_box  input.input6");
      // let input7 = document.querySelectorAll(".main_box  input.input7");
      // let input8 = document.querySelectorAll(".main_box  input.input8");
      let sentence = localStorage.getItem("updateType");
      let words = sentence.split(" ");
      let firstWord = words[0];
      const washingtonRef = doc(
        db,
        `كورسات - ${firstWord} - ${localStorage.getItem(
          "updateLang"
        )} - ${localStorage.getItem("updateClass")}`,
        this.Ids[this.num]
      );
      await updateDoc(washingtonRef, {
        BookLink: input1[this.num].value,
        // FreeCourse_Video: input2[this.num].value,
        // FreeCourse_Pdf_1: input3[this.num].value,
        // FreeCourse_Pdf_2: input4[this.num].value,
        // CachCourse_Video: input5[this.num].value,
        // CachCourse_PdfPrice_1: input6[this.num].value,
        // CachCourse_PdfPrice_2: input7[this.num].value,
        // AllCourse: input8[this.num].value,
      });
      this.getdata();
    },
    EditFunction() {
      let box = document.querySelectorAll(".main_box");
      let svg = document.querySelectorAll(".main_box > svg");
      let span = document.querySelectorAll(".main_box > span");
      let inputs = document.querySelectorAll(".main_box  input");
      for (let i = 0; i < svg.length; i++) {
        svg[i].onclick = async () => {
          this.num = i;
          box.forEach((e) => {
            e.classList.remove("border-[--main-color]");
          });
          span.forEach((e) => {
            e.classList.add("hidden");
          });
          span[i].classList.remove("hidden");
          inputs.forEach((e) => {
            e.classList.add("pointer-events-none");
          });
          box[i].classList.add("border-[--main-color]");
          box[i].querySelectorAll("input").forEach((e) => {
            e.classList.remove("pointer-events-none");
          });
        };
      }
    },
    getvalues() {
      this.Type = localStorage.getItem("updateType");
      this.Lang = localStorage.getItem("updateLang");
      this.Class = localStorage.getItem("updateClass");
    },
    AddSubToStore() {
      let link = document.querySelectorAll(".main_box .book ");
      for (let i = 0; i < link.length; i++) {
        link[i].querySelector("a:last-child").parentElement.onclick = () => {
          localStorage.setItem("updateSub", this.AllData[i].sub_name);
        };
      }
    },

    CloseAndOpenAddSub() {
      this.showAddSub = !this.showAddSub;
    },
    CloseAndOpenEditSub() {
      this.ShowEdit = !this.ShowEdit;
    },
    async getdata() {
      this.showDownloadIcon = true;
      this.AllData = [];
      let sentence = localStorage.getItem("updateType");
      let words = sentence.split(" ");
      let firstWord = words[0];
      const querySnapshot = await getDocs(
        collection(
          db,
          `كورسات - ${firstWord} - ${localStorage.getItem(
            "updateLang"
          )} - ${localStorage.getItem("updateClass")}`
        )
      );
      querySnapshot.forEach((doc) => {
        this.AllData.push(doc.data());
        this.Ids.push(doc.id);
      });
      this.showDownloadIcon = false;
      AllData.length === 0
        ? (this.showDownloadIcon = false)
        : (this.showDownloadIcon = true);
      setTimeout(() => {
        this.EditFunction();
        this.AddSubToStore();
        // this.Open_Test();
      }, 1000);
    },
  },
  setup() {
    const activeItem = ref("collapseOne");
    return {
      activeItem,
    };
  },
};
</script>
<style lang="scss" scoped>
.v-snackbar__content {
  margin: auto;
}
.Main_Class {
  background-image: url("../assets/oie_iipONfIda6gh.png");
  background-size: cover;
  background-position: center top;
  background-attachment: fixed;
}
.popup_2 {
  background-image: url("../assets/oie_iipONfIda6gh.png");
  background-size: cover;
  background-position: center top;
  background-attachment: fixed;
}
section {
  div {
    border: 1px solid var(--main-color);
    background: #fff;
    border-radius: 5px;
    font-size: 21px;
    color: var(--main-color);
    transition: 0.3s;
    &:hover {
      background: var(--main-color);
      color: #fff;
    }
  }
}
nav {
  background: #fff;
  padding: 15px;
  border-radius: 5px;
  font-size: 14px;
  &.nav_1 {
    padding: 0;
    box-shadow: 0 0 10px #ddd;
  }
  nav ol.breadcrumb {
    margin: 0 !important;
    li {
      transition: 0.3s;
      font-weight: bold;
      &:hover {
        color: var(--main-color) !important;
      }
    }
    li.breadcrumb-item.active {
      font-weight: bold;
      color: var(--main-color);
    }
  }
}
.border-[--main-color] {
  border: 1px solid var(--main-color) !important;
}

.hover-0 {
  transition: 0.3s;
}
.hover-0:hover {
  background: var(--main-color);
  color: #fff;
}
.hover-0:hover svg,
.hover-0:hover span {
  color: #fff;
}
.table_1 {
  height: 35px;
  border: 1px solid var(--main-color);
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50%;
  border-bottom: none;
  &:last-child {
    border: 1px solid var(--main-color);
  }
}
.table_2 {
  border: 1px solid var(--main-color);
  height: 35px;
  width: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  border-right: none;
  border-top: none;

  &:last-child {
    border-top: 1px solid var(--main-color);
  }
}
.green {
  color: #3fbb3f !important;
}
table th,
td {
  text-align: center;
  border: 1px solid #ddd;
  padding: 10px;
  color: var(--main-color);
  width: 50%;
  font-weight: bold;
}
@media (min-width: 1200px) {
}

@media (min-width: 768px) and (max-width: 1199px) {
  // .body .main_box {
  //   width: 100% !important;
  // }
}

@media (max-width: 767px) {
  .book {
    flex-direction: column;
    & > div,
    a {
      width: 100%;
    }
  }
  .PayAllCourse .body {
    flex-direction: column;
    gap: 10px;
    & > div {
      width: 100% !important;
      div {
        // flex-direction: column;
        & > div {
          // width: 100%;
        }
      }
    }
  }
  .Main_Class {
    margin-top: -20px !important;
    .container {
      padding-top: 123px !important;
    }
  }
  .body .main_box {
    width: 100% !important;
  }
  section {
    flex-direction: column;
    & > div {
      width: 100%;
    }
  }
  .nav_1 {
    flex-direction: column;
    align-items: stretch;
    & > div {
      justify-content: center;
    }
  }
}
</style>
