<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <h1>File a Complaint</h1>
                    <hr> 
                    <div class="form-group">
                        <label for="email">Mail</label>
                        <input
                                type="text"
                                id="email"
                                v-model="userData.email"
                                class="form-control">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                                type="password"
                                id="password"
                                v-model.lazy="userData.password"
                                class="form-control">
                    </div>
                    <div class="form-group">
                        <label for="age">Age</label>
                        <input
                                type="number"
                                id="age"
                                v-model="userData.age"
                                class="form-control">
                    </div>

                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <label for="message">Message</label><br>
                    <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
                    <textarea
                            id="message"
                            rows="5"
                            v-model="userData.message"
                            class="form-control"></textarea>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <div class="form-group">
                        <label for="sendmail">
                            <input
                                    type="checkbox"
                                    id="sendmail"
                                    v-model="sendMail"
                                    value="SendMail"> Send Mail
                        </label>
                        <label for="sendInfomail">
                            <input
                                    type="checkbox"
                                    id="sendInfomail"
                                    v-model="sendMail"
                                    value="SendInfoMail"> Send Infomail
                        </label>
                    </div>
<li v-for="mail in sendMail" v-bind:key="mail">{{mail}}</li>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <label for="male">
                        <input
                                type="radio"
                                id="male"
                                v-model="gender"
                                value="Male"> Male
                    </label>
                    <label for="female">
                        <input
                                type="radio"
                                id="female"
                                v-model="gender"
                                value="Female"> Female
                    </label>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
                    <label for="priority">Priority</label>
                    <select
                            v-model="setPriority"
                            id="priority"
                            class="form-control">
                        <option  :selected="priority == 'Medium'" v-for="priority in priorities" v-bind:key="priority">{{ priority }}</option>
                    </select>
                </div>
            </div>
            <hr>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <button
                            @click.prevent="formSubmitted"
                            class="btn btn-primary">Submit!
                    </button>
                </div>
            </div>

              <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                 <app-switcher v-model="switched" @input="switchSomething"></app-switcher>

                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="isSubmitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body" >
                        <p>Mail: {{ userData.email }}</p>
                        <p>Password: {{ userData.password }}</p>
                        <p>Age: {{ userData.age }}</p>
                        <p style="white-space: pre;">Message: {{ userData.message}} </p>
                        <p><strong>Send Mail?</strong></p>
                        <ul>
                            <li></li>
                        </ul>
                        <p>Gender:{{ gender }}</p>
                        <p>Priority: {{setPriority}} </p>
                        <p>Switched: {{ switched }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Switch from './component/Switch.vue';

    export default {
        data() {
            return {
                email: '',
                userData: {
                    email: '',
                    password: '',
                    age: 27,
                    message: 'A new text',
                },
                    sendMail: [],
                    gender: 'Male',
                    priorities: ['High', 'Low', 'Medium'],
                    setPriority: 'High',
                    dataSwitch: true,
                    switched: true,
                    isSubmitted: false

            }
        },
        components: {
            appSwitcher: Switch
        },
        methods: {
            switchSomething(isOn){
                this.switched = !isOne
            },
            formSubmitted(event){
                this.isSubmitted = !this.isSubmitted;
            }
        }
    }
</script>

<style>

</style>
