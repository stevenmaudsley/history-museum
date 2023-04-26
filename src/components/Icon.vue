<template>
  <div>
    <div id="star-five" />
  </div>
</template>

<script>
export default {
  name: "IconComponent",
};

// if using an icon library this would be a component that would take an icon as a prop
// this would make it reusable for each case needed
</script>

<style lang="scss" scoped>
#star-five {
  margin: 13px 0;
  position: relative;
  display: block;
  color: gold;
  width: 0px;
  height: 0px;
  border-right: 25px solid transparent;
  border-bottom: 18px solid gold;
  border-left: 25px solid transparent;
  transform: rotate(35deg);
}
#star-five:before {
  border-bottom: 20px solid gold;
  border-left: 8px solid transparent;
  border-right: 8px solid transparent;
  position: absolute;
  height: 0;
  width: 0;
  top: -11px;
  left: -16px;
  display: block;
  content: "";
  transform: rotate(-35deg);
}
#star-five:after {
  position: absolute;
  display: block;
  color: gold;
  top: 3px;
  left: -27px;
  width: 0px;
  height: 0px;
  border-right: 25px solid transparent;
  border-bottom: 18px solid gold;
  border-left: 25px solid transparent;
  transform: rotate(-70deg);
  content: "";
}
</style>
