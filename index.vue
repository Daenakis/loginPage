<template>
<div>
<Header/>
  <div class="global-block">
    <img src="../../assets/img/bg-sign-up.svg" class="bg">
    <div class="main-block">
      <div class="main-data">
        <div class="top-data-info">
          <p class="sign-up-tittle">{{ getField('TITLE') }}</p>
          <div class="for-info">
            <p class="sign-up-info">{{ getField('DESCRIPTION_1') }}<br>{{ getField('DESCRIPTION_2') }}</p>
          </div>
        </div>
        <div class="data-input-fields">
          <div class="data-input-body">
          <div class="svg-img">
            <svg width="30px" height="30px" viewBox="0 0 30 30" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
            <g id="Symbols" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
              <g id="ic/mail_sign_up_ic" :fill="this.fill_email">
            <g id="icons/mail_sign_up_ic" transform="translate(6.000000, 8.000000)">
                <path d="M18,1.73240812 L9,7.39907479 L-2.22044605e-16,1.73240812 L0,1 C-6.76353751e-17,0.44771525 0.44771525,1.01453063e-16 1,0 L17,0 C17.5522847,-1.01453063e-16 18,0.44771525 18,1 L18,1.73240812 Z M18,2.93425855 L18,13 C18,13.5522847 17.5522847,14 17,14 L1,14 C0.44771525,14 6.76353751e-17,13.5522847 0,13 L0,2.93425855 L9,8.60092521 L18,2.93425855 Z" id="Combined-Shape"></path>
               </g>
               </g>
              </g>
              </svg>
              </div>
            <input type="text" class="data-input" id="border-email" :placeholder="this.placeholder.email_p?this.getField('EMAIL_PLACEHOLDER'):this.getField('EMAIL_PLACEHOLDER_FALSE')" @blur="allGoesDefault()" v-on:click="focusEmail()" name="mail" v-model="input.email" />
            <p class="error-p" id="error-email" v-on:click="hideErrorEmail()">{{ getField('EMAIL_PLACEHOLDER_FALSE') }}</p>
          </div>
          <div class="data-input-body">
          <div class="svg-img">
            <svg width="30px" height="30px" viewBox="0 0 30 30" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
            <g id="Symbols" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
            <g id="ic/password-off" :fill="this.fill_password">
            <g id="Icons-/-ic_password_sign_up" transform="translate(6.000000, 4.000000)">
                <path d="M1,7 L17,7 C17.5522847,7 18,7.44771525 18,8 L18,18 C18,18.5522847 17.5522847,19 17,19 L1,19 C0.44771525,19 6.76353751e-17,18.5522847 0,18 L0,8 C-6.76353751e-17,7.44771525 0.44771525,7 1,7 Z M8,10.9998075 L8,14.0001925 C8,14.5562834 8.44771525,15 9,15 C9.55613518,15 10,14.5523709 10,14.0001925 L10,10.9998075 C10,10.4437166 9.55228475,10 9,10 C8.44386482,10 8,10.4476291 8,10.9998075 Z" id="Combined-Shape"></path>
                <path d="M13.9090909,7 L13.9090909,5.5 C13.9090909,3.01471863 11.711216,1 9,1 C6.28878396,1 4.09090909,3.01471863 4.09090909,5.5 L4.09090909,7 L3,7 L3,5.5 C3,2.46243388 5.6862915,5.57991845e-16 9,0 C12.3137085,-5.57991845e-16 15,2.46243388 15,5.5 L15,7 L13.9090909,7 Z M13.9090909,7 L13.9090909,5.5 C13.9090909,3.01471863 11.711216,1 9,1 C6.28878396,1 4.09090909,3.01471863 4.09090909,5.5 L4.09090909,7 L3,7 L3,5.5 C3,2.46243388 5.6862915,5.57991845e-16 9,0 C12.3137085,-5.57991845e-16 15,2.46243388 15,5.5 L15,7 L13.9090909,7 Z" id="Rectangle-15" fill-rule="nonzero"></path>
              </g>
                </g>
                </g>
          </svg>
          </div>
            <input type="password" id="border-password" class="data-input" :placeholder="this.placeholder.password_p?this.getField('PASSWORD_PLACEHOLDER'):this.getField('PASSWORD_PLACEHOLDER_FALSE')" @blur="allGoesDefault()" name="password" v-on:click="focusPassword()" v-model="input.password"  />
             <p class="error-p" id="error-password" v-on:click="hideErrorPassword()">{{ getField('PASSWORD_PLACEHOLDER_FALSE') }}</p>
          </div>
        </div>

        <div class="no-acc-and-forget">
            <nuxt-link :to="this.getField('NO_ACCOUNT_LINK')">
            <span class="no-acc-and-forget-a uderline-style">{{ getField('NO_ACCOUNT') }}</span>
            </nuxt-link>
            <nuxt-link :to="this.getField('FORGOT_PASS_LINK')">
            <span class="no-acc-and-forget-a uderline-style">{{ getField('FORGOT_PASS') }}</span>
            </nuxt-link>
        </div>
        <div class="gradient_sign-up-button cursor" v-on:click="logIn()">
          <gradient-button bg="gradient-button__white-block" style="margin-top: 40px;"/>
          <p class="gradient-button__text_sign-up">{{ getField('BUTTON_TEXT') }}</p>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>
<script>
import axios from "axios";
import GradientButton from "~/components/GradientButton/GradientButton.vue";
import Header from "~/components/Header/Header.vue";
  export default {
    name: 'Login',
        components: {
            Header,
            GradientButton,
        },
        data() {
            return {
              fill_email: '#E0E0E0',
              fill_password: '#E0E0E0',
              placeholder:{
                email_p: true,
                password_p: true,
              },
                input: {
	              email: "",
	              password: "",
                },
                body:{
                	"email": "",
                	"password": "",
                  "from_new_fridn": 1
                }
            }
        },
        methods: {
          getField(key) {
            if(this.stateJson.length === undefined) {
              for (let i = 0; i < this.stateJson.logInPage.data.acf.log_in.length; i++) {
                if(this.stateJson.logInPage.data.acf.log_in[i]['key'] == key) {
                  return this.stateJson.logInPage.data.acf.log_in[i]['value'];
                }
              }
            }
            return '';
          },
            logIn() {
                if(this.input.password !== "" && this.input.email !== "") {
                  if(this.validEmail(this.input.email) !== false){
                     this.sendData();
                   }else{
                     this.input.email = '';
                     this.errorEmail();
                   }
                 }else {
                    this.placeholder.email_p = false;
                    this.placeholder.password_p = false;
                    if(this.input.email === ""){
                      this.errorEmail();
                    }
                    if(this.input.password === ""){
                      this.errorPassword();
                    }
                  }
            },
            sendData() {
             let _self = this;
              _self.body.username = _self.input.email;
              _self.body.password = _self.input.password;
              _self.body.from_new_fridn = 1;
                axios.post('https://api.dev.fridn.com/api/qc/login_new', _self.body
                  )
                  .then(function (response) {
                     console.log(response)
                     if(response.data.code === -2){
                       document.getElementById('error-email').style.display = 'block'
                       document.getElementById('border-email').style.border = '0.5px solid #d5425e'
                       _self.fill_email = "#d5425e";
                     }
                     else if(response.data.code === -6){
                       document.getElementById('error-password').style.display = 'block';
                       document.getElementById('border-password').style.border = '0.5px solid #d5425e'
                       _self.fill_password = "#d5425e";
                     }
                     else{
                       window.location.href = response.data.url;
                     }
                   })
                .catch(function (error) {
               console.log(error);
                   });
            },
            errorEmail(){
              document.getElementById('error-email').style.display = 'block';
              this.fill_email = "#d5425e";
              document.getElementById('border-email').style.border = '0.5px solid #d5425e';
              this.placeholder.email_p = false;
            },
            errorPassword(){
              document.getElementById('error-password').style.display = 'block';
              this.fill_password = "#d5425e";
              document.getElementById('border-password').style.border = '0.5px solid #d5425e'
            },
            hideErrorEmail() {
              document.getElementById('error-email').style.display = 'none'
              document.getElementById("border-email").focus()
              this.focusEmail();
            },
            hideErrorPassword() {
              document.getElementById('error-password').style.display = 'none'
              document.getElementById("border-password").focus()
              this.focusPassword();
            },
            allGoesDefault(){
              this.fill_email = "#e0e0e0";
              document.getElementById('border-email').style.border = '0.5px solid #7b8b93'
              this.fill_password = "#e0e0e0";
              document.getElementById('border-password').style.border = '0.5px solid #7b8b93'
            },
            focusEmail(){
              this.allGoesDefault()
              this.fill_email = "#d8ad4c";
              document.getElementById('border-email').style.border = '0.5px solid #d8ad4c'
            },
            focusPassword(){
              this.allGoesDefault()
              this.fill_password = "#d8ad4c";
              document.getElementById('border-password').style.border = '0.5px solid #d8ad4c'
            },
             validEmail: function (email) {
      var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
  },
    mounted() {
      this.loadPageJson('logInPage', 65);
    }
  
  }
</script>

<style lang="scss" scoped src="./index.scss"></style>
