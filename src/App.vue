<template>
  <div class="main">
    <div class="form-wrapper">
      <div class="main-form">
        <div class="input-wrapper">
          <input class="input" v-model.trim="plan" required>
          <label class="label">
            <span class="content-name">
              Add your plan
            </span>
          </label>
        </div>
      </div>
      <button class="button" @click="addList(plan)">Confirm</button>
    </div>
    <h2>Your plans</h2>
    <p v-for="item of plans" :key="item">{{item}}</p>
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
      console.log(plan)
      this.plans.push(plan);
    }
  }
}
</script>

<style lang="scss">
.main {
  &-form {}
}

.form-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #fff;
  padding: 30px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.15);
  border-radius: 20px;
  max-width: 60%;
  margin: 50px auto;
}

.input-wrapper {
  position: relative;
  margin-bottom: 40px;
}

.input {
  border: none;
  border-bottom: 1px solid #7e7a7a;
  width: 100%;
  height: 30px;
  padding: 6px 15px;
  transition: border 2px ease;
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
  top: -2px;
  transition: top 0.3s ease 0s;
}

.input:focus-visible {
  outline: none;
  border-bottom: 1px solid #fbc2eb;
  border-image: linear-gradient(to right top, #a6c1ee, #fbc2eb, #a6c1ee);
  border-image-slice: 1;
}

.input:focus~.label,
.input:not(:focus):valid~.label {
  top: -26px;
  font-size: 12px;
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
}

.button:hover {
  background-position: right center;
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
