<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="*, 2*">
        <!-- Label with tap trigger to open drawer menu (RadSideDrawer) -->
        <Label
          :text="locales.navBarButtonText"
          @tap="$refs.drawer.nativeView.showDrawer()"
          col="0"
        />
        <!-- <Label
          :text="locales.navBarButtonText"
          col="0"
        /> -->
        <Label class="title" :text="locales.navBarTitle" col="1"/>
      </GridLayout>
    </ActionBar>

    <!-- Hamburguer menu -->
    <RadSideDrawer ref="drawer">
      <StackLayout ~drawerContent backgroundColor="#ffffff">
        <Label class="drawer-header" text="Drawer"/>
        <Label class="drawer-item" text="Item 1"/>
        <Label class="drawer-item" text="Item 2"/>
        <Label class="drawer-item" text="Item 3"/>
      </StackLayout>

      <GridLayout ~mainContent columns="*" rows="*">
        <Label class="message" :text="locales.mainPageText" col="0" row="0"/>
        <ListView class="list-group" for="task in tasks" @itemTap="onItemTap" style="height:1250px" separatorColor="transparent">
          <v-template>
            <FlexboxLayout flexDirection="column" class="list-group-item">
              <!-- <Image :src="country.imageSrc" class="thumb img-circle" /> -->
              <Label :text="task.name" class="list-group-item-heading" height="50" click/>
            </FlexboxLayout>
          </v-template>
      </GridLayout>
    </RadSideDrawer>
  </Page>
</template>

<script>
export default {
  methods: {
    onItemTap: function(item) {
      console.log('Item tapped: ', item);
    }
  },
  data() {
    return {
      locales: {
        navBarTitle: "Task Reminder",
        navBarButtonText: "MENU",
        mainPageText: "Further tasks"
      },
      tasks: [
        {
          name: "Task 1"
        },
        {
          name: "Task 2"
        },
        {
          name: "Task 3"
        },
        {
          name: "Task 4"
        },
        {
          name: "Task 5"
        }
      ]
    };
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}

.list-group-item-heading {
    color: black;
}

.list-group-item {
    text-align: center;
}

.title {
  text-align: left;
  padding-left: 16;
}

.message {
  vertical-align: top;
  margin-top: 15;
  text-align: center;
  font-size: 20;
  color: #333333;
}

.drawer-header {
  padding: 50 16 16 16;
  margin-bottom: 16;
  background-color: #53ba82;
  color: #ffffff;
  font-size: 24;
}

.drawer-item {
  padding: 8 16;
  color: #333333;
  font-size: 16;
}
</style>
