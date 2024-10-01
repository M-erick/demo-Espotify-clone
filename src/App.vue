<script setup>
import {ref} from 'vue'
import {RouterLink,RouterView} from 'vue-router'
import ChevronUp from 'vue-material-design-icons/ChevronUp.vue'
import ChevronDown from 'vue-material-design-icons/ChevronDown.vue'
import ChevronRight from 'vue-material-design-icons/ChevronRight.vue'
import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue'
import MenuItem from './components/MenuItem.vue';
let openMenu = ref(false)
</script>


<template>
  <div>
      <div 
        id="TopNav"
        class="
          w-[calc(100%-240px)] 
          h-[60px] 
          fixed 
          right-0 
          z-20 
          bg-[#101010] 
          bg-opacity-80 
          flex 
          items-center 
          justify-between
        "
      >
          <div class="flex items-center ml-6">
              <button type="button" class="rounded-full bg-black p-[1px] cursor-pointer">
                  <ChevronLeft fillColor="#FFFFFF" :size="30" />
              </button>
              <button type="button" class="rounded-full bg-black p-[1px] hover:bg-[#] ml-4 cursor-pointer">
                  <ChevronRight fillColor="#FFFFFF" :size="30" />
              </button>
          </div>

          <button @click="openMenu = !openMenu" :class="openMenu ? 'bg-[#282828]' : 'bg-black'"
              class="bg-black hover:bg-[#282828] rounded-full p-0.5 mr-8 mt-0.5 cursor-pointer">
              <div class="flex items-center">
                  <img 
                    class="rounded-full" 
                    width="27"
                    src="data:image/jpeg;base64,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"
                  >
                  <div class="text-white text-[14px] ml-1.5 font-semibold">Erick Muriithi</div>
                  <ChevronDown v-if="!openMenu" @click="openMenu = true" fillColor="#FFFFFF" :size="25" />
                  <ChevronUp v-else @click="openMenu = false" fillColor="#FFFFFF" :size="25" />
              </div>
          </button>

          <span v-if="openMenu"
              class="fixed w-[190px] bg-[#282828] shadow-2xl z-50 rounded-sm top-[52px] right-[35px] p-1 cursor-pointer">
              <ul class="text-gray-200 font-semibold text-[14px]">
                  <li class="px-3 py-2.5 hover:bg-[#3E3D3D] border-b border-b-gray-600">Profile</li>
                  <li class="px-3 py-2.5 hover:bg-[#3E3D3D]">Log out</li>
              </ul>
          </span>
      </div>


      <div id="SideNav" class="h-[100%] p-6 w-[240px] fixed z-50 bg-black">
          <RouterLink to="/">
            <img width="125" src="/images/icons/spotify-logo.png">
          </RouterLink>
          <div class="my-8"></div>
          <ul>
              <RouterLink to="/">
                  <MenuItem class="ml-[1px]" :iconSize="23" name= "Home" iconString="home" pageUrl="/" />
              </RouterLink>
              <RouterLink to="/search">
                  <MenuItem class="ml-[1px]" :iconSize="24" name="Search" iconString="search" pageUrl="/search" />
              </RouterLink>
              <RouterLink to="/library">
                  <MenuItem class="ml-[2px]" :iconSize="23" name="Your Library" iconString="library" pageUrl="/library" />
              </RouterLink>
              <div class="py-3.5"></div>
              <MenuItem :iconSize="24" name="Create Playlist" iconString="playlist" pageUrl="/playlist" />
              <MenuItem class="-ml-[1px]" :iconSize="27" name="Liked Songs" iconString="liked" pageUrl="/liked" />
          </ul>
          <div class="border-b border-b-gray-700"></div>
          <ul>
              <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #1</li>
              <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #2</li>
              <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #3</li>
              <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #4</li>
          </ul>
      </div>
  </div>

  <div
      class="
          fixed
          right-0
          top-0
          w-[calc(100%-240px)]
          overflow-auto
          h-full
          bg-gradient-to-b
          from-[#1C1C1C]
          to-black
      "
  >
      <div class="mt-[70px]"></div>
      <RouterView />
      <div class="mb-[100px]"></div>
  </div>

  <MusicPlayer v-if="currentTrack"/>
</template>

