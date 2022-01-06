<template>
  <div :id="`task-${index}`" class="tasks">
    <p>
      {{ message }}

      {{ this.currentPosition }} here
    </p>
  </div>
</template>

<script>
import Draggable from "plain-draggable";
export default {
  name: "Task",
  props: {
    message: {
      type: String,
    },
    index: {
      type: Number,
    },
    position: {
      type: Object,
    },
  },
  data() {
    return {
      draggable: undefined,
      newposition: null,
    };
  },
  computed: {
    currentPosition: function () {
      if (this.newposition) {
        return this.newposition;
      } else {
        return this.position;
      }
    },
  },
  mounted() {
    // var slot1_out = document.getElementById(`#task-${this.index}`);
    //var slot1_in = document.getElementById(`#task-${this.index + 1}`);

    // this.line1 = new LeaderLine(slot1_in, slot1_out, {
    //   startPlug: "behind",
    //   endPlug: "behind",
    //   size: 4,
    //   startPlugSize: 1,
    //   endPlugSize: 1,
    //   startSocket: "left",
    //   endSocket: "right",
    //   color: "#fb8c00"
    //   // path: 'grid',
    //   // dropShadow: {color: '#111', dx: 0, dy: 2, blur: 0.2}
    // });

    this.draggable = new Draggable(
      document.querySelector(`#task-${this.index}`),
      {
        left: this.position.left,
        top: this.position.top,
        onMove: function () {
          // this.line1.position();
        },
      }
    );

    this.draggable.onDrag = function (newPosition) {
      console.log(newPosition);
      this.newposition = newPosition;
    }.bind(this);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.tasks {
  background-color: #f0f0f0;
  width: fit-content;
  align-self: flex-start;
}
</style>
