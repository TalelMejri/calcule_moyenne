<template>
  <div>
    <b-alert
      class="mt-4"
      :show="alert.dismissCountDown"
      dismissible
      :variant="alert.variant"
      @dismissed="alert.dismissCountDown = 0"
    >
      <p>{{ alert.msg }}</p>
    </b-alert>

    <form-wizard @onComplete="onComplete">
      <tab-content title="معلومات شخصية" :selected="true">
        <div class="form-group">
          <label for="first_name">الأسم</label>
          <input
            id="first_name"
            type="text"
            name="first_name"
            class="form-control"
            :class="hasError('first_name') ? 'is-invalid' : ''"
            placeholder="ادخل اسمك"
            v-model="formData.first_name"
          />
          <div v-if="hasError('first_name')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.first_name.required">
              الرجاء ادخال اسمك.
            </div>
          </div>
        </div>
        <div class="form-group">
          <label for="last_name">اللقب</label>
          <input
            type="text"
            id="last_name"
            name="last_name"
            class="form-control"
            :class="hasError('last_name') ? 'is-invalid' : ''"
            placeholder="ادخل لقبك"
            v-model="formData.last_name"
          />
          <div v-if="hasError('last_name')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.last_name.required">
              الرجاء ادخال لقبك.
            </div>
          </div>
        </div>
        <div class="form-group">
          <label for="birth_date">تاريح الولادة</label>
          <input
            type="date"
            id="birth_date"
            @change="formData.troupe = null"
            class="form-control"
            :class="hasError('birth_date') ? 'is-invalid' : ''"
            placeholder="الرجاء ادخال تاريخ ولادتك"
            v-model="formData.birth_date"
          />
          <div v-if="hasError('birth_date')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.birth_date.required">
              الرجاء ادخال تاريخ ولادتك.
            </div>
            <div class="error" v-if="!$v.formData.birth_date.dateValidator">
              الرجاء ادخال تاريخ ولادتك بشكل صحيح.
            </div>
          </div>
        </div>
        <div class="form-group">
          <label for="sexe">الجنس</label>
          <select
            id="sexe"
            class="form-control"
            :class="hasError('sexe') ? 'is-invalid' : ''"
            v-model="formData.sexe"
            @change="formData.troupe = null"
          >
            <option disabled="disabled" selected="selected">اختر جنسك</option>

            <option value="F">انثى</option>
            <option value="H">ذكر</option>
          </select>
          <div v-if="hasError('sexe')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.sexe.required">
              الرجاء اختيار جنسك.
            </div>
          </div>
        </div>
        <div class="form-group">
          <label for="image">صورة</label>
          <input
            id="image"
            type="file"
            name="image"
            accept="image/*"
            :class="hasError('image') ? 'is-invalid' : ''"
            class="form-control"
            @change="convert64"
            ref="file"
          />
          <div v-if="hasError('image')" class="invalid-feedback">
            <div
              class="error"
              v-if="
                !$v.formData.image.required || !$v.formData.image.isFileImage
              "
            >
              الرجاء ادخال صورة.
            </div>
          </div>
        </div>
        <div class="form-group">
          <label for="cin">رقم ب.ت.و</label>
          <input
            id="cin"
            type="number"
            name="cin"
            class="form-control"
            :class="hasError('cin') ? 'is-invalid' : ''"
            placeholder="ادخل رقم ب.ت.و"
            v-model="formData.cin"
          />
          <div v-if="hasError('cin')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.cin.required">
              الرجاء ادخال رقم ب.ت.و(او رقم ب.ت.و الولي )
            </div>
            <div
              class="error"
              v-if="!$v.formData.cin.numeric || !$v.formData.cin.between"
            >
              الرجاء ادخال رقم ب.ت.و بشكل صحيح.
            </div>
            <!-- <div
              class="error"
              v-if="!$v.formData.cin.isUnique"
            >
              Cette cin est deja utilisée.
            </div> -->
          </div>
        </div>
        <span class="caption">
          هل لديك حساب ?
          <router-link color="primary" to="/login"
            >تسجيل الدخول</router-link
          ></span
        >
      </tab-content>

      <tab-content title="المعطيات الكشفية">
        <div class="form-group">
          <label for="role">مهمة</label>
          <select
            id="role"
            :class="hasError('role') ? 'is-invalid' : ''"
            class="form-control"
            v-model="formData.role"
          >
            <option disabled="disabled" selected="selected">اختر مهمتك</option>
            <option v-for="role in roles" :key="role.id" :value="role.id">
              {{ role.name }}
            </option>
          </select>
          <div v-if="hasError('role')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.role.required">
              <span>مهمة مطلوبة</span>
            </div>
          </div>
        </div>
        <div
          class="form-group"
          v-if="
            roles.length != 0 &&
            roles[formData.role ? formData.role - 2 : 0].ename ==
              'Unit Assigned Leader'
          "
        >
          <label for="responsability">المسؤولية</label>
          <select
            id="responsability"
            :class="hasError('responsability') ? 'is-invalid' : ''"
            class="form-control"
            v-model="formData.responsability"
          >
            <option disabled="disabled" selected="selected">اختر فرقتك</option>

            <option
              v-for="responsability in responsablities"
              :key="responsability.id"
              :value="responsability.id"
            >
              {{ responsability.name }}
            </option>
          </select>
          <div v-if="hasError('responsability')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.responsability.required">
              <span>المسؤولية مطلوبة</span>
            </div>
          </div>
        </div>
        <div
          class="form-group"
          v-if="
            roles.length != 0 &&
            roles[formData.role ? formData.role - 2 : 0].name !=
              'قيادة الفوج' &&
            roles[formData.role ? formData.role - 2 : 0].name != 'ولي'
          "
        >
          <label for="troupe">الفرقة</label>
          <select
            id="troupe"
            :class="hasError('troupe') ? 'is-invalid' : ''"
            class="form-control"
            v-model="formData.troupe"
          >
            <option disabled="disabled" selected="selected">اختر فرقتك</option>

            <option
              v-for="troupe in troupes"
              :key="troupe.id"
              v-show="
                (age >= troupe.min_age &&
                  age <= troupe.max_age &&
                  formData.sexe == troupe.gender) ||
                (roles[formData.role ? formData.role - 2 : 0].name !=
                  'قيادة الفوج' &&
                  roles[formData.role ? formData.role - 2 : 0].name != 'ولي' &&
                  formData.sexe == troupe.gender &&
                  roles[formData.role ? formData.role - 2 : 0].name != 'فرد')
              "
              :value="troupe.id"
            >
              {{ troupe.name }}
            </option>
          </select>
          <div v-if="hasError('troupe')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.troupe.required">
              <span>الفرقة مطلوبة</span>
            </div>
          </div>
        </div>
      </tab-content>
      <tab-content title="الاتصال">
        <div class="form-group">
          <div class="form-group">
            <label for="email">البريد الإلكتروني</label>
            <input
              id="email"
              type="email"
              name="email"
              class="form-control"
              :class="hasError('email') ? 'is-invalid' : ''"
              placeholder="ادخل البريد الإلكترونيك"
              v-model="formData.email"
            />
            <div v-if="hasError('email')" class="invalid-feedback">
              <div class="error" v-if="!$v.formData.email.required">
                الرجاء ادخال البريد الإلكتروني.
              </div>
              <div class="error" v-if="!$v.formData.email.email">
                الرجاء ادخال البريد الإلكتروني بشكل صحيح.
              </div>
              <div class="error" v-if="!$v.formData.email.isUnique">
                البريد الإلكتروني هذا مستخدم من قبل.
              </div>
            </div>
          </div>
          <label for="phone_number">رقم الهاتف</label>
          <input
            id="phone_number"
            type="number"
            name="phone_numberf"
            class="form-control"
            :class="hasError('phone_number') ? 'is-invalid' : ''"
            placeholder="ادخل رقم الهاتف"
            v-model="formData.phone_number"
          />
          <div v-if="hasError('phone_number')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.phone_number.required">
              الرجاء ادخال رقم الهاتف.
            </div>
            <div
              class="error"
              v-if="
                !$v.formData.phone_number.numeric ||
                !$v.formData.phone_number.between
              "
            >
              الرجاء ادخال رقم الهاتف بشكل صحيح.
            </div>
          </div>
        </div>
      </tab-content>
      <tab-content title="معرفات">
        <div class="form-group">
          <label for="password">الرمز السري</label>
          <input
            id="password"
            type="password"
            :class="hasError('password') ? 'is-invalid' : ''"
            class="form-control"
            v-model="formData.password"
          />
          <div v-if="hasError('password')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.password.required">
              الرجاء ادخال رمز السر.
            </div>
            <div
              class="error"
              v-if="
                !$v.formData.password.minLength ||
                !$v.formData.password.maxLength
              "
            >
              الرمز السري يجب ان يكون بين 8 و 30 حرف.
            </div>
          </div>
        </div>
        <div class="form-group">
          <label for="confirm_password">اعادة الرمز السري</label>
          <input
            id="confirm_password"
            :class="hasError('confirm_password') ? 'is-invalid' : ''"
            class="form-control"
            type="password"
            v-model="formData.confirm_password"
          />
          <div v-if="hasError('confirm_password')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.confirm_password.required">
              الرجاء ادخال رمز السر مرة اخرى.
            </div>
            <div
              class="error"
              v-if="
                !$v.formData.confirm_password.minLength ||
                !$v.formData.confirm_password.maxLength
              "
            >
              الرمز السري يجب ان يكون بين 8 و 30 حرف.
            </div>
            <div class="error" v-if="!$v.formData.confirm_password.confirmed">
              الرجاء ادخال رمز السر مرة اخرى.
            </div>
          </div>
        </div>
      </tab-content>
    </form-wizard>
    <v-dialog v-model="dialog" hide-overlay persistent width="300">
      <v-card color="primary" dark>
        <v-card-text>
          الرجاء الانتظار
          <v-progress-linear
            indeterminate
            color="white"
            class="mb-0"
          ></v-progress-linear>
        </v-card-text>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import { mapActions } from "vuex";
import { FormWizard, TabContent, ValidationHelper } from "vue-step-wizard";
import "vue-step-wizard/dist/vue-step-wizard.css";
import {
  required,
  requiredIf,
  email,
  numeric,
  between,
  minLength,
  maxLength,
  sameAs,
} from "vuelidate/lib/validators";

const dateValidator = (date) => {
  return new Date(date).setHours(0, 0, 0, 0) <= new Date().setHours(0, 0, 0, 0);
};
const isFileImage = (file) => {
  if (file == null) {
    return true;
  }
  return file ? file.includes("image") : false;
};
export default {
  name: "StepFormValidation",
  components: {
    FormWizard,
    TabContent,
  },
  mixins: [ValidationHelper],
  updated() {
    // console.log(this.formData.image);
  },
  data() {
    return {
      dialog: false,
      roles: [],
      troupes: {},
      uniqueCin: false,
      uniqueEmail: false,
      responsablities: [],
      formData: {
        first_name: "",
        last_name: "",
        email: null,
        cin: null,
        password: null,
        confirm_password: null,
        birth_date: null,
        role: null,
        troupe: null,
        sexe: null,
        image: null,
        responsability: null,
      },
      validationRules: [
        {
          first_name: { required },
          last_name: { required },
          birth_date: { required, dateValidator },
          sexe: { required },
          cin: {
            required,
            numeric,
            between: between(1000000, 99999999),
          },
          image: { isFileImage },
        },
        {
          role: {
            required,
          },
          responsability: {
            required: requiredIf(function () {
              let index =
                this.formData.role !== null ? this.formData.role - 2 : 0;
              return this.roles.length != 0
                ? this.roles[index].ename == "Unit Assigned Leader"
                : false;
            }),
          },
          troupe: {
            required: requiredIf(function () {
              let index =
                this.formData.role !== null ? this.formData.role - 2 : 0;
              return this.roles.length != 0
                ? this.roles[index].name != "قيادة الفوج" &&
                    this.roles[index].name != "ولي"
                : false;
            }),
          },
        },
        {
          phone_number: { required, between: between(10000000, 99999999) },
          email: {
            required,
            email,
            async isUnique(value) {
              const response = await this.$axios(`/unique/${value}`);
              return response.status == 200 || value == "";
            },
          },
        },
        {
          password: {
            required,
            minLength: minLength(8),
            maxLength: maxLength(30),
          },
          confirm_password: {
            required,
            minLength: minLength(8),
            maxLength: maxLength(30),
            confirmed: sameAs("password"),
          },
        },
      ],
      alert: {
        dismissCountDown: null,
        variant: null,
        msg: null,
      },
    };
  },
  methods: {
    ...mapActions(["register"]),
    Register() {
      this.alert.msg = "";
      this.dialog = true;
      this.register(this.formData)
        .then(() => {
          if (this.$store.getters.regStatus == 2) {
            this.alert.dismissCountDown = 10;
            this.alert.variant = "danger";
            this.alert.msg = this.$store.getters.regMessage;
          }
        })
        .catch(() => {})
        .finally(() => {
          this.dialog = false;
        });
    },
    onComplete() {
      this.Register();
    },
    convert64(e) {
      var file = e.target.files[0];
      this.srcImage = file;
      var reader = new FileReader();
      reader.onloadend = () => {
        this.formData.image = reader.result;
      };
      this.image = file;
      reader.readAsDataURL(file);
    },
  },
  created() {
    this.$axios.get("/roles").then((response) => {
      this.roles = response.data;
    });
    this.$axios.get("/troupes").then((response) => {
      this.troupes = response.data;
    });
    this.$axios.get("/responsablities").then((response) => {
      this.responsablities = response.data;
    });
  },
  computed: {
    age() {
      let date = new Date(this.formData.birth_date);
      let ageDiff = new Date().getFullYear() - date.getFullYear();
      return ageDiff;
    },
  },
};
</script>
<style>
::-webkit-input-placeholder {
  text-align: right;
}
:-moz-placeholder {
  /* Firefox 18- */
  text-align: right;
}
::-moz-placeholder {
  /* Firefox 19+ */
  text-align: right;
}
:-ms-input-placeholder {
  text-align: right;
}
input {
  text-align: right;
}
option,
select {
  text-align: right;
}
.error {
  border-color: red;
  border-width: 1px;
  border-style: solid;
  border-radius: 5px;
  padding: 5px;
  color: white !important;
}
</style>