<template>
  <div>
    <div class="title-box">
      <span class="text-h4 font-weight-light">SERVIÇOS</span>
    </div>
    <div class="buttons-box">
      <v-btn
        class="button white--text"
        color="#404449"
        @click.stop=";(modalService = !modalService), (formTitle = 'NOVO')"
        >Novo Serviço</v-btn
      >
      <v-text-field
        v-model="searchWord"
        prepend-icon="mdi-magnify"
        label="Pesquisar"
        hide-details
      ></v-text-field>
    </div>
    <v-dialog
      v-model="modalService"
      max-width="800px"
      no-click-animation
      persistent
    >
      <v-card>
        <v-card-title>
          <span class="headline">{{ formTitle }} SERVIÇO</span>
        </v-card-title>
        <v-card-text>
          <v-container grid-list-md>
            <v-layout wrap column>
              <v-flex xs12 sm6 md4>
                <v-form ref="form" v-model="validation">
                  <v-text-field
                    v-model="editedItem.title"
                    :rules="[(v) => !!v || 'Campo Obrigatório']"
                    color="cyan darken-2"
                    label="Titulo"
                  />
                  <v-text-field
                    v-model="editedItem.description"
                    :rules="[(v) => !!v || 'Campo Obrigatório']"
                    color="cyan darken-2"
                    label="Descrição"
                  />
                  <v-text-field
                    v-model="editedItem.icon"
                    :rules="[(v) => !!v || 'Campo Obrigatório']"
                    color="cyan darken-2"
                    label="Icone"
                  >
                  </v-text-field>
                </v-form>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn color="#404449" text @click="cancelForm">
            Cancelar
          </v-btn>
          <v-btn color="#404449" text @click="$refs.form.reset()">
            Reiniciar
          </v-btn>
          <v-btn color="#404449" text @click="onSubmit">
            Salvar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-flex>
      <v-data-table :headers="headers" :items="services" :search="searchWord">
        <template v-slot:item.action="{ item }">
          <v-icon medium class="mr-2" color="primary" @click="dialogEdit(item)">
            mdi-circle-edit-outline
          </v-icon>
          <v-icon medium color="error" @click="deleteService(item)">
            mdi-delete
          </v-icon>
        </template>
      </v-data-table>
    </v-flex>
  </div>
</template>

<script>
export default {
  layout: 'dashboard',
  async asyncData({ $axios }) {
    const [servicesRes] = await Promise.all([$axios.get('/service')])
    return {
      services: servicesRes.data.dados,
    }
  },
  data() {
    return {
      services: [],
      headers: [
        { text: 'Serviço', align: 'left', sortable: true, value: 'title' },
        { text: 'Descrição', sortable: true, value: 'description' },
        { text: 'Icone', sortable: true, value: 'icon' },
        { text: '', value: 'action', sortable: false },
      ],
      searchWord: '',
      modalService: false,
      formTitle: '',
      editedIndex: -1,
      editedItem: {
        id: 0,
        title: '',
        description: '',
        icon: '',
      },
      defaultItem: {
        id: 0,
        title: '',
        description: '',
        icon: '',
      },
    }
  },
  methods: {
    onSubmit() {
      if (!this.validation) {
        this.$refs.form.validate()
        return
      }
      if (this.editedIndex !== -1) {
        this.editService()
      } else {
        this.newService()
      }
      this.cancelForm()
    },
    cancelForm() {
      this.modalService = false
      this.editedItem = Object.assign({}, this.defaultItem)
      this.editedIndex = -1
    },
    newService() {
      const Service = {
        title: this.editedItem.title,
        description: this.editedItem.description,
        icon: this.editedItem.icon,
      }
      this.$axios
        .$post('service', Service)
        .then((res) => {
          this.services.push(res.dados)
        })
        .catch(({ response }) => {
          window.alert(
            'Ocorreu um erro \n' + Object.values(response.data.dados).join('\n')
          )
        })
    },
    editService() {
      const Service = {
        title: this.editedItem.title,
        description: this.editedItem.description,
        icon: this.editedItem.icon,
      }
      this.$axios
        .$put(`service/${this.editedItem.id}`, Service)
        .then((res) => {
          this.services = this.services.map((e) => {
            if (e.id === this.editedItem.id) {
              return Object.assign(e, Service)
            }
            return e
          })
        })
        .catch(({ response }) => {
          window.alert(
            'Ocorreu um erro \n' + Object.values(response.data.dados).join('\n')
          )
        })
      window.location.reload()
    },
    dialogEdit(item) {
      this.formTitle = 'EDITAR'
      this.modalService = true
      this.editedIndex = item.id
      this.editedItem = Object.assign({}, item)
    },
    deleteService(item) {
      const ok = window.confirm(
        'Você tem certeza de que deseja excluir esse serviço?'
      )
      if (ok) {
        this.$axios
          .post(`service/${item.id}`, { id: item.id, _method: 'delete' })
          .then((res) => {
            this.services = this.services.filter((e) => e.id !== item.id)
          })
          .catch(({ response }) => {
            window.alert(
              'Ocorreu um erro \n' +
                Object.values(response.data.dados).join('\n')
            )
          })
        window.location.reload()
      }
    },
  },
}
</script>

<style>
.title-box {
  padding-left: 10px;
  padding-block: 10px;
  border-style: solid;
  border-inline-width: 0px;
  border-top-width: 0px;
  border-bottom-width: 3px;
  border-color: #000000;
}
.buttons-box {
  padding-top: 10px;
  padding-inline: 10px;
  margin-bottom: 20px;
  display: flex;
  flex-direction: row;
}
.button {
  padding-block: 10px;
  padding-inline: 25px;
  margin-top: 15px;
  margin-top: 10px;
  margin-right: 45vw;
}
@media screen and (max-width: 702px) {
  .button {
    margin-right: 25vw;
  }
}
</style>
