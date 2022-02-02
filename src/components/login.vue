<template>
<div id="app">
  <v-app id="inspire">
    <v-app id="inspire">
      <v-main> 
           <div class="pinkbox" ref="pinkbox">
                <!-- 注册 -->
                <div class="signup nodisplay" ref="signup" >
                    <div class="login_header" >
                        <h1>Register</h1>
                    </div>
                    
                    <div class="login_body">
                        <v-form 
                       ref="form"
                        v-model="valid"
                        lazy-validation>
                       <v-text-field
                        v-model="name"
                        :counter="10"
                        :rules="nameRules"
                        label="Name"
                        required
                      ></v-text-field>
                      <v-text-field
                      v-model="email"
                      :rules="emailRules"
                      label="E-mail"
                      required
                    ></v-text-field>
                     <v-text-field
                      v-model="password"
                      :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                      :rules="[rules.required, rules.min]"
                      :type="show1 ? 'text' : 'password'"
                      name="input-10-1"
                      label="password"
                      hint="At least 8 characters"
                      counter
                      @click:append="show1 = !show1"
                    ></v-text-field>
                    </v-form>
                    </div>
                    <div class="login_submit" >
                    <input type="submit" name="submit" value="注册">
                    
                    </div>
                    <!-- <div class="login_text">
                        <input type="checkbox" checked="checked" style="margin-right: 10px">
                        我已阅读并同意
                        <a href="#"><ins>《 须知 》</ins></a>
                    </div> -->
                </div>
                <!-- 登录 -->
                <div class="signin" ref="signin">
                    <div class="login_header">
                      <h1>Sign In</h1>  
                    </div>
                    <div class="login_body"> 
                      <v-form 
                       ref="form"
                        v-model="valid"
                        lazy-validation>
                       <v-text-field
                        v-model="name"
                        :counter="10"
                        :rules="nameRules"
                        label="Name"
                        required
                      ></v-text-field>
                  
                     <v-text-field
                      v-model="password"
                      :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                      :rules="[rules.required, rules.min]"
                      :type="show1 ? 'text' : 'password'"
                      name="input-10-1"
                      label="password"
                      hint="At least 8 characters"
                      counter
                      @click:append="show1 = !show1"
                    ></v-text-field>
                        
            
                      </v-form>
        
                    </div>
                    <div class="login_submit" >
                    <input type="submit" name="submit" value="登录" class="buttom-submit">
                    </div>
                </div>
        </div>
        <v-container  
        class="welcome"
        fluid>
          <v-row
            align="center"
            justify="center"
          >
            <v-col cols="8">
              <v-card>
                <v-card-text>
                  <v-row>
                    <!-- left -->
                    <v-col
                      cols="12"
                      md="6"
                      class="left"
                    >
                      <h2 class="title"><span>BLOOM</span>&<br>BOUQUET</h2>
                        <p class="desc">Pick your perfect <span>bouquet</span></p>
                        <img class="flower smaller" src="https://hbimg.huabanimg.com/c09305167a883e60179a45374df73252304001359acca-W3qbYm_fw658/format/webp" />
                        <p class="account">Have an account?</p>
                        <v-card-action>
                            <button class="button" id="signup" @click="signup">点击登录</button>
                        </v-card-action>
                    </v-col>
                    <!-- right -->
                    <v-col
                      cols="12"
                      md="6"
                      class="right"
                    >
                      <h2 class="title"><span>BLOOM</span>&<br>BOUQUET</h2>
                        <p class="desc">Pick your perfect <span>bouquet</span></p>
                        <img class="flower" src="https://hbimg.huabanimg.com/b28be92c8198975a74ad656eba00b352c9b9e589819af-lDXUAS_fw658/format/webp" />
                        <p class="account">Don't have an account?</p>
                        <v-card-action>
                             <button class="button" id="signin" @click="signin">点击注册</button>
                        </v-card-action>
                    </v-col>
                  </v-row>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
  
    </v-app>
  </v-app>
</div>

</template>

<script>
export default {
    name:"login",
    data: () => ({
    show1: false,
    valid: true,
    //用户名
    name: '',
    nameRules: [
      v => !!v || 'Name is required',
      v => (v && v.length <= 10) || 'Name must be less than 10 characters',
    ],
    //邮件
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
    checkbox: false,
    //密码
    password: '',
      rules: {
        required: value => !!value || 'Required.',
        min: v => v.length >= 8 || 'Min 8 characters',
        emailMatch: () => ('The email and password you entered don\'t match'),
      },
  }),
     methods:{
         //  登录
         signin:function(){
             this.$refs.pinkbox.style.transform="translateX(110%)";
             this.$refs.signin.style.display="none";
             this.$refs.signup.style.display="block";
         },
         signup:function(){
             this.$refs.pinkbox.style.transform="translateX(0%)";
             this.$refs.signup.style.display="none";
             this.$refs.signin.style.display="block";
         }
     },

}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,400|Lora");
    
    #inspire{
        background-color: #eadff1;
    }
    .welcome{
        margin-top: 10%;
        z-index: 1;
    }
 .pinkbox {
 position: absolute;
  top: 20%;
  margin-left: 400px;
  background: #eac7cc;
  width: 340px;
  height: 500px;
  border-radius: 5px;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  transition: all 0.5s ease-in-out;
  z-index: 2;
} 
.display{
  display: block;
  transition: all 0.5s ease;
}

.nodisplay{
  display: none; 
  transition: all 0.5s ease;
}

.flower{
  top: 45%;
  width: 130px;
  height: 130px;
  margin-left: 30%;
  opacity: 0.9;
}
/* 字体和按钮的样式 */
h1 {
  font-family: "Open Sans", sans-serif;
  text-align: center;
  margin-top: 95px;
  text-transform: uppercase;
  color: #f6f6f6;
  font-size: 2em;
  letter-spacing: 8px;
}

.title {
  font-family: "Lora", serif;
  color: #8e9aaf;
  font-size: 1.8em;
  line-height: 1.1em;
  letter-spacing: 3px;
  text-align: center;
  font-weight: 300;
  margin-top: 20%;
}
.desc {
  margin-top: -8px;
}

.account {
  margin-top: 20px;
  font-size: 10px;
}
/* 按钮 */
.button {
  padding: 12px;
  font-family: "Open Sans", sans-serif;
  text-transform: uppercase;
  letter-spacing: 3px;
  font-size: 11px;
  border-radius: 10px;
  margin: auto;
  outline: none;
  display: block;
   margin-top: 3%;
  background: #f6f6f6;
  color: #ce7d88;
  border: solid 1px #eac7cc;
}
.button:hover {
  background: #f7dbdf;
  color: #f6f6f6;
  transition: background-color 1s ease-out;
}
/* 表单样式 */
.login_body {
  display: flex;
  align-items: center;
  flex-direction: column;
  padding-top: 7px;
}
.signin {
  padding-top: 35px;
}
.signin input {
  padding: 12px;
}
input {
  background: #f1e7e8;
  width: 65%;
  color: #ce7d88;
  border: none;
  border-bottom: 1px solid rgba(246, 246, 246, 0.5);
  padding: 9px;
  font-weight: 100;
}
p {
  font-family: "Open Sans", sans-serif;
  font-size: 0.7em;
  letter-spacing: 2px;
  color: #8e9aaf;
  text-align: center;
}
span {
  color: #eac7cc;
  height: 34px;
  width: 10px;
  line-height: 34px;
}
.login_submit {
  margin-left: 5px;
  padding: 12px;
}

.singup .login_submit {
  margin-left: auto;
  margin-top: -15px;
  padding: 0;
}

.login_text {
  margin-left: auto;
}
input[type="submit"] {
  margin-left: 40px;
  margin-top: 15px;
  padding: 12px;
  border-color: #ce7d88;
  background-color: #fff;
}

.login_submit input[type="submit"] {
  margin-left: 40px;
  padding: 12px;
  border-color: #ce7d88;
  background-color: #fff;
}
.checkbox {
  display: inline;
  white-space: nowrap;
  position: relative;
  left: -52px;
  top: 25px;
}

input[type="checkbox"] {
  width: 15px;
  background: #ce7d88;
}

.checkbox input[type="checkbox"]:checked + label {
  color: #ce7d88;
  transition: 0.5s all ease;
}
</style>