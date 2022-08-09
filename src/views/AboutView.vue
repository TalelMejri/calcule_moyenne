<template>
  <div class="about py-5">
    <div class="row">
      <primaire_calcul
        class="col-md-4"
        :primaire="primaire"
        :niveau="niveau"
        :titel="titel_primaire"
      ></primaire_calcul>
      <college_calcul
        class="col-md-4"
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
              { name: "الفرض التأليفي في الانشاء", coef: 1 },
              { name: "الفرض التأليفي في دراسة النص", coef: 1 },
              { name: "معدل العربية", coef: 0 },
            ],
          },
          francais: {
            name: "مادة الفرنسية",
            coef: 4,
            matiere: [
              { name: "فرض المراقبة عدد 1 في الفرنسية ", coef: 1 },
              { name: "فرض المراقبة عدد 2 في الفرنسية ", coef: 1 },
              { name: " الفرض التأليفي في الفرنسية ", coef: 1 },
              { name: "الشفوي في مادة الفرنسية", coef: 1 },
              { name: "معدل الفرنسية", coef: 0 },
            ],
          },
          anglais: {
            name: "مادة الانجليزية",
            coef: 1.5,
            matiere: [
              "فرض المراقبة عدد 1 مادة الانجليزية",
              "فرض المراقبة عدد 2 مادة الانجليزية",
              " الفرض التأليفي مادة الانجليزية",
              "الشفوي مادة الانجليزية",
              "معدل الانجليزية",
            ],
          },
          math: {
            name: "مادة الرياضيات",
            coef: 3,
            matiere: [
              "فرض المراقبة عدد 1 مادة الرياضيات",
              "فرض المراقبة عدد 2 مادة الرياضيات",
              " الفرض التأليفي مادة الرياضيات",
              "معدل الرياضيات",
            ],
          },
          physqiue: {
            name: "مادة العلوم الفيزيائية",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 مادة العلوم الفيزيائية",
              "الفرض التأليفي مادة العلوم الفيزيائية",
              "معدل العلوم الفيزيائية",
            ],
          },
          science: {
            name: "مادة العلوم الطبيعية",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 مادة العلوم الطبيعية",
              "الفرض التأليفي مادة العلوم الطبيعية",
              "الشفوي / الأشغال التطبيقية",
              "معدل العلوم الطبيعية",
            ],
          },
          history: {
            name: "مادة التاريخ",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 مادة التاريخ",
              "الفرض التأليفي مادة التاريخ",
              "الشفوي مادة التاريخ",
              "معدل التاريخ",
            ],
          },
          geo: {
            name: "مادة الجغرافيا",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 مادة الجغرافيا",
              "الفرض التأليفي مادة الجغرافيا",
              "الشفوي مادة الجغرافيا",
              "معدل الجغرافيا",
            ],
          },
          technique: {
            name: "مادة التربية التكنولوجية",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 مادة التربية التكنولوجية",
              "الفرض التأليفي مادة التربية التكنولوجية",
              "الشفوي مادة التربية التكنولوجية",
              "معدل التكنولوجية",
            ],
          },
          islamic: {
            name: "مادة التربية الاسلامية",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 الاسلامية",
              "الفرض التأليفي الاسلامية",
              "الشفوي الاسلامية",
              " معدل التربية الاسلامية",
            ],
          },
          civil: {
            name: "مادة التربية المدنية",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 المدنية",
              "الفرض التأليفي المدنية",
              "الشفوي المدنية",
              " معدل التربية المدنية",
            ],
          },
          info: {
            name: "مادة الإعلامية",
            coef: 1,
            matiere: [
              "فرض المراقبة عدد 1 الإعلامية",
              "الفرض التأليفي الإعلامية",
              " معدل الإعلامية",
            ],
          },
          theatre: {
            name: "مادة المسرح",
            coef: 1,
            matiere: [
              "فرض المراقبة عددالمسرح  1",
              "الفرض التأليفي المسرح",
              "الشفوي المسرح",
              " معدل  المسرح",
            ],
          },
          sport: {
            name: " مادة التربية البدنية",
            coef: 1,
            matiere: [
              "فرض المراقبة البدنية",
              "الفرض التأليفي البدنية",
              " معدل التربية البدنية",
            ],
          },
          dessin: {
            name: " مادة التربية التشكيلية  ",
            coef: 1,
            matiere: [
              "فرض المراقبة التشكيلية",
              "الفرض التأليفي التشكيلية",
              " معدل التربية التشكيلية",
            ],
          },
          music: {
            name: "مادة التربية الموسيقية ",
            coef: 1,
            matiere: [
              "فرض المراقبة  الموسيقية",
              "الفرض التأليفي الموسيقية",
              "الشفوي الموسيقية",
              " معدل التربية الموسيقية",
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
            /*this.college.domaine["history"],
            this.college.domaine["geo"],
            this.college.domaine["technique"],
            this.college.domaine["islamic"],
            this.college.domaine["civil"],
            this.college.domaine["info"],
            this.college.domaine["theatre"],
            this.college.domaine["sport"],
            this.college.domaine["dessin"],
            this.college.domaine["music"],*/
          ],
        },
        "السنة الثامنة أساسي  ": {
          name: "  السنة الثامنة أساسي",
          id: 2,
          modules: [
            this.college.domaine["arabic"],
            this.college.domaine["francais"],
            /* this.college.domaine["anglais"],
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
            this.college.domaine["music"],*/
          ],
        },
        "  السنة التاسعة أساسي": {
          name: "  السنة التاسعة أساسي",
          id: 3,
          modules: [
            this.college.domaine["arabic"],
            this.college.domaine["francais"],
            /* this.college.domaine["anglais"],
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
            this.college.domaine["music"],*/
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
