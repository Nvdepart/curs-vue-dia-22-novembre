<template>
   <v-container>
        <v-row>
                <v-col cols="12" md="6" style="background-color:aquamarine">
                        <v-text-field
                            label="Camp1"
                            placeholder="Escriu el text"
                            filled
                            type="Text"
                            v-model="camp1"
                        
                        
                        ></v-text-field>
                        <v-text-field
                        label="Camp2"
                            placeholder="Escriu el text"
                            filled
                            type="Text"
                            v-model="camp2"
                        
                        ></v-text-field>
                        <v-btn @click="mostrarElsTexts()">
                            mostrar a la consola
                        </v-btn>
                        <br><br>
                        <v-btn @click="borraElsTexts()">
                            Borrar Els texts
                        </v-btn>
                </v-col>
                <v-col cols="12" md="6" style="background-color:beige">
                        <div style="font-size:40px">{{camp1}}</div><br>
                        <div style="font-size:40px" v-text="camp2"></div><br>
                        <MostraCamps
                            :parametre1="camp1"
                            
                            :parametre2="camp2"
                        />
                        <br>
                </v-col>
        </v-row>
   </v-container>
</template>


<script>

function emplenarElsTexts(){
    console.log("....")
}
export default{

        data(){
            return {
                camp1:"",
                camp2:""
            }

        },
        methods:{
            //ES6
            mostrarElsTexts(){
                    console.log("El camp 1 es ",this.camp1)
                    console.log("El camp 2 es ",this.camp2)
            },

            //ES5
            borraElsTexts(){
                console.log("Hem borrat els camps")
                this.camp1=""
                this.camp2=""
            },
            omple:emplenarElsTexts
        }
        


}


</script>