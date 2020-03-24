<template>
  <div>
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item v-for="item in listItems" :key="item.name" :active="item.isActive" link>
          <v-list-item-action>
            <v-icon>{{item.icon}}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{item.name}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="indigo" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>{{ pageName }}</v-toolbar-title>
    </v-app-bar>
  </div>
</template>

<script>
import ImagesView from "../views/ImagesView"
export default {
  name: "Menu",

  data: () => ({
    drawer: null,
    pageName:"Images View",
    // Here we add all menú items
    listItems: [
      {
        name: "Home",
        icon: "mdi-home",
        component:ImagesView,
        title:"title",
        isActive: true
      }
    ]
  })
};
</script>
