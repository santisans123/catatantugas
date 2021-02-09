(<template>
  <v-card
    dark
    flat
  >
    <v-toolbar
      flat
      height="72"
    >
    <v-switch
        v-model="$vuetify.theme.dark"
        hint="DARK MODE"
        inset
        persistent-hint
        ></v-switch>
        <v-bottom-navigation
            :value="value"
            color="blue"
            grow
        >

            <v-btn
                dark
                @click.stop="drawer = !drawer"
            >
                <span>Jadwal</span>
                <v-icon>mdi-book</v-icon>
            </v-btn>

                <v-dialog
                v-model="dialog"
                    width="600px" 
                >
                <template v-slot:activator="{ on, attrs }">
                    <v-btn
                    dark
                    v-bind="attrs"
                    v-on="on"
                    >
                        <span>Note</span>
                        <v-icon>mdi-note</v-icon>
                    </v-btn>
                </template>
                <v-card>
                    <v-card-title>
                        <span class="headline">CATATAN</span>
                    </v-card-title>

                     <v-col
                        cols="12"
                        md="12"
                    >
                        <v-textarea
                        filled
                        name="input-7-4"
                        label="Tulis Disini"
                                v-model="catatan"
                        ></v-textarea>
                    </v-col>

                    <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                        color="blue"
                        text
                        @click="dialog = false"
                    >
                        Close
                    </v-btn>
                    </v-card-actions>
                </v-card>
                </v-dialog>

                <v-dialog
                    transition="dialog-top-transition"
                >
                    <template v-slot:activator="{ on, attrs }">
                        <v-btn
                            dark
                            v-bind="attrs"
                            v-on="on"
                        >
                            <span>Kalender</span>
                            <v-icon>mdi-calendar</v-icon>
                        </v-btn>
                    </template>
                    <template v-slot:default="dialog">
                        <v-card-text>
                           <v-date-picker
                                v-model="date"
                                full-width
                                class="mt-4"
                                >
                                <v-card-actions class="justify-end">
                                    <v-btn
                                        text
                                        @click="dialog.value = false"
                                    >Close</v-btn>
                                </v-card-actions>
                            </v-date-picker>
                        </v-card-text>
                    </template>
                </v-dialog>
        </v-bottom-navigation>
    </v-toolbar>

    <v-card-text>
      <v-theme-provider root>
        <v-list rounded="b">
            <div class="my-2">

                <v-navigation-drawer
                    v-model="drawer"
                    absolute
                    temporary
                    >
                    <v-bottom-navigation
                        color="blue"
                        grow
                    >
                    <v-list-item>
                        <v-list-item-content>
                            <center>
                                <v-list-item-title>JADWAL</v-list-item-title>
                            </center>
                        </v-list-item-content>
                    </v-list-item>
                    
                        <v-btn
                            @click="show = !show"
                        >
                            <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
                        </v-btn>
                        
                    </v-bottom-navigation>
                        <v-card-actions>
                            <v-btn
                                color="blue"
                                text
                            >
                                SENIN
                            </v-btn>
                            <div>
                             <v-btn
                                class="ml-16"
                                color="primary"
                                dark
                                 @click="simpanData"
                            >
                                Save
                                <v-icon
                                dark
                                right
                                >
                                mdi-checkbox-marked-circle
                                </v-icon>
                            </v-btn>
                        </div>

                        </v-card-actions>
                        <v-expand-transition>
                            <div v-show="show">
                                    <input  class="jadwal1 ml-5" v-model="senin1">
                                    <input  class="jadwal2 ml-5" v-model="senin2">
                            </div>
                        </v-expand-transition>

                        <v-card-actions>
                            <v-btn
                                color="blue"
                                text
                            >
                                SELASA
                            </v-btn>
                        </v-card-actions>
                        <v-expand-transition> 
                            <div v-show="show">
                                <input  class="jadwal1 ml-5" v-model="selasa1">
                                <input  class="jadwal2 ml-5" v-model="selasa2">
                            </div>
                        </v-expand-transition>
                        
                        <v-card-actions>
                            <v-btn
                                color="blue"
                                text
                            >
                                RABU
                            </v-btn>
                        </v-card-actions>
                      <v-expand-transition>
                            <div v-show="show">
                                <input  class="jadwal1 ml-5" v-model="rabu1">
                                <input  class="jadwal2 ml-5" v-model="rabu2">
                            </div>
                        </v-expand-transition>

                        <v-card-actions>
                            <v-btn
                                color="blue"
                                text
                            >
                                KAMIS
                            </v-btn>
                        </v-card-actions>
                        <v-expand-transition>
                            <div v-show="show">
                                <input  class="jadwal1 ml-5" v-model="kamis1">
                                <input  class="jadwal2 ml-5" v-model="kamis2">
                            </div>
                        </v-expand-transition>

                        <v-card-actions>
                            <v-btn
                                color="blue"
                                text
                            >
                                JUMAT
                            </v-btn>
                        </v-card-actions>
                        <v-expand-transition>
                            <div v-show="show">
                                <input  class="jadwal1 ml-5" v-model="jumat1">
                                <input  class="jadwal2 ml-5" v-model="jumat2">
                            </div>
                        </v-expand-transition>
                        <v-col
                            cols="12"
                            md="12"
                        >
                            <v-textarea
                            outlined
                            name="input-7-4"
                            label="Jadwal Tambahan"
                            v-model="jtmb"
                            ></v-textarea>
                        </v-col>
                        <v-responsive height="150"></v-responsive>
    
                </v-navigation-drawer>

                     <div id="app">
                    <center> <h1> TUGAS </h1> </center>
                    <v-form class="form">
                        <v-text-field
                        label="Nama Tugas"
                        v-model="nama"
                        required
                        ></v-text-field>

                        <v-text-field
                        label="Deskripsi"
                        v-model="desk"
                        required
                        ></v-text-field>

                        <v-btn @click="addTodo" color="info"> Kirim </v-btn>
                        <v-btn @click="clear" class="ml-5">Bersihkan</v-btn>
                    </v-form>

                    <v-data-table
                        :headers="headers"
                        :items="todos"
                        hide-actions
                        class="elevation-1"
                    >
                    <template v-slot:item.hapus="{item}">
                      
                            <v-btn icon @click="removeTodo(item)">
                            <v-icon color="pink">mdi-delete</v-icon>
                            </v-btn>    
                        
                    </template>
                    </v-data-table>
                </div>
            </div>

          <v-footer
            padless
            >
            <v-row
            justify="center"
            no-gutters
            >
                <v-card-text>
                    <center>
                        <v-btn
                        v-for="icon in icons"
                        :key="icon"
                        class="mx-4 blue--text"
                        icon
                        >
                            <v-icon size="24px" >
                                {{ icon }}
                            </v-icon>
                        </v-btn>
                    </center>
                </v-card-text>
                <v-col
                    class="py-4 text-center blue--text"
                    cols="12"
                >
                    {{ new Date().getFullYear() }} <v-icon color="blue">mdi-copyright</v-icon> <strong>Santi</strong>
                </v-col>
            </v-row>
            </v-footer>
        </v-list>
        
      </v-theme-provider>

    </v-card-text>
  </v-card>
</template>

<script>
  export default {
    data: () => ({

    headers: [
    { text: "Nama Tugas", value: "nama" },
    { text: "Deskripsi", value: "desk" },
    { text: "Hapus", value: "hapus" }
    ],

    nama: "",
    desk: "",
    todos: [],

        date: new Date().toISOString().substr(0, 10),

        dialog: false,
        show: false,

        icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],

        //page
        page: 1,

        drawer: null,

        //catatan
        catatan:'',

        //jadwal
        senin1:'Isi jadwal 1',
        senin2:'Isi jadwal 2',
        selasa1:'Isi jadwal 1',
        selasa2:'Isi jadwal 2',
        rabu1:'Isi jadwal 1',
        rabu2:'Isi jadwal 2',
        kamis1:'Isi jadwal 1',
        kamis2:'Isi jadwal 2',
        jumat1:'Isi jadwal 1',
        jumat2:'Isi jadwal 2',
        jtmb:''
    }),
     methods: {
        addTodo() {
        if (this.nama.trim() === "" && this.desk.trim() === "") {
            alert("Data tidak boleh kosong!");
        } else {
            this.todos.push({
            nama: this.nama,
            desk: this.desk
            });
            this.nama = "";
            this.desk = "";
            console.log(this.todos);
            this.simpan();
            
        }
        },

        removeTodo(id) {
        this.todos.splice(id, 1);
        this.simpan();
        },

        clear() {
        this.nama = "";
        this.desk = "";
        },

        simpanData() {
      localStorage.senin1 = this.senin1;
      localStorage.senin2 = this.senin2;
      localStorage.selasa1 = this.selasa1;
      localStorage.selasa2 = this.selasa2;
      localStorage.rabu1 = this.rabu1;
      localStorage.rabu2 = this.rabu2;
      localStorage.kamis1 = this.kamis1;
      localStorage.kamis2 = this.kamis2;
      localStorage.jumat1 = this.jumat1;
      localStorage.jumat2 = this.jumat2;
      localStorage.jtmb = this.jtmb;
      console.log('Diisi ya..');
    },

    simpan() {
      const parsed = JSON.stringify(this.todos);
      localStorage.setItem('nama', parsed);
    },
    },

    
    
  mounted() {
      //Simpan tugas
    if (localStorage.getItem('nama')) {
      try {
        this.todos = JSON.parse(localStorage.getItem('nama'));
      } catch(e) {
        localStorage.removeItem('nama');
      }
    }

    //catatan
    if(localStorage.catatan) this.catatan = localStorage.catatan;

    //jadwal
    if(localStorage.senin1) this.senin1 = localStorage.senin1;
    if(localStorage.senin2) this.senin2 = localStorage.senin2;
    if(localStorage.selasa1) this.selasa1 = localStorage.selasa1;
    if(localStorage.selasa2) this.selasa2 = localStorage.selasa2;
    if(localStorage.rabu1) this.rabu1 = localStorage.rabu1;
    if(localStorage.rabu2) this.rabu2 = localStorage.rabu2;
    if(localStorage.kamis1) this.kamis1 = localStorage.kamis1;
    if(localStorage.kamis2) this.kamis2 = localStorage.kamis2;
    if(localStorage.jumat1) this.jumat1 = localStorage.jumat1;
    if(localStorage.jumat2) this.jumat2 = localStorage.jumat2;
    if(localStorage.jtmb) this.jtmb = localStorage.jtmb;
  },
  //catatan
  watch:{
    catatan(newcatat) {
      localStorage.catatan = newcatat;
    },
    //todos(){
        //this.todos()
    //}
  }
}
</script>

<style scoped>
#app {
  margin-top: 30px;
}
.form {
  margin-top: 20px;
  margin-bottom: 50px;
}

.elevation-1{
    background-color: rgb(114, 169, 201);
}
.catatan{
    background-color: rgb(114, 169, 201);
    height: 90px;
    width: 600px;
}
.jadwal1{
    background-color: rgb(149, 250, 241);
    text-align: center;
}
.jadwal2{
    background-color: rgb(145, 211, 255);
    text-align: center;
}
</style>

)