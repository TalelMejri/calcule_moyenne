<template>
  <div class="about py-5">
    <div class="row">
      <primaire_calcul
        class="col-md-4"
        :show_card="show_card"
        @selection="show_card = !show_card"
        :primaire="primaire"
        :niveau="niveau"
        :titel="titel_primaire"
      ></primaire_calcul>
      <college_calcul
        class="col-md-4"
        :show_card="show_card"
        @selection="show_card = !show_card"
        :niveau="niveau_college"
        :titel="titel_college"
      ></college_calcul>
    </div>
  </div>
</template>
<script>
import primaire_calcul from "@/components/primaire_calcul.vue";
import college_calcul from "@/components/college_calcul.vue";
export default {
  name: "AboutView",
  data() {
    return {
      show_card: true,
      titel_primaire: "المرحلة الابتدائية",
      primaire: {
        domaine: {
          arabic: {
            name: "مجال العربية",
            matiere: [
              "تواصل شفوي",
              "الخط",
              "القراءة",
              "الانتاج الكتابي",
              "معدل مجال اللغة العربية",
            ],
          },
          science: {
            name: "مجال العلوم",
            matiere: [
              "الرياضيات",
              "الايقاظ العلمي",
              "التربية التكنولوجية",
              "معدل مجال العلوم",
            ],
          },
          nourir_sup: {
            name: "مجال التنشئة",
            matiere: [
              "تربية اسلامية",
              "تربية موسيقية",
              "تربية تشكيلية",
              "التاريخ",
              "الجغرافيا",
              "المدنية",
              "تربية بدنية",
              "معدل مجال التنشئة",
            ],
          },
          nourir: {
            name: "مجال التنشئة",
            matiere: [
              "تربية اسلامية",
              "تربية موسيقية",
              "تربية تشكيلية",
              "تربية بدنية",
              "معدل مجال التنشئة",
            ],
          },
          francais: {
            name: "اللغة الفرنسية",
            matiere: ["Exp. Orale", "Pro. Ecrite", "Lecture", "Moy. Français"],
          },
          langue: {
            name: "اللغات الاجنبية",
            matiere: [
              "Exp. Orale",
              "Pro. Ecrite",
              "Lecture",
              "Anglais",
              "معدل اللغات الاجنبية",
            ],
          },
        },
      },
      titre_secondaire: "المرحلة الثانوي",
      premiere_secondaire: {},
      titel_college: "المرحلة الاعدادية",
      college: {
        domaine: {
          arabic: {
            name: "مادة العربية",
            coef: 4,
            matiere: [
              { name: "فرض المراقبة عدد 1 في دراسة النص", coef: 1 },
              { name: "فرض مراقبة عدد 1 في الانشاء", coef: 1 },
              { name: "الشفوي في مادة العربية", coef: 1 },
              { name: "الفرض التأليفي في الانشاء", coef: 2 },
              { name: "الفرض التأليفي في دراسة النص", coef: 2 },
              { name: "معدل العربية" },
            ],
          },
          francais: {
            name: "مادة الفرنسية",
            coef: 4,
            matiere: [
              { name: "فرض المراقبة عدد 1 في الفرنسية ", coef: 1 },
              { name: "فرض المراقبة عدد 2 في الفرنسية ", coef: 1 },
              { name: " الفرض التأليفي في الفرنسية ", coef: 2 },
              { name: "الشفوي في مادة الفرنسية", coef: 2 },
              { name: "معدل الفرنسية" },
            ],
          },
          anglais: {
            name: "مادة الانجليزية",
            coef: 1.5,
            matiere: [
              { name: "فرض المراقبة عدد 1 مادة الانجليزية", coef: 1 },
              { name: "فرض المراقبة عدد 2 مادة الانجليزية", coef: 1 },
              { name: " الفرض التأليفي مادة الانجليزية", coef: 2 },
              { name: "الشفوي مادة الانجليزية", coef: 1 },
              { name: "معدل الانجليزية" },
            ],
          },
          math: {
            name: "مادة الرياضيات",
            coef: 3,
            matiere: [
              { name: "فرض المراقبة عدد 1 مادة الرياضيات", coef: 1 },
              { name: "فرض المراقبة عدد 2 مادة الرياضيات", coef: 1 },
              { name: " الفرض التأليفي مادة الرياضيات", coef: 2 },
              { name: "معدل الرياضيات" },
            ],
          },
          physqiue: {
            name: "مادة العلوم الفيزيائية",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 مادة العلوم الفيزيائية", coef: 1 },
              { name: "الفرض التأليفي مادة العلوم الفيزيائية", coef: 2 },
              { name: "معدل العلوم الفيزيائية" },
            ],
          },
          science: {
            name: "مادة العلوم الطبيعية",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 مادة العلوم الطبيعية", coef: 1 },
              { name: "الفرض التأليفي مادة العلوم الطبيعية", coef: 2 },
              { name: "الشفوي / الأشغال التطبيقية", coef: 1 },
              { name: "معدل العلوم الطبيعية" },
            ],
          },
          history: {
            name: "مادة التاريخ",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 مادة التاريخ", coef: 1 },
              { name: "الفرض التأليفي مادة التاريخ", coef: 2 },
              { name: "الشفوي مادة التاريخ", coef: 1 },
              { name: "معدل التاريخ" },
            ],
          },
          geo: {
            name: "مادة الجغرافيا",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 مادة الجغرافيا", coef: 1 },
              { name: "الفرض التأليفي مادة الجغرافيا", coef: 2 },
              { name: "الشفوي مادة الجغرافيا", coef: 1 },
              { name: "معدل الجغرافيا" },
            ],
          },
          technique: {
            name: "مادة التربية التكنولوجية",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 مادة التربية التكنولوجية", coef: 1 },
              { name: "الفرض التأليفي مادة التربية التكنولوجية", coef: 2 },
              { name: "الشفوي مادة التربية التكنولوجية", coef: 1 },
              { name: "معدل التكنولوجية" },
            ],
          },
          islamic: {
            name: "مادة التربية الاسلامية",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 الاسلامية", coef: 1 },
              { name: "الفرض التأليفي الاسلامية", coef: 2 },
              { name: "الشفوي الاسلامية", coef: 1 },
              { name: " معدل التربية الاسلامية" },
            ],
          },
          civil: {
            name: "مادة التربية المدنية",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 المدنية", coef: 1 },
              { name: "الفرض التأليفي المدنية", coef: 2 },
              { name: "الشفوي المدنية", coef: 1 },
              { name: " معدل التربية المدنية" },
            ],
          },
          info: {
            name: "مادة الإعلامية",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عدد 1 الإعلامية", coef: 1 },
              { name: "الفرض التأليفي الإعلامية", coef: 2 },
              { name: " معدل الإعلامية" },
            ],
          },
          theatre: {
            name: "مادة المسرح",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة عددالمسرح  1", coef: 1 },
              { name: "الفرض التأليفي المسرح", coef: 2 },
              { name: "الشفوي المسرح", coef: 1 },
              { name: " معدل  المسرح" },
            ],
          },
          sport: {
            name: " مادة التربية البدنية",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة البدنية", coef: 1 },
              { name: "الفرض التأليفي البدنية", coef: 2 },
              { name: " معدل التربية البدنية" },
            ],
          },
          dessin: {
            name: " مادة التربية التشكيلية  ",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة التشكيلية", coef: 1 },
              { name: "الفرض التأليفي التشكيلية", coef: 2 },
              { name: " معدل التربية التشكيلية" },
            ],
          },
          music: {
            name: "مادة التربية الموسيقية ",
            coef: 1,
            matiere: [
              { name: "فرض المراقبة  الموسيقية", coef: 1 },
              { name: "الفرض التأليفي الموسيقية", coef: 2 },
              { name: "الشفوي الموسيقية", coef: 1 },
              { name: " معدل التربية الموسيقية" },
            ],
          },
        },
      },
    };
  },
  computed: {
    niveau_college() {
      return {
        "السنة السابعة أساسي": {
          name: "السنة السابعة أساسي",
          id: 1,
          modules: [
            this.college.domaine["arabic"],
            this.college.domaine["francais"],
            this.college.domaine["anglais"],
            this.college.domaine["math"],
            this.college.domaine["physqiue"],
            this.college.domaine["science"],
            this.college.domaine["history"],
            this.college.domaine["geo"],
            this.college.domaine["technique"],
            this.college.domaine["islamic"],
            this.college.domaine["civil"],
            this.college.domaine["info"],
            this.college.domaine["theatre"],
            this.college.domaine["sport"],
            this.college.domaine["dessin"],
            this.college.domaine["music"],
          ],
        },
        "السنة الثامنة أساسي  ": {
          name: "  السنة الثامنة أساسي",
          id: 2,
          modules: [
            this.college.domaine["arabic"],
            this.college.domaine["francais"],
            this.college.domaine["anglais"],
            this.college.domaine["math"],
            this.college.domaine["physqiue"],
            this.college.domaine["science"],
            this.college.domaine["history"],
            this.college.domaine["geo"],
            this.college.domaine["technique"],
            this.college.domaine["islamic"],
            this.college.domaine["civil"],
            this.college.domaine["info"],
            this.college.domaine["theatre"],
            this.college.domaine["sport"],
            this.college.domaine["dessin"],
            this.college.domaine["music"],
          ],
        },
        "  السنة التاسعة أساسي": {
          name: "  السنة التاسعة أساسي",
          id: 3,
          modules: [
            this.college.domaine["arabic"],
            this.college.domaine["francais"],
            this.college.domaine["anglais"],
            this.college.domaine["math"],
            this.college.domaine["physqiue"],
            this.college.domaine["science"],
            this.college.domaine["history"],
            this.college.domaine["geo"],
            this.college.domaine["technique"],
            this.college.domaine["islamic"],
            this.college.domaine["civil"],
            this.college.domaine["info"],
            this.college.domaine["theatre"],
            this.college.domaine["sport"],
            this.college.domaine["dessin"],
            this.college.domaine["music"],
          ],
        },
      };
    },
    niveau() {
      return {
        "السنة الاولى ابتدائي": {
          name: "السنة الاولى ابتدائي",
          id: 1,
          modules: [
            this.primaire.domaine["arabic"],
            this.primaire.domaine["science"],
            this.primaire.domaine["nourir"],
          ],
        },
        "السنة الثانية ابتدائي": {
          name: "السنة الثانية ابتدائي",
          id: 2,
          modules: [
            this.primaire.domaine["arabic"],
            this.primaire.domaine["science"],
            this.primaire.domaine["nourir"],
          ],
        },
        "السنة الثالثة ابتدائي": {
          name: "السنة الثالثة ابتدائي",
          id: 3,
          modules: [
            this.primaire.domaine["arabic"],
            this.primaire.domaine["science"],
            this.primaire.domaine["francais"],
            this.primaire.domaine["nourir"],
          ],
        },
        "السنة الرابعة ابتدائي": {
          name: "السنة الرابعة ابتدائي",
          id: 4,
          modules: [
            this.primaire.domaine["arabic"],
            this.primaire.domaine["science"],
            this.primaire.domaine["francais"],
            this.primaire.domaine["nourir"],
          ],
        },
        "السنة الخامسة ابتدائي": {
          name: "السنة الخامسة ابتدائي",
          id: 5,
          modules: [
            this.primaire.domaine["arabic"],
            this.primaire.domaine["science"],
            this.primaire.domaine["francais"],
            this.primaire.domaine["nourir_sup"],
          ],
        },
        "السنة السادسة ابتدائي": {
          name: "السنة السادسة ابتدائي",
          id: 6,
          modules: [
            this.primaire.domaine["arabic"],
            this.primaire.domaine["science"],
            this.primaire.domaine["langue"],
            this.primaire.domaine["nourir_sup"],
          ],
        },
      };
    },
  },
  components: {
    primaire_calcul,
    college_calcul,
  },
};
</script>

<style scoped >
</style>
