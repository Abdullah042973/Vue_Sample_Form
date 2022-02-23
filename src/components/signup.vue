<template>
  <form>
    <label>Email</label>
    <input type="email" required v-model="email" />

    <label>Password</label>
    <input type="password" v-model="password" />

    <label> Role:</label>
    <select v-model="role">
      <option value="designer">Web designer</option>
      <option value="developer">Web developer</option>
      <option value="hosting">Web hosting</option>
    </select>

    <label>Education:</label>
    <div>
      <input type="checkbox" value="SSC" v-model="names" />
      <label>SSC</label>
    </div>
    <div>
      <input type="checkbox" value="HSC" v-model="names" />
      <label>HSC</label>
    </div>
    <div>
      <input type="checkbox" value="Graduation" v-model="names" />
      <label>Graduation</label>
    </div>

    <label>Skills</label>
    <input type="text" v-model="tempskills" @keyup="addskills" />
    <div v-for="skill in skills" :key="skill" class="pills">
      {{ skill }}
    </div>
    <label class="note">Press Alt + ',' to Show the Skills</label>
  </form>

  <div class="terms">
    <input type="checkbox" v-model="terms" required />
    <label>Terms and Condition</label>
  </div>

  <div class="show">
    <p>email: {{ email }}</p>
    <p>password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms & Condition: {{ terms }}</p>
    <p>Education: {{ names }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: "",
      names: [],
      tempskills: "",
      skills: [],
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
</style>