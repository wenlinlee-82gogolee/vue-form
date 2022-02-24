<template>
  <form @submit.prevent="handleSubmit">
    <label>Email: </label>
    <input type="email" v-model="email" />

    <label>Password: </label>
    <input type="password" v-model="password" />
    <div v-if="passwordError" class="error">{{ passwordError }}</div>

    <label>Desired Position: </label>
    <select v-model="role">
      <option value="web-designer">Web Designer</option>
      <option value="web-developer">Web Developer</option>
    </select>

    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup.ctrl="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="term">
      <input type="checkbox" v-model="term" required />
      <label>Accept terms and conditions</label>
    </div>

    <div class="submit">
      <button>Create an Account</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: '',
      term: false,
      tempSkill: '',
      skills: [],
      passwordError: '',
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === ',' && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = '';
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter(item => skill !== item);
    },
    handleSubmit() {
      this.passwordError =
        this.password.length > 5
          ? ''
          : 'Password must be at least 6 characters long!';
      if (!this.passwordError) {
        console.log('successfully submitted');
        console.log('Email:', this.email);
        console.log('Password:', this.password);
        console.log('Role:', this.role);
        console.log('Skills:', this.skills);
        console.log('Terms accepted:', this.term);
      }
    },
  },
};
</script>

<style>
form {
  max-width: 42rem;
  margin: 3rem auto;
  background: #fff;
  text-align: left;
  padding: 4rem;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 2.5rem 0 1.5rem;
  font-size: 1rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 1rem 0.6rem;
  width: 100%;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type='checkbox'] {
  display: inline-block;
  width: 1.6rem;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.pill {
  display: inline-block;
  margin: 2rem 1rem 0 0;
  padding: 0.6rem 1.2rem;
  background: #eee;
  border-radius: 2rem;
  font-size: 1.2rem;
  letter-spacing: 1px;
  font-weight: 700;
  color: #777;
  cursor: pointer;
}
button {
  background: #146356;
  border: 0;
  padding: 1rem 2rem;
  margin-top: 2rem;
  color: #fff;
  border-radius: 2rem;
}
.submit {
  text-align: center;
}
.error {
  color: #b33030;
  font-weight: 700;
  font-size: 1.3rem;
  margin-top: 1rem;
}
</style>
