<template>
<div class="container">
    <button @click="copy()">zaznacz tabelę</button>
    <table id="tabela">
        <thead>
            <tr>
                <td>Kod</td>
                <td>Opis</td>
                <td>Cena</td>
                <!-- <td>Cena</td> -->
            </tr>
        </thead>
        <tbody>
            <tr v-for="elem in output">
                <td>
                    {{elem.kod}}

                </td>
                <td>{{elem.opis}}</td>
                <td>{{elem.cena}}</td>

                <!-- <td>{{elem.cena}}</td> -->
            </tr>
        </tbody>
    </table>

</div>
</template>

<script>
export default {
    data() {
//6066,6045,6066,6085,6075,6034
        return {
            output: [],
            profile: [
                    {kod:'6001',opis:'oscieznica 70/83 mm AD',cena:{biale:'2.4',bialeszara:'2.56', ZW:'3.47',O:'4.43' } },
                    {kod:'6002',opis:'oscieznica 70/83 mm MD',cena:{biale:'2.56',bialeszara:'2.56',ZW:'3.64',O:'4.59' } },
                    {kod:'6077',opis:'oscieznica 70/83 MM AD ',cena:{biale:'2.11',bialeszara:'2.11',ZW:'3.09',O:'4.12' } },
                    {kod:'6015',opis:'oscieznica 84/83 MM AD',cena:{biale:'3.72',bialeszara:'3.88',ZW:'4.27',O:'5.23' } },
                    {kod:'6016',opis:'oscieznica 84/83 MM MD',cena:{biale:'3.94',bialeszara:'4.1',ZW:'4.34',O:'5.35' } },
                    {kod:'6035',opis:'oscieznica 113/83 MM AD',cena:{biale:'6.69',bialeszara:'6.85',ZW:'9.45',O:'10.07' } },
                    {kod:'6036',opis:'oscieznica 113/83 MM MD',cena:{biale:'5.73',bialeszara:'5.89',ZW:'8.07',O:'9.71' } },
                    {kod:'6047',opis:'oscieznica 54/82,5 MM AD',cena:{biale:'3.5',bialeszara:'3.66',ZW:'6.67',O:'8.34' } },
                    {kod:'6048',opis:'oscieznica 54/82,5 MM MD',cena:{biale:'4.67',bialeszara:'4.83',ZW:'7',O:'8.68' } },
                    {kod:'6031',opis:'oscieznica 54/82,5 MM AD',cena:{biale:'4.96',bialeszara:'5.12',ZW:'7.35',O:'9.34' } },
                    {kod:'6032',opis:'oscieznica 54/82,5 MM MD mm',cena:{biale:'5.26',bialeszara:'5.42',ZW:'7.68',O:'9.68' } },
                    {kod:'6009',opis:'oscieznica 84/82,5MM',cena:{biale:'4.4',bialeszara:'4.4',ZW:'5.2',O:'6.1' } },
                    {kod:'6004',opis:'oscieznica 70/82,5MM mm',cena:{biale:'2.56',bialeszara:'2.56',ZW:'3.64',O:'4.59' } },
                    {kod:'6026',opis:'oscieznica 119 mm',cena:{biale:'4.31',bialeszara:'4.47',ZW:'5.55',O:'7.23' } },
                    {kod:'6030',opis:'oscieznica 105 mm',cena:{biale:'3.98',bialeszara:'4.14',ZW:'5.21',O:'6.89' } },
                    {kod:'6053',opis:'słupek 108/83 mm',cena:{biale:'5.58',bialeszara:'5.74',ZW:'8.01',O:'9.1' } },
                    {kod:'6054',opis:'słupek 108/83 mm',cena:{biale:'6.03',bialeszara:'6.19',ZW:'8.51',O:'9.61' } },
                    {kod:'6049',opis:'słupek 91/83 mm',cena:{biale:'3.42',bialeszara:'3.58',ZW:'4.38',O:'5.35' } },
                    {kod:'6050',opis:'słupek 91/83 mm',cena:{biale:'3.64',bialeszara:'3.8',ZW:'4.59',O:'5.55' } },
                    {kod:'6057',opis:'słupek 92/82,5 mm',cena:{biale:'3.64',bialeszara:'3.8',ZW:'4.59',O:'5.55' } },
                    {kod:'6058',opis:'słupek 108/82,5 MM',cena:{biale:'7.75',bialeszara:'7.91',ZW:'9.18',O:'10.53' } },
                    {kod:'6055',opis:'skrzydło 38/83  mm',cena:{biale:'2.75',bialeszara:'2.91',ZW:'3.64',O:'4.59' } },
                    {kod:'6023',opis:'skrzydło 82/83mm ',cena:{biale:'2.99',bialeszara:'3.15',ZW:'4.16',O:'5.23' } },
                    {kod:'6003',opis:'skrzydło 54/83 mm',cena:{biale:'2.64',bialeszara:'2.8',ZW:'3.64',O:'4.59' } },
                    {kod:'6017',opis:'skrzydło 108/83 mm',cena:{biale:'4.89',bialeszara:'4.89',ZW:'6.52',O:'7.48' } },
                    {kod:'6079',opis:'skrzydło 74/83 mm',cena:{biale:'2.37',bialeszara:'2.76',ZW:'3.35',O:'4.38' } },
                    {kod:'6061',opis:'skrzydło 89/82,5 mm',cena:{biale:'5.68',bialeszara:'5.84',ZW:'7.47',O:'8.54' } },
                    {kod:'6033',opis:'skrzydło 108/83 mm',cena:{biale:'5.13',bialeszara:'5.29',ZW:'7.16',O:'8.23' } },
                    {kod:'6025',opis:'skrzydło 120/83 mm',cena:{biale:'5.58',bialeszara:'5.74',ZW:'6.94',O:'8.23' } },
                    {kod:'6027',opis:'skrzydło 120/83 mm',cena:{biale:'5.58',bialeszara:'5.74',ZW:'7.16',O:'8.33' } },
                    {kod:'6065',opis:'skrzydło 132/83 mm',cena:{biale:'6.84',bialeszara:'7.00',ZW:'9.83',O:'11.85' } },
                    {kod:'6067',opis:'skrzydło 132/83 mm',cena:{biale:'13.47',bialeszara:'13.63',ZW:'18.65',O:'25.9' } },
                    // {kod:'6034',opis:'skrzydło 89 mm',cena:{biale:'8.33',bialeszara:0,ZW:'9.94',O:'11.75' } },
                    
            ],
            profile2:[
                    {kod:'6039',opis:'skrzydło 72 mm',cena:{biale:'5.87',kolor:'6.75'} },
            ],
            listwy:[
                    {kod:'6124',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6126',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6128',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6130',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6132',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6134',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6136',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6138',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6140',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6142',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6144',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6146',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6148',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6150',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},
                    {kod:'6152',opis:'Listwa',cena:{bialeszara:'0',bialeczarna:'0',kolor:'0'}},














                ]
            ,
            strony:[
                {kod:'Z',opis:'zewnatrz'},
                {kod:'W',opis:'wewnatrz'},
                {kod:'O',opis:'obustronnie'}
            ],

            uszczelki:[
                {kod:'S',opis:'usz.szara'},
                {kod:'C',opis:'usz.czarna'}

            ],
            grupy:[
                '0','6','10','20'
            ],
    
        }
    },
    methods:{
    selectElementContents(el) {
        var body = document.body,
            range, sel;
        if (document.createRange && window.getSelection) {
            range = document.createRange();
            sel = window.getSelection();
            sel.removeAllRanges();
            try {
                range.selectNodeContents(el);
                sel.addRange(range);
            } catch (e) {
                range.selectNode(el);
                sel.addRange(range);
            }
        } else if (body.createTextRange) {
            range = body.createTextRange();
            range.moveToElementText(el);
            range.select();
        }
    },
    generate(){
    for(let profil of this.profile){
           for(let strona of this.strony){
                    for(let grupa of this.grupy){
                    let kod = `PG_${profil.kod}_${strona.kod}_${grupa}`
                    let opis = `${profil.opis} ${profil.kod} ${strona.opis} usz.czarna ${grupa}%`
                    let cena = 0;
                    let cenabase = 0;
                    if(strona.kod == 'Z' || strona.kod == 'W'){
                        cenabase = profil.cena.ZW
                    }

                    if(strona.kod == 'O'){
                        cenabase = profil.cena.O
                    }
                    cena = Math.round(parseFloat(cenabase.replace(',', '.')) * (1 + parseFloat(grupa) / 100) * 100) / 100

                    this.output.push({kod:kod,opis:opis,cena:cena})
                    }
           }
       }
    },
    generate2(){
            let  strony = [
                {kod:'D',opis:'dekor'}
            ]

        for(let profil of this.profile2){
           for(let strona of strony){
                    for(let grupa of this.grupy){
                    let kod = `PG_${profil.kod}_${strona.kod}_${grupa}`
                    let opis = `${profil.opis} ${profil.kod} ${strona.opis} usz.czarna ${grupa}%`
                    let cenabase =  profil.cena.kolor;

                    let cena = Math.round(parseFloat(cenabase.replace(',', '.')) * (1 + parseFloat(grupa) / 100) * 100) / 100;
                   

                    this.output.push({kod:kod,opis:opis,cena:cena})
                    }
           }
       }

    },
    generateBiale(){
        // this.output.push({kod:'PG_8036_B_S',opis: 'szpros konstrukcyjny 8036 66 / 74 MM usz.szara ',cena:'4,73' })

        let uszczelki = [
            {kod:'C',opis:'usz.czarna'},
            {kod:'S',opis:'usz.szara' }
        ]

        for(let profil of this.profile){
            for (let uszczelka of uszczelki){
            
                    let kod = `PG_${profil.kod}_B`
                    if(uszczelka.kod == 'S'){
                        kod += '_S'
                    }

                    let opis = `${profil.opis} ${profil.kod} biale ${uszczelka.opis}`
                    let cena = `${profil.cena.biale}`

                    if(profil.kod == '6001'){
                        console.log(cena);
                    }


                    this.output.push({kod:kod,opis:opis,cena:cena})
                }
           }
    },
    generateListwy(){
        let kolory = [
            // {kod:'B',opis:'biale'},
            {kod:'D',opis:'dekor'}
        ]

        for(let listwa of this.listwy){
            for(let kolor of kolory){
                for(let grupa of this.grupy){
                let kod = `PG_${listwa.kod}_${kolor.kod}_${grupa}`
                let opis = `Listwa ${listwa.kod} ${kolor.opis} usz.czarna ${grupa} %`
                let cenabase =  listwa.cena.kolor;

                let cena = Math.round(parseFloat(cenabase.replace(',', '.')) * (1 + parseFloat(grupa) / 100) * 100) / 100;

                this.output.push({kod:kod,opis:opis,cena:cena})

                }
            }
        }

    },
    generateListwyBiale(){
         let kolory = [
            {kod:'B',opis:'biale'},
            // {kod:'D',opis:'decco'}
        ]

        let uszczelki = [
            {kod:'S',opis:'usz.szara'},
            {kod:'C',opis:'usz.czarna'},

        ]

        for(let listwa of this.listwy){
            for(let kolor of kolory){
                for(let uszczelka of uszczelki){
                let kod = `PG_${listwa.kod}_${kolor.kod}_${uszczelka.kod}`
                let opis = `Listwa ${listwa.kod} ${kolor.opis} ${uszczelka.opis}`
                let cena = 0;

                if(uszczelka.kod == 'S'){
                    cena = listwa.cena.bialeszara
                }

                if(uszczelka.kod == 'C'){
                    cena = listwa.cena.bialeczarna
                }

                this.output.push({kod:kod,opis:opis,cena:cena})

                }

            }
        }


    },
    copy() {
        this.selectElementContents(document.getElementById('tabela'));
    }

},
mounted() {
    let self = this;
      this.generateBiale();
    //   this.generate2();
    //   this.generate();
    //   this.generateListwyBiale();
    //   this.generateListwy();



    // this.generateBiale()
    console.log(parseFloat('2.25'));

}

}
</script>

<style scoped>
p {
    margin: 0px;
    padding: 0px;
    font-weight: bold;
}

td {
    border: 1px black solid;
}
</style>
