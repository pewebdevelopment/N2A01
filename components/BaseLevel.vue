<script>
// import { h, defineComponent } from "vue";
import { h, defineComponent, useSlots } from 'vue';

export default defineComponent({
  name: "BaseLevel",
  props: {
    mobile: Boolean,
    type: {
      type: String,
      default: "justify-between",
    },
  },

  // const props = defineProps({

  //   mobile: {
  //     type: Boolean,

  //   },
  //   type: {
  //     type: String,
  //     default: "justify-between",
  //   },

  // });

  setup(props) {
    const slots = useSlots();
    // slots = slots.default ? slots.default() : [];
    const parentClass = [props.type, "items-center"];

    const parentMobileClass = ["flex"];

    const parentBaseClass = ["block", "md:flex"];

    const childBaseClass = ["flex", "items-center", "justify-center"];

    return () => h(
      "div",
      {
        class: parentClass.concat(
          props.mobile ? parentMobileClass : parentBaseClass
        )
      },

      slots.default().map((element, index) => {
        const childClass =
          !props.mobile && slots.default().length > index + 1
            ? childBaseClass.concat(["mb-6", "md:mb-0"])
            : childBaseClass;

        return h("div", { class: childClass }, [element]);
      })
    )
  },

})

</script>
  //   render() {
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
  //     ((element, index) => {
  //       const childClass =
  //         !this.mobile 
  //           ? childBaseClass.concat(["mb-6", "md:mb-0"])
  //           : childBaseClass;

  //       return h("div", { class: childClass }, [element]);
  //     })
  //   );
  // },
//   render() {
//     const parentClass = [this.type, "items-center"];

//     const parentMobileClass = ["flex"];

//     const parentBaseClass = ["block", "md:flex"];

//     const childBaseClass = ["flex", "items-center", "justify-center"];

//     return h(
//       "div",
//       {
//         class: parentClass.concat(
//           this.mobile ? parentMobileClass : parentBaseClass
//         ),
//       },
//       {
//         this.$slots.default().map((element, index) => {
//           const childClass =
//             !this.mobile && this.$slots.default().length > index + 1
//               ? childBaseClass.concat(["mb-6", "md:mb-0"])
//               : childBaseClass;

//           return h("div", { class: childClass }, [element]);
//         })
    
//     );

//   },
// });



 //   if (this.$slots.default()) {}