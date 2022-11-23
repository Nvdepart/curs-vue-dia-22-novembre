<template>
    <v-container>
            <v-row>
                <V-col cols="12" md="4" offset-md="4" style="background-color:bisque;margin-top:10vh">
                    <v-text-field 
                    label="usuari"
                    v-model="usuari"
                    ></v-text-field>
                    <v-text-field
                    label="password"
                    type="password"
                    v-model="contrasenya"
                    ></v-text-field>
                    <div v-if="siHiHaMajusculesMinuscules" style="color:green">Molt be, tens majuscules i miniscules</div>
                    <div v-else style="color:red">Ep, cal posar alguna majuscula i miniscula</div>
                    <div v-if="siHiHaMesDe6Caracters" style="color:green">Molt be, tens 6 caracters</div>
                    <div v-else style="color:red">Cal posar minim 6 caracter</div>
                    <div v-if="siHiHa1CaracterEspecial" style="color:green">Molt be, tens algun caracter especial</div>
                    <div v-else style="color:red">Cal posar alguna caracter especial</div>
                           
                                <v-btn v-if="
                                siHiHaMajusculesMinuscules
                                && siHiHaMesDe6Caracters
                                && siHiHa1CaracterEspecial"
                                >Login</v-btn>
                                <v-btn v-if="totCorecte">
                                    Netejar
                                </v-btn>
          
                </V-col>
               
            </v-row>
    </v-container>
</template>

<script>
    export default{
            data(){
                return {
                    usuari:"",
                    contrasenya:""
                }

            },
           methods:{
                conteLletres(str) {
                return /[a-zA-Z]/.test(str)
            },
            conteCaracter(crt){
                return /[?]/.test(crt)
            }
        },
            computed:{
                siHiHaMajusculesMinuscules(){
                    let textOriginal = this.contrasenya
                    let hiHaMajuscules = false
                    let hiHaMinuscules = false
                    let HihaCacterEspecial = false
                    for(var i = 0; i < textOriginal.length;i++){
                        let caracter = textOriginal[i]
                        
                        if(this.conteLletres(caracter)){
                           
                            if(caracter.toUpperCase() === caracter){
                               // Mirem si hi ha majuscules
                                hiHaMajuscules = true
                            }else{
                                // Mirem si hi ha maniscules
                                hiHaMinuscules = true
                            }
                        }
                    }
                    return hiHaMajuscules && hiHaMinuscules
                },
            
                siHiHaMesDe6Caracters(){
                    // fem algo i tornam true si hi ha mes de 6 caracters
                    if(this.contrasenya 
                    && typeof(this.contrasenya)=="string"
                    && this.contrasenya.length >= 6){
                        return true
                    }
                },

                siHiHa1CaracterEspecial(){
                    console.log(this.contrasenya)
                    let textOriginal = this.contrasenya
                    
                    let hihaCacterEspecial = false
                    // per cada lletra de la cadena de text
                    for(var i = 0; i < textOriginal.length;i++){
                        let caracter = textOriginal[i]
                        // Mirem si la lletra es un simbol déxclamacio
                        
                        if(caracter=="!"){
                            // Mirem si hi ha un caracter Especial
                            hihaCacterEspecial = true
                            }
                        }
                        return hihaCacterEspecial
                },
                totCorecte(){
                    return this.siHiHaMajusculesMinuscules
                        && this.siHiHaMesDe6Caracters
                        && this.siHiHa1CaracterEspecial
                }
        }
    }

</script>