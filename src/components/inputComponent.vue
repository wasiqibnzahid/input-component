<template>
  <div class="input-container" >
    <div class="input-field-container" :class="showMenu ? 'active' : ''">
      <input :class="showMenu ? 'active' : ''" type="text" />
      <img class="input-img" :src="imagePath" alt="" />
    </div>
    <div class="btn-container" :class="showMenu ? 'active' : ''">
      <button
        :class="showMenu ? 'active' : ''"
        ref="menuButton"
        @click="showMenu = !showMenu"
      >
        {{ title }}
        <img src="../assets/down-arrow-svgrepo-com.svg" />
      </button>
    </div>
    <div ref="menu" v-show="showMenu" class="menu">
      <div
        v-for="(item, index) in itemList"
        :key="index"
        @click="selectItem(item)"
        class="menuItem"
      >
        <div>
          <div class="img-container"><img :src="item.icon" alt="" /></div>
        </div>
        <div class="text-box">
          <h5>{{ item.name }}</h5>
          <p>{{ item.desc }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {imagePath: String, itemList: Array},
  mounted() {
    document.addEventListener("click", (e) => {
      this.handleClick(e);
    });
  },
  unmounted() {
    document.removeEventListener("click", (e) => {
      this.handleClick(e);
    });
  },
  data() {
    return {
      showMenu: false,
      
      title: "Talent",
    };
  },
  methods: {
    handleClick(e) {
      if (
        e.target != this.$refs.menu &&
        !this.$refs.menu.contains(e.target) &&
        e.target != this.$refs.menuButton &&
        !this.$refs.menuButton.contains(e.target)
      ) {
        this.showMenu = false;
      }
    },
    selectItem(item) {
      this.title = item.name;
      this.$emit("itemSelected", item);
      this.showMenu = false;
    },
  },
};
</script>
