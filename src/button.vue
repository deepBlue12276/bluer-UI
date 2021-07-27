<template>
  <button class="b-button" :class="{[`b-button-${type}`]: true,[`icon-${iconPosition}`]: true}"> 
    <svg class="icon" v-if="icon">
      <use :xlink:href="`#i${icon}`"></use>
    </svg>
    <div class="content">
      <slot></slot>
    </div>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    type:{
      type:String,
      default:'primary'
    },
    icon: {
      type: String,
      default: "",
    },
    iconPosition: {
      type: String,
    },
  },
  computed: {
    isRight() {
      if (this.right) return true;
      else return false;
    },
  },
};
</script>

<style lang='scss'>
.b-button-primary {
  $b-button-main-color: #409eff!global;
}
.b-button-success {
  $b-button-main-color: #67c23a!global;
}
.b-button-info {
  $b-button-main-color: #909399!global;
}
.b-button-warning {
  $b-button-main-color: #e6a23c!global;
}
.b-button-danger {
  $b-button-main-color: #f56c6c!global;
}
.b-button {
  height: 32px;
  font-size: 14px;
  padding: 0 1em;
  border-radius: 4px;
  border: 1px solid $b-button-main-color;
  background: $b-button-main-color;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  color:#fff;
  vertical-align: middle;
  &:hover {
    border-color:lighten($b-button-main-color, 10%);
    color: lighten(#fff, 10%);
    background-color:lighten($b-button-main-color, 10%);
    box-shadow: 0 0 8px 0 rgb(232 237 250 / 60%), 0 2px 4px 0 rgb(232 237 250 / 50%)
  }
  &:active {
    border-color: darken($b-button-main-color, 10%);
    background-color:  darken($b-button-main-color, 10%);
    color: darken(#fff, 10%);
  }
  &:focus {
    outline: none;
  }
  .icon {
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }
  > .icon {
    order: 1;
    margin-right: 0.3em;
  }
  > .content {
    order: 2;
  }
  &.icon-right {
    > .icon {
      order: 2;
      margin-left: 0.3em;
    }
    > .content {
      order: 1;
    }
  }
}

</style>