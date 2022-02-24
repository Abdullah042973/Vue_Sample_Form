<template>
  <form @submit.prevent="formsubmit">
    <label>Email</label>
    <input type="email" required v-model="email" />

    <label>Password</label>
    <input type="password" v-model="password" />
    <div class="error" v-if="passworderror">{{ passworderror }}</div>

    <label> Role:</label>
    <select v-model="role">
      <option value="designer">Web designer</option>
      <option value="developer">Web developer</option>
      <option value="hosting">Web hosting</option>
    </select>

    <label>Education:</label>
    <div>
      <input type="checkbox" value="SSC" v-model="education" />
      <label>SSC</label>
    </div>
    <div>
      <input type="checkbox" value="HSC" v-model="education" />
      <label>HSC</label>
    </div>
    <div>
      <input type="checkbox" value="Graduation" v-model="education" />
      <label>Graduation</label>
    </div>

    <label>Skills</label>
    <input type="text" v-model="tempskills" @keyup.alt="addskills" />
    <div v-for="skill in skills" :key="skill" class="pills">
      <span @click="deleteskills(skill)">{{ skill }}</span>
    </div>
    <label class="note">Press Alt + ',' to Enter the Skills</label>

    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Terms and Condition</label>
    </div>

    <div class="submit">
      <button>Create An Account</button>
    </div>
  </form>

  <!--<div class="show">
    <p>email: {{ email }}</p>
    <p>password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms & Condition: {{ terms }}</p>
    <p>Education: {{ education }}</p>
    <p>Skills: {{ skills }}</p>
  </div> -->
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: "",
      education: [],
      tempskills: "",
      skills: [],
      passworderror: ''
    };
  },
  methods: {
    addskills(e) {
      if (e.key === "," && this.tempskills) {
        if (!this.skills.includes(this.tempskills)) {
          this.skills.push(this.tempskills);
        }
        this.tempskills = "";
      }
    },
    deleteskills(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    formsubmit(){
      this.passworderror = this.password.length > 5 ? '' : "password must be greater than 5 character"

      if(!this.passworderror){
        console.log('Email : ', this.email)
        console.log('Role : ', this.role)
        console.log('Education : ', this.education)
        console.log('Skills : ', this.skills)
      }
    }
  },
};
</script>

<style>
form {
  max-width: 450px;
  margin: 10px auto;
  padding: 40px;
  background: white;
  border-radius: 10px;
  text-align: left;
}
label {
  display: inline-block;
  font-weight: bold;
  font-size: 0.5em;
  font-family: "Times New Roman";
  color: rgb(160, 160, 160);
  margin: 25px 0 15px;
  text-transform: uppercase;
  letter-spacing: 1px;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid rgb(160, 160, 160);
  color: #555;
  font-weight: bold;
  font-size: 0.8em;
  font-family: "Times New Roman";
  letter-spacing: 1px;
  caret-color: rgb(255, 93, 93);
}
p {
  display: block;
  font-weight: bold;
  font-size: 0.7em;
  font-family: "Times New Roman";
  color: rgb(102, 101, 101);
  margin: 25px 0 15px;
  text-transform: uppercase;
  letter-spacing: 1px;
}
.show {
  max-width: 450px;
  background: white;
  color: rgb(214, 235, 253);
  padding: 40px;
  border-radius: 10px;
  margin: 10px auto;
  text-align: left;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  position: relative;
  margin: 0 10px 0 0;
  top: 2px;
}
.note {
  display: block;
  text-align: center;
  color: rgba(255, 0, 0, 0.548);
  text-transform: uppercase;
  font-size: 0.5em;
}
.pills {
  display: inline-block;
  background: #d2d8dd;
  color: #2c3e50;
  padding: 6px 12px;
  margin: 20px 10px 0 0;
  border-radius: 20px;
  font-weight: bold;
  font-size: 12px;
  letter-spacing: 1px;
  cursor: pointer;
}
button {
  color: white;
  background: #2c3e50;
  border-radius: 20px;
  padding: 10px 20px;
  border: 0;
  margin-top: 20px;
  letter-spacing: 1px;
}
.submit {
  text-align: center;
}
.error{
  color: red;
  font-size: 0.7em;
  letter-spacing: 1px;
  font-weight: bold;
  margin-top: 10px;
}
</style>