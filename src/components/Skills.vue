<template>
  <div class="holder">
    <form @submit.prevent="addSkill">
      <input type="text" placeholder="What needs to be done?" v-model="skill" />
    </form>

    <ul>
      <li v-for="(data, index) in skills" v-bind:class="{ completed: data.complete }" :key="index">
        <i class="fa fa-check-square" v-on:click="toggle(index)"></i>
        <span class="item-count">{{ index + 1 }}</span>
        <span class="item-text">{{ data.skill }}</span>
        <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
      </li>
    </ul>
    <div class="buttons">
      <button name="clear all" v-on:click="clearAll()">Clear All</button>
      <button name="clear complete" v-on:click="clearCompleted()">Clear Completed</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      skill: "",
      complete: "",
      skills: []
    };
  },
  methods: {
    addSkill() {
      this.skills.push({ skill: this.skill, complete: false });
      this.skill = "";
    },
    remove(index) {
      this.skills.splice(index, 1);
    },
    toggle(index) {
      if (this.skills[index].complete == false) {
        this.$set(this.skills[index], "complete", true);
      } else {
        this.$set(this.skills[index], "complete", false);
      }
    },
    clearAll(i) {
      if (confirm("Are you sure you want to clear all items?")) {
        for (i = this.skills.length; i--; ) {
          this.skills.splice(i, 1);
        }
      }
    },
    clearCompleted() {
      for (var i = 0; i < this.skills.length; i++) {
        if (this.skills[i].complete === true) {
          this.skills.splice(i, 1);
          i--;
        }
      }
    }
  },
  mounted() {
    console.log("App  mounted!");
    if (localStorage.getItem("skills"))
      this.skills = JSON.parse(localStorage.getItem("skills"));
  },
  watch: {
    skills: {
      handler() {
        localStorage.setItem("skills", JSON.stringify(this.skills));
      },
      deep: true
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}

.holder {
  background: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}

.completed {
  background-color: #c0f0d5;
  text-decoration: line-through;
}

p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687f7f;
}

.fa-check-square {
  float: left;
  cursor: pointer;
  margin: 2px 20px 0 0;
}

.fa-minus-circle {
  float: right;
  cursor: pointer;
  margin: 2px 0px 0 20px;
}

.item-count {
  margin-right: 15px;
}

.buttons {
  width: 100%;
  text-align: right;
}
</style>
