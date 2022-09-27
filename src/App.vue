<template>
  <input-component
    :imagePath="imagePath"
    :itemList="itemList"
    @itemSelected="selectItem"
  />
</template>
<script>
import inputComponent from "./components/inputComponent.vue";
export default {
  name: "App",
  components: { inputComponent },
  data() {
    return {
      imagePath:
        "https://cdn2.iconfinder.com/data/icons/ios-7-icons/50/search-512.png",
      itemList: [
        {
          icon: "https://www.iconpacks.net/icons/1/free-user-icon-244-thumb.png",
          name: "talent",
          desc: "Hire professionals and agencies",
        },
        {
          icon: "https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Noun_Project_process_icon_2519390.svg/1024px-Noun_Project_process_icon_2519390.svg.png",
          name: "Projects",
          desc: "Buy ready-to-start services",
        },
        {
          icon: "https://cdn2.iconfinder.com/data/icons/ios-7-icons/50/search-512.png",
          name: "all",
          desc: "Search talen and projects",
        },
      ],
    };
  },
  methods: {
    selectItem(e) {
      console.log(e);
    },
  },
};
</script>
