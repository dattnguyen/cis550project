<template>
    <component :is="tag"
               :type="tag === 'button' ? nativeType: ''"
               @click="handleClick"
               class="btn-header-custom"
               :class="classes"
               v-b-tooltip.hover.bottom
               >
    <span class="btn-header-icon-custom" v-if="$slots.icon || icon && $slots.default">
      <slot name="icon">
        <i :class="icon"></i>
      </slot>
    </span>
        <i v-if="!$slots.default" :class="icon"></i>
        <slot v-if="!$slots.icon && !icon"></slot>
    </component>
</template>
<script>
export default {
  name: "button-header",
  props: {
    tag: {
      type: String,
      default: "button",
      description: "Button tag (default -> button)"
    },
    type: {
      type: String,
      default: "default",
      description: "Button type (e,g primary, danger etc)"
    },
    size: {
      type: String,
      default: "",
      description: "Button size lg|sm"
    },
    textColor: {
      type: String,
      default: "",
      description: "Button text color (e.g primary, danger etc)"
    },
    nativeType: {
      type: String,
      default: "button",
      description: "Button native type (e.g submit,button etc)"
    },
    icon: {
      default: "",
      description: "Button icon"
    },
    text: {
      type: String,
      default: "",
      description: "Button text in case not provided via default slot"
    },
    outline: {
      type: Boolean,
      default: false,
      description: "Whether button style is outline"
    },
    rounded: {
      type: Boolean,
      default: false,
      description: "Whether button style is rounded"
    },
    iconOnly: {
      type: Boolean,
      default: false,
      description: "Whether button contains only an icon"
    },
    block: {
      type: Boolean,
      default: false,
      description: "Whether button is of block type"
    }
  },
  computed: {
    classes() {
      let btnClasses = [
        { "btn-block": this.block },
        { "rounded-circle": this.rounded },
        { "btn-icon-only": this.iconOnly },
        { [`text-${this.textColor}`]: this.textColor },
        { "btn-icon": this.icon || this.$slots.icon },
        this.type && !this.outline ? `btn-${this.type}` : "",
        this.outline ? `btn-outline-${this.type}` : ""
      ];
      if (this.size) {
        btnClasses.push(`btn-${this.size}`);
      }
      return btnClasses;
    }
  },
  methods: {
    handleClick(evt) {
      this.$emit("click", evt);
    }
  }
};
</script>
<style>
</style>
