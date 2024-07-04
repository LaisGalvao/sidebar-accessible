<template>
  <div class="hello">
    <button @click="openMenu('side-menu')">
      <img src="../assets/logo.png" alt="" width="70" />
    </button>
    <ul id="side-menu" class="side" role="menubar">
      <li
        role="menuitem"
        aria-haspopup="true"
        tabindex="0"
        @click="openSubmenu('sub1')"
        @keypress.13="openSubmenu('sub1')"
      >
        <span>Menu 1</span>
        <ul v-for="(item, index) in items" id="sub1" class="side" role="menu" :key="index">
          <li :id="index" role="menuitem" aria-haspopup="true" tabindex="0">{{ item.name + '-' + index }}</li>
          <!-- <li role="menuitem" aria-haspopup="true" tabindex="0">Item 2</li>
          <li role="menuitem" aria-haspopup="true" tabindex="0">Item 3</li>
          <li role="menuitem" aria-haspopup="true" tabindex="0">Item 4</li>
          <li role="menuitem" aria-haspopup="true" tabindex="0">Item 5</li> -->
        </ul>
      </li>

      <li
        role="menuitem"
        aria-haspopup="true"
        tabindex="0"
        @click="openSubmenu('sub2')"
        @keypress.13="openSubmenu('sub2')"
      >
        <span>Menu 2</span>
        <ul v-for="(item, index) in items2" id="sub2" class="side" role="menu" :key="index">
          <li :id="index">{{ item.name + '-' + index }}</li>
          <!-- <li>Item 2</li>
          <li>Item 3</li> -->
        </ul>
      </li>

      <li
        role="menuitem"
        aria-haspopup="true"
        tabindex="0"
        @click="openSubmenu('sub3')"
        @keypress.13="openSubmenu('sub3')"
      >
        <span>Menu 3</span>
        <ul id="sub3" class="side" role="menu">
          <li>Item 1</li>
          <li>Item 2</li>
        </ul>
      </li>
      <li>Menu 4</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      sub: false,
      main: false,
      items: [
        { id: 1, name: 'Item 1' },
        { id: 2, name: 'Item 1' },
        { id: 3, name: 'Item 1' },
        { id: 4, name: 'Item 1' },
        { id: 5, name: 'Item 1' },
      ],
      items2: [
        { id: 1, name: 'Item 1' },
        { id: 2, name: 'Item 1' },
        { id: 3, name: 'Item 1' },
        { id: 4, name: 'Item 1' },
        { id: 5, name: 'Item 1' },
      ]
    };
  },
  methods: {
    openSubmenu(submenu, display) {
      var id_ = document.getElementById(submenu);
      display = id_.style.display == "block";

      var menus = document.querySelectorAll("[id^=sub]");
      for (var i = 0; i < menus.length; i++) {
        menus[i].style.display = "none";
        this.sub = false;
      }

      if (display) {
        id_.style.display = "none";
        this.sub = false;
      } else {
        id_.style.display = "flex";
        id_.style.flexDirection = "column";
        id_.style.alignItems = "center";
        this.sub = true;
      }
    },

    openMenu(menu) {
      menu = document.getElementById("side-menu");
      /*  var windowWidth = window.innerWidth; */
      if (this.main) {
        this.main = false;
      } else {
        this.main = true;
      }
      /* if (windowWidth < 1025) { */

      if (this.main == true) {
        menu.style.display = "flex";
        menu.style.flexDirection = "column";
        menu.style.alignItems = "center";
      } else {
        menu.style.display = "none";
      }
      /* } */
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

#sub1,
#sub2,
#sub3 {
  display: none;
  width: min-content;
}
.side {
  display: none;
  width: 10vw;
}

.hello {
  display: flex;
  left: 0px !important;
  position: fixed;
  top: 0;
  flex-direction: column;
  width: 10vw;
  height: 100%;
  background-color: #42b983;
  z-index: 1;
  align-content: center;
  align-items: center;
}
</style>
