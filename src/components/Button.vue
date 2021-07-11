<template>
  <a @click="onClick">{{ text }}</a>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
  },
  methods: {
    onClick() {
      this.$emit("btn-click");
    },
  },
};
</script>

<style scoped>
a {
  display: grid;
  place-items: center;
  width: 150px;
  font-size: 20px;
  font-weight: bolder;
  text-decoration: none;
  padding: 10px 20px;
  color: deeppink;
  position: relative;
  transition: all 0.5s;
  overflow: hidden;
  cursor: pointer;
  user-select: none;
}
a:before {
  content: "";
  position: absolute;
  bottom: -100%;
  left: 0;
  width: 100%;
  height: 100%;
  background: deeppink;
  border: 2px solid deeppink;
  z-index: -1;
  transition: all 0.5s;
}
a:hover:before {
  bottom: 0;
}
a:active:before {
  background: rgb(116, 8, 65);
}

a:hover {
  color: white !important;
}
</style>
