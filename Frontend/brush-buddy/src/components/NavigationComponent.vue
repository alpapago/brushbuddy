<script setup lang="ts">
import { RouterLink } from 'vue-router'
import { ref } from 'vue'
const activeTab = ref<string | null>('home')
const setActiveTab = (path: string) => {
  activeTab.value = path
}

import { watch, onMounted } from 'vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();

const updateTabFromUrl = () => {
      const path = router.currentRoute.value.path;
      console.log(path)
      switch (path) {
        case '/':
        activeTab.value = 'home';
          break;
        case '/search':
        activeTab.value = 'search';
          break;
        case '/draft':
        activeTab.value = 'draft';
          break;
        case '/community':
          activeTab.value = 'community';
           break;
      //   case '/diary':
      //     activeTab.value = 'diary';
      //     break;
      }

      if(path.startsWith("/diary")){
        activeTab.value = 'diary';
      }
    };

watch(route, updateTabFromUrl);
onMounted(
  () => {
    updateTabFromUrl()
  }
)
</script>

<template>
  <div class="bottom-navbar">
    <router-link to="/" @click="setActiveTab('home')">
      <div class="navicon" :class="{ inactiveTab: activeTab !== 'home' }">
        <svg viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path
            id="Vector"
            d="M22.524 11.3116L12.0738 0.251884C11.9986 0.172037 11.9092 0.10869 11.8108 0.0654689C11.7125 0.0222474 11.607 0 11.5005 0C11.394 0 11.2885 0.0222474 11.1901 0.0654689C11.0917 0.10869 11.0023 0.172037 10.9271 0.251884L0.476967 11.3116C0.17252 11.634 0 12.072 0 12.5288C0 13.4773 0.728135 14.2485 1.62372 14.2485H2.7248V22.1402C2.7248 22.6158 3.0876 23 3.53666 23H9.87676V16.9811H12.7183V23H19.4643C19.9134 23 20.2762 22.6158 20.2762 22.1402V14.2485H21.3772C21.8085 14.2485 22.2221 14.0684 22.5265 13.7433C23.1582 13.0715 23.1582 11.9833 22.524 11.3116Z"
            fill="black"
          />
        </svg>
        <p>홈</p>
      </div>
    </router-link>
    <router-link to="/search" @click="setActiveTab('search')">
      <div class="navicon" :class="{ inactiveTab: activeTab !== 'search' }">
        <svg viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g id="&#240;&#159;&#166;&#134; icon &#34;camera&#34;">
            <g id="Group 8">
              <path
                id="Vector"
                d="M24.2208 3.46011H20.0192L19.0183 0.65495C18.9491 0.463001 18.8224 0.297081 18.6554 0.179857C18.4884 0.0626324 18.2893 -0.000179993 18.0853 3.87418e-07H8.60703C8.18997 3.87418e-07 7.81615 0.262598 7.67713 0.65495L6.67308 3.46011H2.47151C1.106 3.46011 0 4.56612 0 5.93162V20.0192C0 21.3847 1.106 22.4907 2.47151 22.4907H24.2208C25.5863 22.4907 26.6923 21.3847 26.6923 20.0192V5.93162C26.6923 4.56612 25.5863 3.46011 24.2208 3.46011ZM24.4679 20.0192C24.4679 20.1552 24.3567 20.2664 24.2208 20.2664H2.47151C2.33558 20.2664 2.22436 20.1552 2.22436 20.0192V5.93162C2.22436 5.79569 2.33558 5.68447 2.47151 5.68447H8.2394L8.76768 4.20775L9.47515 2.22436H17.2141L17.9215 4.20775L18.4498 5.68447H24.2208C24.3567 5.68447 24.4679 5.79569 24.4679 5.93162V20.0192ZM13.3462 7.66168C10.6151 7.66168 8.40313 9.87368 8.40313 12.6047C8.40313 15.3357 10.6151 17.5477 13.3462 17.5477C16.0772 17.5477 18.2892 15.3357 18.2892 12.6047C18.2892 9.87368 16.0772 7.66168 13.3462 7.66168ZM13.3462 15.5705C11.7088 15.5705 10.3803 14.2421 10.3803 12.6047C10.3803 10.9673 11.7088 9.63889 13.3462 9.63889C14.9835 9.63889 16.312 10.9673 16.312 12.6047C16.312 14.2421 14.9835 15.5705 13.3462 15.5705Z"
                fill="black"
              />
            </g>
          </g>
        </svg>
        <p>검색</p>
      </div>
    </router-link>
    <router-link to="/draft" @click="setActiveTab('draft')">
      <div class="navicon" :class="{ inactiveTab: activeTab !== 'draft' }">
        <svg viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g id="&#240;&#159;&#166;&#134; icon &#34;picture&#34;">
            <g id="Group 7">
              <path
                id="Vector"
                d="M27 0H1C0.446875 0 0 0.446875 0 1V21C0 21.5531 0.446875 22 1 22H27C27.5531 22 28 21.5531 28 21V1C28 0.446875 27.5531 0 27 0ZM25.75 19.75H2.25V18.5031L6.57812 13.3687L11.2688 18.9312L18.5656 10.2812L25.75 18.8V19.75ZM25.75 15.6938L18.7563 7.4C18.6562 7.28125 18.475 7.28125 18.375 7.4L11.2688 15.825L6.76875 10.4906C6.66875 10.3719 6.4875 10.3719 6.3875 10.4906L2.25 15.3969V2.25H25.75V15.6938ZM7.5 9.25C8.22935 9.25 8.92882 8.96027 9.44454 8.44454C9.96027 7.92882 10.25 7.22935 10.25 6.5C10.25 5.77065 9.96027 5.07118 9.44454 4.55546C8.92882 4.03973 8.22935 3.75 7.5 3.75C6.77065 3.75 6.07118 4.03973 5.55546 4.55546C5.03973 5.07118 4.75 5.77065 4.75 6.5C4.75 7.22935 5.03973 7.92882 5.55546 8.44454C6.07118 8.96027 6.77065 9.25 7.5 9.25ZM7.5 5.625C7.98438 5.625 8.375 6.01562 8.375 6.5C8.375 6.98438 7.98438 7.375 7.5 7.375C7.01562 7.375 6.625 6.98438 6.625 6.5C6.625 6.01562 7.01562 5.625 7.5 5.625Z"
                fill="black"
              />
            </g>
          </g>
        </svg>
        <p>도안 생성</p>
      </div>
    </router-link>
    <router-link to="/community" @click="setActiveTab('community')">
      <div class="navicon" :class="{ inactiveTab: activeTab !== 'community' }">
        <svg viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g id="&#240;&#159;&#166;&#134; icon &#34;team&#34;">
            <path
              id="Vector"
              d="M22.2562 18.4288C21.474 17.6436 20.56 17.0027 19.5562 16.5355C20.9718 15.3851 21.8749 13.6298 21.8749 11.6613C21.8749 8.1882 18.9875 5.33889 15.525 5.39218C12.1156 5.44546 9.36877 8.23209 9.36877 11.6613C9.36877 13.6298 10.275 15.3851 11.6875 16.5355C10.6835 17.0024 9.76945 17.6433 8.98752 18.4288C7.28128 20.1434 6.31254 22.4066 6.25004 24.8202C6.24921 24.8536 6.25506 24.8869 6.26725 24.9181C6.27943 24.9492 6.29772 24.9776 6.32101 25.0016C6.34431 25.0255 6.37216 25.0445 6.4029 25.0575C6.43365 25.0705 6.46667 25.0772 6.50004 25.0772H8.25003C8.3844 25.0772 8.4969 24.9706 8.50002 24.8358C8.5594 23.0178 9.29377 21.3157 10.5844 20.0243C11.2448 19.3583 12.0304 18.8303 12.8956 18.4709C13.7608 18.1115 14.6885 17.9278 15.625 17.9304C17.5281 17.9304 19.3187 18.6733 20.6656 20.0243C21.9531 21.3157 22.6874 23.0178 22.7499 24.8358C22.7531 24.9706 22.8656 25.0772 22.9999 25.0772H24.7499C24.7833 25.0772 24.8163 25.0705 24.8471 25.0575C24.8778 25.0445 24.9056 25.0255 24.9289 25.0016C24.9522 24.9776 24.9705 24.9492 24.9827 24.9181C24.9949 24.8869 25.0008 24.8536 24.9999 24.8202C24.9374 22.4066 23.9687 20.1434 22.2562 18.4288ZM15.625 15.6735C14.5562 15.6735 13.55 15.2566 12.7969 14.4981C12.4189 14.1219 12.1204 13.6733 11.919 13.1789C11.7177 12.6845 11.6177 12.1545 11.625 11.6205C11.6344 10.5924 12.0438 9.59875 12.7594 8.86213C13.5094 8.09103 14.5125 7.6616 15.5844 7.64906C16.6437 7.63966 17.6718 8.05342 18.4281 8.79631C19.2031 9.55801 19.6281 10.5767 19.6281 11.6613C19.6281 12.7333 19.2125 13.7395 18.4562 14.4981C18.0852 14.872 17.6439 15.1684 17.158 15.3702C16.672 15.572 16.1509 15.6751 15.625 15.6735ZM7.7969 12.4888C7.76878 12.2161 7.75315 11.9403 7.75315 11.6613C7.75315 11.1629 7.80003 10.677 7.88753 10.2037C7.9094 10.0909 7.85003 9.9749 7.7469 9.92788C7.32191 9.73668 6.93128 9.47337 6.59379 9.14111C6.1961 8.75433 5.88316 8.28864 5.67493 7.77376C5.46671 7.25888 5.36776 6.70612 5.38442 6.15074C5.41254 5.14455 5.81567 4.18851 6.51879 3.46756C7.29066 2.67451 8.32815 2.24194 9.43127 2.25448C10.4281 2.26389 11.3906 2.64944 12.1188 3.33277C12.3656 3.56473 12.5781 3.82176 12.7562 4.0976C12.8187 4.19478 12.9406 4.23552 13.0469 4.19791C13.5969 4.0067 14.1781 3.87192 14.775 3.80922C14.95 3.79042 15.05 3.60234 14.9719 3.44562C13.9562 1.43009 11.8813 0.0383502 9.48127 0.000735485C6.01567 -0.052552 3.12818 2.79676 3.12818 6.26672C3.12818 8.23522 4.0313 9.99057 5.44692 11.141C4.45318 11.6017 3.53756 12.2381 2.74381 13.0342C1.03132 14.7488 0.0625778 17.012 7.81433e-05 19.4287C-0.00075593 19.4622 0.00509412 19.4955 0.0172838 19.5266C0.0294734 19.5578 0.0477559 19.5862 0.071054 19.6101C0.094352 19.6341 0.122195 19.6531 0.15294 19.6661C0.183686 19.6791 0.216714 19.6858 0.250077 19.6858H2.00319C2.13757 19.6858 2.25006 19.5792 2.25319 19.4444C2.31256 17.6264 3.04693 15.9243 4.33755 14.6329C5.2563 13.7113 6.38129 13.0718 7.60941 12.7615C7.73128 12.7302 7.81253 12.6142 7.7969 12.4888Z"
              fill="black"
            />
          </g>
        </svg>
        <p>커뮤니티</p>
      </div>
    </router-link>
    <router-link to="/diary" @click="setActiveTab('diary')">
      <div class="navicon" :class="{ inactiveTab: activeTab !== 'diary' }">
        <svg viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g id="Group 5">
            <circle id="Ellipse 3" cx="10" cy="10" r="9" stroke="black" stroke-width="2" />
          </g>
        </svg>
        <p>그림기록</p>
      </div>
    </router-link>
  </div>
</template>

<style scoped>
.bottom-navbar {
  background-color: #fff;
  color: white;
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100vw;
  height: 10vh; /* 적절한 높이로 조정하세요 */
  z-index: 99999;
}

.bottom-navbar a {
  text-decoration: none;
  padding: 2px;
}
.navicon {
  width: 4rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  opacity: 1;
  transition: opacity 0.3s ease;
}
.inactiveTab {
  opacity: 0.4;
}
p {
  font-size: 0.8rem;
  margin-top: 0.2rem;
  color: black;
}
svg {
  width: 3rem;
  height: 1.5rem;
  fill: white;
}
</style>
