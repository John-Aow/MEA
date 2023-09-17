<template>
    <v-card>
      <v-layout>
        <!-- <v-system-bar color="deep-purple darken-3"></v-system-bar> -->
  
        <v-app-bar
          class="bg-mea"
          prominent
        >
          <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer" color="white"></v-app-bar-nav-icon>

          <v-toolbar-title >
            <v-container fill-height >
              <v-row>
                 <v-col>
                  <v-img :width="200" alt="MEA logo" :src="require('../assets/Metropolitan-Electricity-Authority-logo-w.png')">
                  </v-img>
                </v-col>
                <v-col><p class="font-weight-medium"  style="color:white">| Mea Cloud Computing</p></v-col>
              </v-row>
            </v-container>
         
          </v-toolbar-title>
          <v-spacer></v-spacer>
          <v-icon icon="mdi-account" color="white" ></v-icon>
          <p class="font-weight-medium mx-2" style="color:white">Panumas Panyacharoenchai</p>
        </v-app-bar>
  
        <v-navigation-drawer
          v-model="drawer"
          location="left"
          temporary
        >
        <v-list >
          <v-list-item
            v-for="item in items"
            :key="item.value"
            :to="item.link"
            class="color-mea text-left"
          >
          <template v-slot:prepend>
            <v-icon :icon="item.icon"></v-icon>
          </template>
          <v-list-item-title v-text="item.title"></v-list-item-title>
        </v-list-item>
        </v-list>
        </v-navigation-drawer>
  
        <v-main style="min-height: 500px;">
            <router-view/>   
        </v-main>
      </v-layout>
    </v-card>
  </template>
  <script>
    export default {
      data: () => ({
        drawer: false,
        group: null,
        items: [
          {
            title: 'Home',
            value: 'home',
            link: '/',
            icon: 'mdi-home'
          }, 
          {
            title: 'History',
            value: 'history',
            link: '/history',
            icon: 'mdi-clipboard-text-clock-outline'
          }, 
          {
            title: 'Manage Admin',
            value: 'manage_admin',
            link: '/manage_admin',
            icon: 'mdi-account-group'
          },
          {
            title: 'Login',
            value: 'login',
            link: '/login',
            icon: 'mdi-account-key'
          },
        ]
      }),
  
      watch: {
        group () {
          this.drawer = false
        },
      },
    }
  </script>
