<template>
  <div class="main">
    <form class="form-wrapper">
      <div class="input-wrapper">
        <input class="input" v-model.trim="plan" required>
        <label class="label">
          <span class="content-name">
            Add your plan
          </span>
        </label>
      </div>
      <button type="button" class="button" @click="addList(plan)">Confirm</button>
    </form>
    <div class="main-plans">
      <h2>Your plans</h2>
      <ol>
        <li v-for="item of plans" :key="item">
          <p class="main-plan">{{item}}</p>
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
      plans: []
    }
  },
  methods: {
    addList(plan) {
      this.plans.push(plan);
      this.plan = ''
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
  }

  &-plan {
    text-align: left;
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
