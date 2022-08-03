<template>
  <div class="about py-5">
    <primaire_calcul
      :primaire="primaire"
      :niveau="niveau"
      :titel="titel"
    ></primaire_calcul>
  </div>
</template>
<script>
import primaire_calcul from "@/components/primaire_calcul.vue";

export default {
  mounted() {},
  name: "AboutView",
  data() {
    return {
      titel: "المرحلة الابتدائية",
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
    };
  },
  computed: {
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
  },
};
</script>

<style scoped >
</style>
