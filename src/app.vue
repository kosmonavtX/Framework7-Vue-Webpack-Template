<template>
<!-- App -->
<div id="app">

    <!-- Statusbar -->
    <f7-statusbar></f7-statusbar>

    <!-- Right Panel -->
    <f7-panel right cover layout="dark">
        <f7-view id="right-panel-view" navbar-through :dynamic-navbar="true">
            <f7-navbar v-if="$theme.ios" sliding></f7-navbar>
            <f7-pages>
                <f7-page>
                    <f7-navbar v-if="$theme.material" sliding></f7-navbar>
                    <f7-list>
                        <f7-list-item link="/ctrlpump/" link-view="#main-view" link-close-panel title="Управление насосом"></f7-list-item>
                        <f7-list-item v-if="false" link="/form/" link-view="#main-view"  title="Система" link-close-panel></f7-list-item>
                        <f7-list-item link="/params/" link-view="#main-view"  title="Параметры" link-close-panel></f7-list-item>
                        <f7-list-item link="/about/" title="О Cosmoiler"></f7-list-item>
                    </f7-list>
                </f7-page>
            </f7-pages>
        </f7-view>
    </f7-panel>

    <!-- Main Views -->
    <f7-views>
        <f7-view id="main-view" navbar-through :dynamic-navbar="true" main>
            <!-- iOS Theme Navbar -->
            <f7-navbar v-if="$theme.ios">
                <f7-nav-left>
                    <f7-link icon="icon-bars" open-panel="left"></f7-link>
                </f7-nav-left>
                <f7-nav-center sliding>CosmOiler</f7-nav-center>
                <f7-nav-right>
                    <f7-link icon="icon-bars" open-panel="right"></f7-link>
                </f7-nav-right>
            </f7-navbar>
            <!-- Pages -->
            <f7-pages>
                <f7-page>
                    <!-- Material Theme Navbar -->
                    <f7-navbar v-if="$theme.material">
                        <f7-nav-left>
                            <f7-link icon="icon-cosmoiler-logo_pict_font2" icon-size="32px"></f7-link>
                        </f7-nav-left>
                        <f7-nav-center sliding>CosmOiler</f7-nav-center>
                        <f7-nav-right>
                            <f7-link icon="icon-bars" open-panel="right"></f7-link>
                        </f7-nav-right>
                    </f7-navbar>


                    <!-- Page Content -->
                   <!-- <div v-if="connection">-->
                    <div v-if="true">
                        <!--                     <f7-grid>
                            <f7-col width="100">
                                <f7-chip text="ПОДКЛЮЧЕНО!" bg="green" color="white"></f7-chip>
                            </f7-col>
                        </f7-grid> -->

                        <f7-block-title>Выберите режим работы</f7-block-title>
                        <f7-list media-list>
                            <f7-list-item swipeout title="По пробегу..." media="<i class='icon icon-meter'></i>" link="#" :badge="badgeName1" badge-color="green" subtitle="Смазывать через заданное расстояние...">
                            <f7-swipeout-actions>
                                <f7-swipeout-button close color="purple" id="trip" v-on:click="ctrlMode($event)">{{messonoff[0]}}</f7-swipeout-button>
                                <f7-swipeout-button href="/trip/" color="teal">Настройки</f7-swipeout-button>     
                            </f7-swipeout-actions>
                            </f7-list-item>
                            <f7-list-item swipeout title="По времени..." media="<i class='icon icon-time'></i>" link="#" :badge="badgeName2" badge-color="green" subtitle="Смазывать через заданное время...">
                            <f7-swipeout-actions>
                                <f7-swipeout-button close color="purple" id="time" v-on:click="ctrlMode($event)">{{messonoff[1]}}</f7-swipeout-button>
                                <f7-swipeout-button href="/time/" color="teal">Настройки</f7-swipeout-button>
                            </f7-swipeout-actions>
                            </f7-list-item>
                            <f7-list-item swipeout title="Вручную..." media="<i class='icon icon-right-hand'></i>" link="#" :badge="badgeName3" badge-color="green" subtitle="Смазывать вручную...">
                            <f7-swipeout-actions>
                                <f7-swipeout-button close color="purple" id="manual" v-on:click="ctrlMode($event)">{{messonoff[2]}}</f7-swipeout-button>
                                <f7-swipeout-button href="/manual/" color="teal">Настройки</f7-swipeout-button>
                            </f7-swipeout-actions>                                 
                            </f7-list-item>                         
                            <f7-list-item v-if="false" swipeout title="Прокачка..." media="<i class='icon icon-repeat'></i>" link="#" :badge="badgeName4" badge-color="green" subtitle="Прокачать систему...">
                                <f7-swipeout-actions>
                                    <f7-swipeout-button close color="purple" id="pumping" v-on:click="ctrlMode($event)">{{messonoff[3]}}</f7-swipeout-button>
                                </f7-swipeout-actions>
                            </f7-list-item>
                        </f7-list>
                    </div>
                    <div class="preload" v-else="connection">
                        <f7-grid>
                            <f7-col width="100">
                                <p>Подключение к Cosmoiler...</p>
                            </f7-col>
                            <f7-col width="100">
                                <f7-preloader color="blue" size="40px"></f7-preloader>
                            </f7-col>
                        </f7-grid>
                    </div>
                </f7-page>
            </f7-pages>
        </f7-view>
    </f7-views>

    <!-- Popup -->
    <f7-popup id="popup">
        <f7-view navbar-fixed>
            <f7-pages>
                <f7-page>
                    <f7-navbar title="Popup">
                        <f7-nav-right>
                            <f7-link close-popup>Close</f7-link>
                        </f7-nav-right>
                    </f7-navbar>
                    <f7-block>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque, architecto. Cupiditate laudantium rem nesciunt numquam, ipsam. Voluptates omnis, a inventore atque ratione aliquam. Omnis iusto nemo quos ullam obcaecati, quod.</f7-block>
                </f7-page>
            </f7-pages>
        </f7-view>
    </f7-popup>

    <!-- Login Screen -->
    <f7-login-screen id="login-screen">
        <f7-view>
            <f7-pages>
                <f7-page login-screen>
                    <f7-login-screen-title>Login</f7-login-screen-title>
                    <f7-list form>
                        <f7-list-item>
                            <f7-label>Username</f7-label>
                            <f7-input name="username" placeholder="Username" type="text"></f7-input>
                        </f7-list-item>
                        <f7-list-item>
                            <f7-label>Password</f7-label>
                            <f7-input name="password" type="password" placeholder="Password"></f7-input>
                        </f7-list-item>
                    </f7-list>
                    <f7-list>
                        <f7-list-button title="Sign In" close-login-screen></f7-list-button>
                        <f7-list-label>
                            <p>Click Sign In to close Login Screen</p>
                        </f7-list-label>
                    </f7-list>
                </f7-page>
            </f7-pages>
        </f7-view>
    </f7-login-screen>

</div>
</template>

<script>
    export default {
        data: function() {
            return {
                modejson: {
                    mode: 0,
                    preset: 0
                },
                connection: this.$root.connection,
                messonoff: ['','','',''],
                interval: null,
            }
        },
        created: function() {
            console.log('app cteated');
            console.log(this.$root.uri);
            this.fetchModes();
        },
        computed: {

            badgeName1: function() { // trip
                if (this.modejson.mode == 1) {
                    this.messonoff[0] = 'ВЫКЛ';
                    return "ВКЛЮЧЕНО";
                }
                else {
                    this.messonoff[0] = 'ВКЛ';
                    return "";
                }
            },
            badgeName2: function() { // time
                if (this.modejson.mode == 2) {
                    this.messonoff[1] = 'ВЫКЛ';
                    return "ВКЛЮЧЕНО";
                }
                else {
                    this.messonoff[1] = 'ВКЛ';
                    return "";
                }
            },
            badgeName3: function() { // manual
                if (this.modejson.mode == 3) {
                    this.messonoff[2] = 'ВЫКЛ';
                    return "ВКЛЮЧЕНО";
                }
                else {
                    this.messonoff[2] = 'ВКЛ';
                    return "";
                }
            },
            badgeName4: function() { // pumping
                if (this.modejson.mode == 4) {
                    this.messonoff[3] = 'ВЫКЛ';
                    return "ВКЛЮЧЕНО";
                }
                else {
                    this.messonoff[3] = 'ВКЛ';
                    return ""
                }
            },
        },
        methods: {
            fetchModes: function() {
                var self = this;

                self.connection = false;
                this.interval = setInterval(() => {

                        this.axios.get('http://'+self.$root.uri+'/mode.json', {timeout: 1000}).then(
                                (response) => {
                                    console.log(response);
                                    console.log(response.status);
                                    if (response.status === 200) {
                                        self.modejson = response.data;
                                        self.connection = true;
                                    }
                                })
                            .catch(
                                (response) => {
                                    console.log(response);
                                    self.modejson.mode = 0; // выкл
                                    self.connection = false;
                                })
                    },
                    750);
            },
            
            send: function(data) {
                var self = this;
                var blob = new Blob([JSON.stringify(data)]);
                const dataF = new FormData();

                dataF.append('data', new File([blob], '/mode.json', { type: 'application/json' } ));
                
                this.axios.post('http://'+self.$root.uri+'/mode', dataF, {timeout: 1000, headers: { 'Content-Type': 'multipart/form-data' }}).then(
                    (response) => {
                        console.log(response);
                    })
                .catch(
                (response) => {
                    console.log('error');
                    self.connection = false;
                })
                    
            },
/*            Управление режимами*/
            ctrlMode: function(event) {
                console.log(this.modejson.mode);
                if (this.modejson.mode != null) {
                        switch(event.currentTarget.id) {
                                case 'trip': 
                                    console.log('trip x');
                                    if (this.modejson.mode === 1)
                                        this.send({mode:0, preset: this.modejson.preset});
                                    else
                                        this.send({mode:1, preset: this.modejson.preset});
                                    break;
                                case 'time': 
                                    console.log('time x'); 
                                    if (this.modejson.mode === 2)
                                        this.send({mode:0, preset: this.modejson.preset});
                                    else
                                        this.send({mode:2, preset: this.modejson.preset});
                                    break;
                                case 'manual':
                                    console.log('manual x'); 
                                    if (this.modejson.mode === 3)
                                        this.send({mode:0, preset: this.modejson.preset});                       
                                    else
                                        this.send({mode:3, preset: this.modejson.preset});                       
                                    break;
                                case 'pumping':
                                    console.log('pumping x'); 
                                    if (this.modejson.mode === 4)
                                        this.send({mode:0, preset: this.modejson.preset});                       
                                    else
                                        this.send({mode:4, preset: this.modejson.preset});
                                    break;
                        };
/*                        break;
                    default:
                        console.log("mode <> 0");
                        this.send({mode:0, preset: this.modejson.preset}); 
                        break;
                        
                }*/
                }
            },
        },
        
/*        beforeDestroy: function () {
            console.log('clear interval');
            console.log(this.interval);
            clearInterval(this.interval);
        }*/
    }

</script>
