<template>
    <v-container>
        <v-row>
            <v-col cols="12" md="6" style="background-color:aquamarine">
                    <v-textarea
                        label="Tasca"
                        placeholder="Escriu la tasca"
                        outlined
                        v-model="laNovaTasca"
                    
                    ></v-textarea>
                    <v-btn @click="afegirTasca()" color="blue" :disabled="!tincText">Afegir tasca</v-btn><br>
            </v-col>
            <v-col cols="12" sm="6">
                    <h1>Lista de tareas a hacer</h1>
                    
                    
                    <div style="background-color:aquamarine; margin:20px" v-for="tasca in tasques">{{tasca.text}}</div>

                    <v-row class="tasca" v-for="tasca in tasques">
                        <v-col cols="8">
                           <h2>{{tasca.text}}</h2>
                        </v-col>
                        <v-col cols="4">
                            <v-checkbox 
                                v-model="tasca.feta">
                            </v-checkbox>
                        </v-col>
                    </v-row>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
        export default{

                methods:{
                    afegirTasca(){
                        if(this.laNovaTasca.length<=0){
                            alert("El camp tasca no pot estar buid")
                            return
                        }
                        console.log("Afegint tasca ...")
                        var tasca={}
                        tasca.text=this.laNovaTasca
                        tasca.feta=false
                        this.tasques.push(tasca)
                        this.laNovaTasca=""
                    }
                },
                data(){
                    return {
                        laNovaTasca:"",
                        tasques:[
                            {
                                text:"Fer el llit",
                                feta: true
                            },
                            {
                                text:"Fer els deures",
                                feta:false
                            },
                            {
                                text:"Anar a comprar",
                                feta:true
                            }
                        ]
                }
                   
        },
        computed:{
            tincText(){
                if(this.laNovaTasca.length <=0){
                    return false
                } else {
                    return true
                }
            }
        }

    }

</script>

<style>
        .tasca{
            background-color: bisque;
            margin-bottom: 10px;
        } 
</style>
            
                
