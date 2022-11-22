<template>
    <v-container>
        <v-row>
            <v-col cols="12" md="6" style="background-color:aqua">
    <h1 style=" color:blue">Manipular arrays Temperatures</h1>
                <v-text-field
                    label="Temperatura"
                    placeholder="Escriu la temperatura"
                    filled
                    type="Number"
                    v-model="temperatura"
                ></v-text-field>
                    <v-btn @click="afegir()">Afegir</v-btn><br>
                    <v-btn @click="netejar()">Netejar</v-btn><br>
                    <v-btn @click="borraUltimElement()">Borrar el ultim Element</v-btn><br>
                    <v-btn @click="temperaturesAleatories()">Aleatori</v-btn>
            </v-col>
            <v-col cols="12" md="6" style="background-color:blue">
            <h1 style=" color:aliceblue">Resultat:
                 <br>
                 Mostres:{{tamanyArray}}
                 <br>
                 Mostres superiors a 50 graus:{{mesDe50}}
                 <br>
                <v-sparkline 
                :value="temperatures"
                :gradient="elMeuArrayDeColrs"  
                ></v-sparkline> 
      
                <div v-for="element in temperatures">
                    La temperatura es {{element}}
                </div>
            </h1>
            </v-col>
        </v-row>
    </v-container>
</template>
<script>
    export default{
               mounted(){
                // inicialitzem l'array de temperatures
                this.temperaturesAleatories()
               },
                data(){
                    return {
                        elMeuArrayDeColrs:['red','green','yellow'],
                        temperatura:0,
                        temperatures:[33,24,41,23,44,11,23]
                    }
                },
                methods:{
                    afegir(){
                        console.log("Afegir...")
                        console.log("temperatura:", this.temperatura)
                        const tmp = parseFloat(this.temperatura)
                        console.log("El tipus de temperatura es ",typeof(tmp))
                        this.temperatures.push(tmp)
                    }, 
                    netejar(){
                        console.log("netejan ..")
                        this.temperatures=[]
                        console.log(this.temperatures)
                    },

                    borraUltimElement(){
                        this.temperatures.pop()
                    },
                    temperaturesAleatories(){
                        console.log("fent temperatures aleatories")
                        // Creem un array buid
                        let nouArray = []
                        // repetim 100 vagades

                        for( let i=0; i<100; i++){
                            // afegim valors
                            let valorAleatoriDecimals = Math.random()*100
                            let valorAleatoriEnter = this.processarEnter(valorAleatoriDecimals)
                            nouArray.push(valorAleatoriEnter)
                        }
                        // Assignem al array del component
                        this.temperatures = nouArray
                    },
                    processarEnter(val){
                        return parseInt(val)
                    }
                },
                computed:{
                    tamanyArray(){
                        return this.temperatures.length
                    },
                    mesDe50(){
                        let mostresDeMesDe50Graus =0
                        this.temperatures.forEach((temperatura)=>{
                            if(temperatura>50){
                                mostresDeMesDe50Graus++
                            }

                        })
                        return mostresDeMesDe50Graus
                    }
                },
                watch:{
                    temperatura(newValue, oldValue){
                        if(newValue>55){
                            alert("ALERTA")
                        }
                    }
                }
        }

        </script>