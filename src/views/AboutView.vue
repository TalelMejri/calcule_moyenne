<template>
  <div class="about py-5">
    <primaire_calcul :primaire="primaire" :niveau="niveau" :titel="titel"></primaire_calcul>
  </div>
</template>
<script>
import primaire_calcul from '@/components/primaire_calcul.vue'

 export default {
 name:"AboutView",
 data(){
    return{   
        titel:'المرحلة الابتدائية',
         niveau:
                ['السنة الاولى ابتدائي'  ,
                 'السنة الثانية ابتدائي',
                 'السنة الثالثة ابتدائي',
                 'السنة الرابعة ابتدائي',
                 'السنة الخامسة ابتدائي',
                 'السنة السادسة ابتدائي'
                ],

        primaire:[
            {
             domaine:[
                 {arabic:{name:'مجال العربية',
                          matiere:['تواصل شفوي','الخط','القراءة','الانتاج الكتابي','معدل مجال اللغة العربية']
                          }
                 },
                 {science:{name:'مجال العلوم',
                           matiere:['الرياضيات','الايقاظ العلمي','التربية التكنولوجية','معدل مجال العلوم']
                          }
                },
                 {nourir_sup:{name:'مجال التنشئة',
                             matiere:['تربية اسلامية','تربية موسيقية','تربية تشكيلية','التاريخ','الجغرافيا','المدنية','تربية بدنية','معدل مجال التنشئة']
                             }
                },
                {nourir:{name:'مجال التنشئة',
                         matiere:['تربية اسلامية','تربية موسيقية','تربية تشكيلية','تربية بدنية','معدل مجال التنشئة']
                         }
                },
                {francais:{name:'اللغة الفرنسية',
                           matiere:['Exp. Orale','Pro. Ecrite','Lecture','Moy. Français']
                           }
                },
                {langue:{name:'اللغات الاجنبية',
                         matiere:['Exp. Orale','Pro. Ecrite','Lecture',,'Anglais*','معدل اللغات الاجنبية']
                         }
                },
            ]
         }
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
