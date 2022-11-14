
<script>
import { h, defineComponent, useSlots } from "vue";
export default defineComponent({
  name: "BaseButtons",
  props: {
    noWrap: Boolean,
    type: {
      type: String,
      default: "justify-start",
    },
    classAddon: {
      type: String,
      default: "mr-3 last:mr-0 mb-3",
    },
    mb: {
      type: String,
      default: "-mb-3",
    },
  },


  setup(props) {

    const slots = useSlots();
    const hasSlot = slots;

    const parentClass = [
      "flex",
      "items-center",
      props.type,
      props.noWrap ? "flex-nowrap" : "flex-wrap",
    ];
    if (props.mb) {
      parentClass.push(props.mb);
    }

    return () => h(
      "div",
      { class: parentClass },
      hasSlot
        ? slots.default().map((element) => {
          if (
            element &&
            element.children &&
            typeof element.children === "object"
          ) {
            return h(
              element,
              {},
              element.children.map((child) => {
                return h(child, { class: [props.classAddon] });
              })
            );
          }
          return h(element, { class: [props.classAddon] });
        })
        : null
    );


  }


});
</script>

// import { defineComponent } from 'vue'


// export default defineComponent({
//   name: 'BaseButtons',
//   props: {
//     noWrap: Boolean,
//     type: {
//       type: String,
//       default: 'justify-start',
//     },
//     mb: {
//       type: String,
//       default: '-mb-3',
//     },
//   },

// })

// </script>
