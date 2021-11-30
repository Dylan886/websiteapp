<template>
    <v-row justify="center">
        <v-dialog v-model="dialog1" persistent max-width="600px">
            <template v-slot:activator="{ on, attrs }">
                <v-btn color="primary" dark v-bind="attrs" v-on="on">
                    Join us
                </v-btn>
            </template>
            <v-card>
                <v-card-title>
                    <span class="text-h5">User Profile</span>
                </v-card-title>
                <v-card-text>
                    <v-container>
                        <v-row>
                            <v-col cols="12" sm="6" md="4">
                                <v-text-field v-model="nickname" name="nickname" label="nickname*" required>
                                </v-text-field>
                            </v-col>
                            <v-col cols="12" sm="6">
                                <v-select v-model="location"
                                    :items="['河北省','山西省','辽宁省','吉林省','黑龙江省','江苏省','浙江省','安徽省','福建省','江西省','山东省','河南省','湖北省','湖南省','广东省','海南省','四川省','贵州省','云南省','陕西省','甘肃省','青海省','台湾省','海外']"
                                    label="*province" required></v-select>
                            </v-col>
                            <v-col cols="3" sm="3" md="2">
                                <v-text-field v-model="age" label="age" hint="age" type="age">
                                </v-text-field>
                            </v-col>
                            <v-col cols="3" sm="3" md="2">
                                <v-select v-model="sex" label="sex" hint="sex" :items="['男','女']" persistent-hint
                                    required></v-select>
                            </v-col>
                            <v-col cols="6">
                                <v-select v-model="constellation"
                                    :items="['白羊座','金牛座','双子座','巨蟹座','狮子座','室女座','天秤座','天蝎座','人马座','摩羯座','宝瓶座','双鱼座']"
                                    label="constellation*"></v-select>
                            </v-col>
                            <v-col cols="4">
                                <v-text-field v-model="phone" label="phone*" type="phone" required></v-text-field>
                            </v-col>
                            <v-col cols="4">
                                <v-text-field v-model="qq" label="qq" type="phone"></v-text-field>
                            </v-col>
                            <v-col cols="4">
                                <v-text-field v-model="vx" label="vx" type="phone"></v-text-field>
                            </v-col>
                            <v-col cols="12">
                                <v-text-field v-model="introduction" label="introduction*" type="introduction" required>
                                </v-text-field>
                            </v-col>
                        </v-row>
                    </v-container>
                    <small>*indicates required field</small>
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="blue darken-1" text @click="dialog1 = false">
                        Close
                    </v-btn>
                    <v-btn color="blue darken-1" text @click="login()">
                        Save
                    </v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
        <v-dialog v-model="dialog2" width="500">
            <template v-slot:activator="{ on, attrs }">
                <v-btn color="red lighten-2" dark v-bind="attrs" v-on="on">
                    GET ONE
                </v-btn>
            </template>

            <v-card class="mx-auto" max-width="460">
                <v-img src="https://cdn.vuetifyjs.com/images/cards/house.jpg" :aspect-ratio="16/9">
                </v-img>
                <v-card-title>
                    <div class="text-h4 mb-2">
                        Welcome Home...
                    </div>
                    <div class="text-h6 font-weight-regular grey--text">
                        Monday, 12:30 PM, Mostly Sunny
                    </div>
                </v-card-title>
                <v-row class="px-4 grey--text" align="center">
                    <v-avatar size="24" class="mr-4">
                        <v-img src="https://cdn.vuetifyjs.com/images/weather/part-cloud-48px.png" contain></v-img>
                    </v-avatar>

                    <span>81° / 62°</span>
                </v-row>

                <v-divider class="mt-6 mx-4"></v-divider>

                <v-card-text>
                    <v-chip class="mr-2" @click="lights">
                        <v-icon left>
                            mdi-brightness-5
                        </v-icon>
                        Turn on Lights
                    </v-chip>
                    <v-chip class="mr-2" @click="alarm">
                        <v-icon left>
                            mdi-alarm-check
                        </v-icon>
                        Set alarm
                    </v-chip>
                    <v-chip @click="blinds">
                        <v-icon left>
                            mdi-blinds
                        </v-icon>
                        Close blinds
                    </v-chip>
                </v-card-text>
            </v-card>
        </v-dialog>
    </v-row>
</template>

<script>
    export default {
        data: () => ({
            dialog1: false,
            dialog2: false,
            nickname: "",
            location: "",
            sex: "男",
            age: 0,
            constellation: "",
            phone: "",
            qq: "",
            vx: "",
            introduction: ""
        }),
        methods: {
            login: function() {
                this.$http.post('http://127.0.0.1:31245/login', {
                    nickname: this.nickname,
                    location: this.location,
                    sex: this.sex,
                    age: this.age,
                    constellation: this.constellation,
                    phone: this.phone,
                    qq: this.qq,
                    vx: this.vx,
                    introduction: this.introduction
                }, {
                    emulateJSON: true
                }).then(function(res) {
                    console.log(this.introduction);
                    this.dialog1 = false;
                }, function(res) {
                    console.log(res.status);
                })
            },
            get: function() {
                this.$http.get('http://127.0.0.1:31245/get?id=1', {
                    emulateJSON: true
                }).then(function(res) {
                    console.log(this.introduction);
                    this.dialog2 = false;
                }, function(res) {
                    console.log(res.status);
                })
            }
        },
    }
</script>

<style>
</style>
