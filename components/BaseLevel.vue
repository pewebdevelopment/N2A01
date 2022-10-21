<script>
// import { defineComponent } from "vue";
import {  defineComponent } from 'vue'
// import { useSlots } from 'vue';

export default defineComponent({
  name: 'BaseLevel',
  props: {
    mobile: Boolean,
    type: {
      type: String,
      default: 'justify-between',
    },
  },

  setup(props) {
    const parentClass = [props.type, 'items-center']

    const parentMobileClass = ['flex']

    const parentBaseClass = ['block', 'md:flex']

    const childBaseClass = ['flex', 'items-center', 'justify-center']
    return {
      parentBaseClass,
      parentClass,
      parentMobileClass,
      childBaseClass,
    }
  },
  // render() {

  // return h(
  //   'div',
  //   {
  //     class: parentClass.concat(
  //       this.mobile ? parentMobileClass : parentBaseClass
  //     ),
  //   },
  //   (element, index) => {
  //     const childClass = !this.mobile
  //       ? childBaseClass.concat(['mb-6', 'md:mb-0'])
  //       : childBaseClass

  //     return h('div', { class: childClass }, [element])
  //   }
  // )
  // },
  // render() {
  //   const parentClass = [this.type, "items-center"];

  //   const parentMobileClass = ["flex"];

  //   const parentBaseClass = ["block", "md:flex"];

  //   const childBaseClass = ["flex", "items-center", "justify-center"];

  //   return h(
  //     "div",
  //     {
  //       class: parentClass.concat(
  //         this.mobile ? parentMobileClass : parentBaseClass
  //       ),
  //     },
  //     this.$slots.default().map((element, index) => {
  //       const childClass =
  //         !this.mobile && this.$slots.default().length > index + 1
  //           ? childBaseClass.concat(["mb-6", "md:mb-0"])
  //           : childBaseClass;

  //       return h("div", { class: childClass }, [element]);
  //     })
  //   );
  // },
})
</script>

<template>
  <div
    :class="[
      mobile
        ? parentClass.concat(parentMobileClass)
        : parentClass.concat(parentBaseClass),
    ]"
  >
    <template>
      <slot/>
    </template>
  </div>
</template>
