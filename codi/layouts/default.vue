<template>
  <v-app>
    <v-container>
        <v-row>
          <v-col style="background-color:blue">
            <v-btn Clar to="/">Inici</v-btn>
            <v-btn Clar to="/tasques">Tasques</v-btn>
            <v-btn dark to="/testmvc">MVC</v-btn>
            <v-btn dark to="/loginusuari">Login Usuari</v-btn>
          </v-col>
        </v-row>
    </v-container>
    <v-main>
      <nuxt/>
    </v-main>
  </v-app>
</template>