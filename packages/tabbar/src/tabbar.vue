<template>
  <div class="mint-tabbar" :class="{
      'is-fixed': fixed
    }">
    <slot></slot>
  </div>
</template>

<script>
/**
 * mt-tabbar
 * @module components/tabbar
 * @desc 底部 tab，依赖 tab-item
 * @param {boolean} [fixed=false] - 固定底部
 * @param {*} value - 返回 item component 传入的 id
 *
 * @example
 * <mt-tabbar v-model="selected">
 *   <mt-tab-item id="订单">
 *     <img slot="icon" src="http://placehold.it/100x100">
 *     <span slot="label">订单</span>
 *   </mt-tab-item>
 * </mt-tabbar>
 *
 * <mt-tabbar v-model="selected" fixed>
 *   <mt-tab-item :id="['传入数组', '也是可以的']">
 *     <img slot="icon" src="http://placehold.it/100x100">
 *     <span slot="label">订单</span>
 *   </mt-tab-item>
 * </mt-tabbar>
 */
export default {
  name: 'mt-tabbar',

  props: {
    fixed: Boolean,
    value: {}
  }
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";
  
  $tabbar-background-color: $default-background-color;
  $tabbar-tab-item-selected-background-color: $default-selected-background-color;
  $tabbar-tab-item-selected-color: $blur-color;

  @component-namespace mint {
    @component tabbar {
      background-image:linear-gradient(180deg, $blur-color, $blur-color 50%, transparent 50%);
      background-size: 100% 1px;
      background-repeat: no-repeat;
      background-position: top left;
      position: relative;
      background-color: rgba($tabbar-background-color, $default-background-opacity);
      display: flex;
      position: absolute * 0 0 0;
      text-align: center;

      @when fixed {
        position: fixed * 0 0 0;
        z-index: $z-index-normal;
      }

      > .mint-tab-item.is-selected {
        box-shadow: 0 0 1px $focus-color;
        background-color: rgba($tabbar-tab-item-selected-background-color, $default-background-opacity);
        color: $tabbar-tab-item-selected-color;
      }
    }
  }
</style>
