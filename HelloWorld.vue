<template>
  <v-container>
    <v-layout text-xs-center wrap >
      <v-flex xs12 sm6 xl4>
        <v-layout row wrap>
          <v-flex xs12>
            <v-text-field
              label="Serial"
              v-model="serial"
              outline
            ></v-text-field>
          </v-flex>
          <v-flex xs12>
            <v-text-field
              label="Password"
              v-model="passwd"
              outline
            ></v-text-field>
          </v-flex>
          <v-flex xs12>
            <v-btn color="success" @click="createLicense()">Generate</v-btn>
          </v-flex>

          <v-flex xs12 class="mt-3">
            <v-list>
              <v-list-tile v-for="license in licenses">
                <v-list-tile-content>
                  {{ license.type }}
                </v-list-tile-content>
                <v-list-tile-action class="headline">
                  {{ license.license }}
                </v-list-tile-action>
              </v-list-tile>              
            </v-list>
          </v-flex>
          

        </v-layout>      
      </v-flex>

    </v-layout>
  </v-container>
</template>

<script>

  import md5 from 'js-md5'

  export default {
    data: () => ({
      serial:'',
      licenses:[],
      passwd:'',
    }),

    methods:{
      createLicense(){  
        if(this.serial == '') return alert('Serial ?????')
        if(this.passwd != 'metal') return alert('Password ?????')

        var crypt = md5('0000000'+this.serial)

            let demo = '';let std = '';let pro = ''
            let std_t1 = '';let std_t2 = '';let std_t3 = '';let std_t4 = '';
            let pro_t1 = '';let pro_t2 = '';let pro_t3 = '';let pro_t4 = '';

            var VUE_APP_LIC_DEMO = '040576'
            var VUE_APP_LIC_STD = '270579'
            var VUE_APP_LIC_STD_T1 = '597626'
            var VUE_APP_LIC_STD_T2 = '813582'
            var VUE_APP_LIC_STD_T3 = '097562'
            var VUE_APP_LIC_STD_T4 = '495632'
            var VUE_APP_LIC_PRO = '815476' 
            var VUE_APP_LIC_PRO_T1 = '751282'
            var VUE_APP_LIC_PRO_T2 = '201358'
            var VUE_APP_LIC_PRO_T3 = '985362'
            var VUE_APP_LIC_PRO_T4 = '256871'            

            for (var i = 0; i <= 5; i++) {
              demo += crypt.charAt(VUE_APP_LIC_DEMO.split('')[i])
              std += crypt.charAt(VUE_APP_LIC_STD.split('')[i])
              pro += crypt.charAt(VUE_APP_LIC_PRO.split('')[i])
              std_t1 += crypt.charAt(VUE_APP_LIC_STD_T1.split('')[i])
              std_t2 += crypt.charAt(VUE_APP_LIC_STD_T2.split('')[i])
              std_t3 += crypt.charAt(VUE_APP_LIC_STD_T3.split('')[i])
              std_t4 += crypt.charAt(VUE_APP_LIC_STD_T4.split('')[i])
              pro_t1 += crypt.charAt(VUE_APP_LIC_PRO_T1.split('')[i])
              pro_t2 += crypt.charAt(VUE_APP_LIC_PRO_T2.split('')[i])
              pro_t3 += crypt.charAt(VUE_APP_LIC_PRO_T3.split('')[i])
              pro_t4 += crypt.charAt(VUE_APP_LIC_PRO_T4.split('')[i])
            }

        this.licenses = [ 
          { type: 'Pro', license: pro }, 
          { type: 'Pro T1', license: pro_t1 },
          { type: 'Pro T2', license: pro_t2 },
          { type: 'Pro T3', license: pro_t3 },
          { type: 'Pro T4', license: pro_t4 },
          { type: 'Standart', license: std }, 
          { type: 'Standart T1', license: std_t1 },
          { type: 'Standart T2', license: std_t2 },
          { type: 'Standart T3', license: std_t3 },
          { type: 'Standart T4', license: std_t4 },
          { type: 'Demo', license: demo },
        ]
      }
    }

  }
</script>

<style>

</style>