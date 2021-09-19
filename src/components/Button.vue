<script lang="ts">
import { PropType, defineComponent, VueElement } from "vue";
import * as CSS from "csstype";
export type CSSProperties = CSS.Properties<string | number>;

export interface ButtonProps {
  className?: string;
  disabled?: boolean;
  endIcon?: VueElement;
  // tbd if this is the right type
  onClick?: () => void;
  startIcon?: VueElement;
  style?: CSSProperties;
  tabIndex?: number;
}
export default defineComponent({
  props: {
    product: {
      type: Object as PropType<ButtonProps>,
      required: false,
    },
  },

  setup(props) {
    const className = `wallet-adapter-button ${props.product?.className || ""}`;
    const justifyContent =
      props.product?.endIcon || props.product?.startIcon
        ? "space-between"
        : "center";
    return { justifyContent, className };
  },
});
</script>
<template>
  <button
    :class="className"
    :disabled="product?.disabled"
    :onclick="product?.onClick"
    :style="{ justifyContent, ...product?.style }"
    :tabindex="product?.tabIndex || 0"
  ></button>
</template>
