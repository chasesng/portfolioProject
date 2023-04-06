<template>
      <div id="menu-background-pattern" style="padding-left:2vw;width:99vw;height:10.5vh;position:absolute;top:0;background-color:#3E517A;overflow:hidden;display: flex;justify-content:flex-start;gap:2.5vw">
      <!-- <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">C</p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">H</p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">A</p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">S</p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">E</p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left"> </p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">S</p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">N</p>
      <p class="nameLte wt pd5 xln l" style="margin-top:-.8vh;font-size:100px;opacity:.5;text-align:left">G</p>

       -->
      </div>

      <div class="f" style="justify-content: space-between; gap: 3vw; width: 99vw; height: 5vh; position: sticky; top: 0; background-color: white;opacity:.5;border-top:1px solid gray;backdrop-filter: blur(30px);z-index:1">
  <p class="pd5 xln p3 menuBtn l" style="height: inherit; opacity: 0.8; padding-left: 2vw; display: flex; align-items: center;" @click="callContactVisible()"></p>
</div>

      
    <router-view />

</template>


<script setup>


import { onMounted, ref} from 'vue'
// import { useRouter } from 'vue-router';
import { getAuth, onAuthStateChanged } from '@firebase/auth';


const isLoggedin = ref(false);
// const router = useRouter();
var usname = ref('');

let auth;


onMounted(() => {
    auth = getAuth();
    onAuthStateChanged(auth, (user) => {
        if (user) {
            isLoggedin.value = true;
            usname = user.email;


        }
        else {
            isLoggedin.value = false;
        }
        return {
            usname
        }
    })
})



</script>

<script>
export default {
  components: {
    
  },
  data() {
    return {
      toggleSidebar: 'block',
      open: false
    }
  },
  methods: {
  go(val) {
            this.$router.push({ path: val})
        },
  callContactVisible() {
        }
      }
}
</script>

<style scoped>


.menuBtn {
  transition: .8s;
  opacity:.8
}
.menuBtn:hover {
  transform:scale(1.1);
  transition-duration: .8s;
  cursor:pointer;
}

.nameLte {
  transition: .3s;

}
.nameLte:hover {
  transform:scale(1.1);
  transition-duration: .3s;
  cursor:default;
  transform: translate(0px, -10px);
}

</style>
