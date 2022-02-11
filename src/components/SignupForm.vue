<template>
 
  <form @submit.prevent="handleSubmit">
      <label>Email:</label>
      <input type="email" required v-model="email" placeholder="abc@gmail.com">
     
      <label>Password:</label>
      <input type="password" required v-model="password">
        <div v-if="pswdError" class="error-alerts">{{pswdError}}</div>
      <label> Role:</label>
      <select v-model="role">
          <option value="developer">Web Developer</option>
          <option value="designer">Web designer</option>
          <option value="designer">IOS Developer</option>
          <option value="designer">ML Engineer</option>


      </select>

      <label></label>

    <div class="card">
           <label> Worked Under:</label>
           <br/>
           <label> Salman</label>
            <input type="checkbox" value="Salman"  v-model="names">
            <label> Irfan</label>
            <input type="checkbox" value="Irfan"  v-model="names">
            <label>Junaid</label>
            <input type="checkbox" value="Junaid"  v-model="names">
      </div>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" required>
    <div v-for="skill in skills" :key="skill" class="display-skills">
       <span @click="deleteSkill (skill)" >{{skill}}</span> 
    </div>

      <div class="terms">
           <label >Accept Terms and Conditions</label>
            <input type="checkbox"  v-model="terms" required>
      </div>

    <button class="submit-button">SIGN UP</button> 
  </form>


</template>

<script>
export default {
    data(){
        return{
            email:"",
            password:"",
            role:"Designer",    
            terms:false,
            names:[],
            tempSkill:'',
            skills:[],
            pswdError:""
        }
    },
    methods: {
        addSkill(e){
            if(e.which === 13 && this.tempSkill) {
                if(!this.skills.includes(this.tempSkill)){
                      this.skills.push(this.tempSkill)
                }
                this.tempSkill=''
            }
        },
        deleteSkill(skill){
            this.skills=this.skills.filter((item)=>
            //The filter methpd cycyles through an array and fires a function for each item in the array . 
            // if(TRUE) -> Keep it in the array 
            // if(FALSE) -> Remove it from the array
            {
                return skill !== item;
            })
        },
        handleSubmit(){
             //validation pswd
            this.pswdError= this.password.length > 5 ? '' : 
            'Password must be atleast 6 characters long'
        }
    
    }
}
</script>

<style>
form{
    max-width: 420px;
    margin:30px auto;
    background: white;
    text-align: ceter;
    padding: 40px;
    border-radius: 10px;

}
label{
    color: rgb(78, 75, 75);
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 2px;
    font-weight: bold;

}
input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border: 1px solid rgb(132, 132, 182);
    color: #555;

}
input[type="checkbox"]{
    display: inline-block;
    width: 20px;
    margin:0 10px 0 0 ;
    position: relative;
    top: 2px;

}
.card{
       border: 1px solid rgb(132, 132, 182);
}
.display-skills{
    display:inline-block;
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
.submit-button{
    padding: 10px 22px;
    border-radius: 20px;
    letter-spacing: 2px;
    background: rgb(85, 136, 165);
    color:white;
   border-style: hidden;
   font-weight: bold;
   margin-top: 20px;
}
.error-alerts{
    color: #ff0000;
    margin-top: 2px;
    font-size: 0.7rem;
    font-weight: bold;

}


</style>