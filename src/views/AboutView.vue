<template>
  <div class="about py-5">
    <primaire_calcul :primaire="primaire" :titel="titel"></primaire_calcul>
  </div>
</template>
<script>
import primaire_calcul from '@/components/primaire_calcul.vue'

 export default {
 name:"AboutView",
 data(){
    return{   
        titel:'primaire',
        primaire:[
            {name1:'السنة الاولى ابتدائي',name2:'السنة الثانية ابتدائي',name3:'السنة الثالثة ابتدائي',
            name4:'السنة الرابعة ابتدائي',name5:'السنة الخامسة ابتدائي',name6:'السنة السادسة ابتدائي',
             domaine:[
                 {arabic:{name:'مجال العربية',
                 matiere:['تواصل شفوي','الخط','القراءة','الانتاج الكتابي','معدل مجال اللغة العربية']}},
                {science:{name:'مجال العلوم',
                 matiere:['الرياضيات','الايقاظ العلمي','التربية التكنولوجية','معدل مجال العلوم']}},
                 {nourir_sup:{name:'مجال التنشئة',
                 matiere:['تربية اسلامية','تربية موسيقية','تربية تشكيلية','التاريخ','الجغرافيا','المدنية','تربية بدنية','معدل مجال التنشئة']}},
                {nourir:{name:'مجال التنشئة',
                 matiere:['تربية اسلامية','تربية موسيقية','تربية تشكيلية','تربية بدنية','معدل مجال التنشئة']}},
                  {francais:{name:'اللغة الفرنسية',
                 matiere:['Exp. Orale','Pro. Ecrite','Lecture','Moy. Français']}},
                   {francais:{name:'اللغات الاجنبية',
                 matiere:['Exp. Orale','Pro. Ecrite','Lecture',,'Anglais*','معدل اللغات الاجنبية']}},
            ]}
        ],

    }
 },
  components: {
     primaire_calcul
  },
 
 }
 
</script>

<style scoped >



</style>
