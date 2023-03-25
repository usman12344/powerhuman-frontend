<template>
  <section class="py-[70px] flex flex-col items-center justify-center px-4">
    <div class="text-[32px] font-semibold text-dark">
      New Role
    </div>
    <p class="mt-4 text-base leading-7 text-center mb-[50px] text-grey">
      Manage your employees to achieve <br>
      a bigger goals for your company
    </p>
    <form class="w-full card" @submit.prevent="createRole">
      <div class="form-group">
        <label for="" class="text-grey">Role Name</label>
        <input type="text" class="input-field" value="Product Marketing" v-model="role.name">
      </div>
      <div class="form-group">
        <label for="idRes" class="text-grey">Responsibility</label>
        <ul id="listResp" class="flex flex-col gap-4">
          <li class="items-center block w-full gap-5">
            <div class="form-group " v-for="(responsibility, index) in list_respon.list_respon" :key="index">
              <input type="text" id="" name="responsibility" class="w-full mt-3 input-field down" v-model="responsibility.name">
           </div>

            <button @click.prevent="addNumber" role="button" id="addRsp" class="flex mx-auto mt-5">
              <img src="/assets/svgs/ric-plus.svg" alt="" class="">
            </button>
          </li>
        </ul>
      </div>

      <!-- <div class="form-group" v-for="(responsibility, index) in list_respon.list_respon" :key="index">
              <input type="text" id="" name="responsibility" class="w-full input-field" v-model="responsibility.name">
        </div> -->

      <button type="submit" class="w-full btn btn-primary mt-[14px]">
        Save Role
      </button>
    </form>
  </section>
</template>

<script>
export default {
  layout: 'form',
  middleware: 'auth',

  data() {
    return {
      role: {
        name: '',
        company_id: this.$route.params.id,
      },
      list_respon: 
        {list_respon:[
          {
        name: '',
        role_id: '',
      }
        ]},
      responsibility: {
        name: '',
        role_id: '',
      },
    }
  },

 

  async fetch() {
    await this.$axios.get('/role', {
      params: {
        // company_id : this.$route.params.id,
        limit: 10000,
      }
    }).then(({ data }) => {
      this.responsibility.role_id = data.data.total + 2
      this.list_respon.list_respon[0].role_id = data.data.total + 2
      // this.list_respon[0].list_respon.role_id = data.data.total + 2
    })
  },

  // computed: {
  //   down() {
  //     if(this.list_respon.list_respon > 1){
        
  //     }
  //   }
  // },

  methods: {
    async createRole() {
      try {
        //Send Registration Data to Server
        // let [res1, res2, res3] = await Promise.all(
        //   this.$axios.post('/role', this.role),
        //   // this.$axios.post('/responsibility', this.responsibility),
        //   this.$axios.post('/responsibility', this.list_respon)
        // )
        let response = await this.$axios.post('/role', this.role)
        // let responsibilitysingle = await this.$axios.post('/responsibility', this.responsibility)
        let responsibility = await this.$axios.post('/responsibility', this.list_respon)

        // redirect to my page team
        this.$router.push({ name: 'companies-id-roles' })
        console.log(response)
        console.log(responsibility)
        // console.log(responsibilitysingle)

      } catch (err) {
        console.log(err)
      }
    },

    addNumber() {
      this.list_respon.list_respon.push(
        {
          name: '',
          role_id: this.responsibility.role_id,
        }
      );
    }
  }
}
</script>

<!-- <style scoped>
   	li:first-of-type {
      /* border: 1px dashed black; */
   /* background: rgb(250, 2, 2) !important; */
   /* display: flex; */
}

</style> -->