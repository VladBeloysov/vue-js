<template>
  <v-app>
    <v-navigation-drawer
        app
        temporary
        v-model="drawer"
    >
		<v-list>
			<v-list-item
				v-for="link of links"
				:key="link.title"
				:to="link.url"
			>
				<v-list-item-content>
					<v-list-item-title v-text="link.title"></v-list-item-title>
				</v-list-item-content>
			</v-list-item>
		</v-list>
    </v-navigation-drawer>
    <v-toolbar dark color="primary">
      <v-app-bar-nav-icon
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-toolbar-title>Ad application</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
		<v-btn
			v-for="link in links"
			:key="link.title"
			:to="link.url"
		>
			{{link.title}}
		</v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>
<script>
export default {
	data () {
		return {
			drawer: false,
			links: [
				{title: 'Login', icon: 'lock', url: '/login'},
				{title: 'Registration', icon: 'face', url: '/registration'},
				{title: 'Orders', icon: 'bookmark_border', url: '/orders'},
				{title: 'New ad', icon: 'note_add', url: '/new'},
				{title: 'My ads', icon: 'list', url: '/list'}
			]
		}
	}
}
</script>
<style scoped>
  .v-toolbar {
    max-height: 64px;
  }
</style>