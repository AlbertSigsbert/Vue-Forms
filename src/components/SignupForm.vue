<template>
  <form @submit.prevent="handleSubmit">
    <label>Email</label>
    <input type="email" v-model="email" required />

    <label>Password</label>
    <input type="password" v-model="password" required />

    <label>Role</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label>Skills:</label>
    <small>Press , to add a new skill && click on skill to delete it</small>
    <input type="text" v-model="tempSkill" @keyup="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Accept terms & conditions</label>
    </div>

    <div class="submit">
      <button>Create Account</button>
    </div>
    <!-- <div>
      <input type="checkbox" value="shaun" v-model="names"/>
      <label>Shaun</label>

      <input type="checkbox" value="mario" v-model="names"/>
      <label>Mario</label>

      <input type="checkbox" value="yoshi" v-model="names"/>
      <label>Yoshi</label>
    </div> -->
  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
  <!-- <p>Names:{{ names }}</p> -->
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      terms: false,
      tempSkill: "",
      skills: [],
      //   names:[]
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        const tempSkill = this.tempSkill.slice(0, -1);
        if (!this.skills.includes(tempSkill)) {
          this.skills.push(tempSkill);
        }
        this.tempSkill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => item !== skill);
    },
    handleSubmit(){
        
        //optional - form Validations
        console.log('Email: ', this.email);
        console.log('Password: ', this.password);
        console.log('Role: ', this.role);
        console.log('Terms Accepted: ', this.terms);
        console.log('Skills: ', this.skills);
        console.log('form submitted');
    }
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}

label {
  display: inline-block;
  color: #aaa;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
small {
  display: block;
  font-size: 12px;
  margin: 0;
  font-weight: 600;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}

input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}

.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}

button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  border-radius: 20px;
  color: white;
}
.submit {
  text-align: center;
}
</style>