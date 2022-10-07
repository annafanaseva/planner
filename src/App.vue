<template>
  <div class="main">
    <form class="form-wrapper">
      <div class="input-wrapper">
        <input class="input" v-model.trim="plan" required>

        <label class="label">
          <span class="content-name">
            Your plan
          </span>
        </label>
      </div>

      <div class="input-wrapper">
        <select class="input" v-model.trim="importance" required>
          <option>1</option>
          <option>2</option>
          <option>3</option>
        </select>

        <label class="label">
          <span class="content-name">
            Importance
          </span>
        </label>
      </div>

      <button type="button" class="button" @click="addList(plan, importance)">Add</button>
    </form>

    <div class="main-plans">
      <h2>Your plans</h2>

      <ol>
        <li v-for="(item, index) of plans" :key="index">
          <p class="main-plan" :class="{'main-plan-ready': item.ready}">{{item.plan}}</p>

          <div class="main-stars">
            <div v-for="i in item.importance" :key="i" class="main-star">
              <img src="@/assets/img/star.svg" alt="">
            </div>
          </div>
          <div class="main-plan-buttons">
            <div class="main-mark" @click="makePlanReady(item)">
              <img src="@/assets/img/mark.svg" alt="mark">
            </div>

            <div class="main-trash" @click="deletePlan(index)">
              <img src="@/assets/img/trash.svg" alt="trash">
            </div>
          </div>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      plans: [
        { plan: 'do homework', importance: 3, ready: false }
      ]
    }
  },

  methods: {
    addList(plan, importance) {
      this.plans.unshift({
        plan: plan,
        importance: Number(importance),
        ready: false
      });
      this.plan = '';
      this.importance = '';
    },
    deletePlan(index) {
      this.plans.splice(index, 1);
    },
    makePlanReady(item) {
      item.ready = true;
      console.log(item);
    }
  }
}
</script>

<style lang="scss">
.form-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #fff;
  padding: 30px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.15);
  border-radius: 20px;
  max-width: 500px;
  margin: 50px auto;
  box-sizing: border-box;
}

.input {
  border: none;
  border-bottom: 1px solid #7e7a7a;
  width: 100%;
  height: 30px;
  padding: 6px 15px;
  box-sizing: border-box;
  transition: border 2px ease;

  &-wrapper {
    position: relative;
    width: 400px;
    margin-bottom: 40px;
  }

  &:focus-visible {
    outline: none;
    border-bottom: 1px solid #fbc2eb;
    border-image: linear-gradient(to right top, #a6c1ee, #fbc2eb, #a6c1ee);
    border-image-slice: 1;
  }

  &:focus~.label,
  &:not(:focus):valid~.label {
    top: -26px;
    font-size: 12px;
  }
}

.label {
  position: absolute;
  bottom: 0px;
  left: 15px;
  pointer-events: none;
  color: #7e7a7a;
  font-size: 14px;
  line-height: 40px;
  white-space: nowrap;
  top: -3px;
  transition: top 0.3s ease 0s;
}

.button {
  width: 100%;
  padding: 10px;
  text-align: center;
  margin-bottom: 40px;
  transition: 0.5s;
  background-size: 200% auto;
  color: white;
  font-size: 14px;
  box-shadow: 0 0 20px #eee;
  border-radius: 20px;
  border: none;
  background-image: linear-gradient(to right, #fbc2eb 0%, #a6c1ee 51%, #fbc2eb 100%);
  cursor: pointer;

  &:hover {
    background-position: right center;
  }
}

.main {
  &-plans {
    max-width: 500px;
    margin: 50px auto 0;

    ol {
      padding: 0;
    }

    li {
      display: flex;
      justify-content: space-between;
      border-bottom: 1px solid #7e7a7a;
    }
  }

  &-trash {
    display: flex;
    justify-content: center;
    align-items: center;

    img {
      padding: 8px;
    }

    &:hover img {
      box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.15);
      border-radius: 10px;
    }
  }

  &-mark {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 10px;

    img {
      padding: 8px;
    }

    &:hover img {
      box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.15);
      border-radius: 10px;
    }
  }

  &-stars {
    display: flex;
    align-items: center;
  }

  &-plan {
    text-align: left;
    width: 200px;

    &-ready {
      text-decoration: line-through;
    }

    &-buttons {
      display: flex;
    }
  }
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
