<template>
  <div>
    <center style="margin:20px 0 20px 0">
    <van-image  justify="center" width="200" height="200" src="https://raw.githubusercontent.com/ZOYBAD14xx/CeitSoftWareWeb/main/image/Logo.png" />
    <h2 id="text">WhatsApp help</h2>
    <p id="text">ພຽງແຕ່ທ່ານປ້ອນເບີໂທ ແລະ ຂໍ້ຄວາມ ກໍ່ສາມາດສົ່ງຂໍ້ຄວາມໄດ້</p>
    </center>
    <van-form @submit="onSubmit" style="margin-top:30px">
      <van-cell-group inset>
        <van-field
        autocomplete="off"
          v-model="phoneNumber"
          name='phoneNumber'
          label='ເບີໂທລະສັບ'
          placeholder='ກະລຸນາໃສ່ເບີໂທ ຕົວຢ່າງ: 20xxxxxxxx'
          :rules="[{ required: true }]"
        />
        <van-field
        autocomplete="off"
          v-model="msg"
          name='msg'
          label='ຂໍ້ຄວາມ'
          placeholder='ກະລຸນາໃສ່ຂໍ້ຄວາມທີ່ຢາກສົ່ງ'
          :rules="[{ required: true }]"
        />
      </van-cell-group>
      <div style="margin: 16px">
        <van-button @click="onCountUsing" round block color="#1989fa" native-type="submit">
          ສົ່ງ
        </van-button>
      </div>
    </van-form>
    <van-tabbar v-model="active">
  <van-tabbar-item> &copy; {{ new Date().getFullYear() }} —
        <strong>CEIT Software</strong>
  </van-tabbar-item>
  </van-tabbar>
  </div>
</template>

<script>
import countapi from 'countapi-js'
export default {
  name: 'IndexPage',
  data () {
    return {
      code: '+856',
      phoneNumber: '',
      msg: '',
      url: 'https://api.whatsapp.com/send',
      weburl: 'https://software-whatsapp.netlify.app'
    }
  },
  methods: {
    onSubmit () {
      window.location.href = this.url + '/?phone=' + this.code + this.phoneNumber + '&text=' + this.msg
    },
    onCountUsing () {
      countapi.hit('software-whatsapp.netlify.app', 'visits').then((result) => {
        console.log(result.value)
      })
    }
  }
}
</script>
<style>
#text{
  color: #169fc6;
  font-family: 'Noto Serif Lao', sans-serif ;
}
div{
  font-family: 'Noto Serif Lao', sans-serif ;
}
</style>
