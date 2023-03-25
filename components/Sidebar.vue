<template>
  <!-- Sidebar -->
  <div
    class="hidden lg:block fixed lg:max-w-[295px] w-full overflow-y-auto h-full bg-white z-[999]"
    id="sidebarHRIS"
  >
    <div class="px-6 py-[50px] gap-y-[50px] flex flex-col">
      <div class="flex items-center justify-between">
        <a href="#" class="flex justify-center">
          <img src="/assets/svgs/logo-type.svg" alt="" />
        </a>
        <a href="#" id="toggleCloseSidebar" class="lg:hidden">
          <svg
            class="w-6 h-6 text-dark"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            ></path>
          </svg>
        </a>
      </div>
      <div class="flex flex-col gap-4">
        <div class="text-sm text-grey">Daily Use</div>
        <NuxtLink
          :to="{ name: 'companies-id' }"
          class="nav-link"
          exact>
          <img src="/assets/svgs/ic-grid.svg" alt="" />
          Overview
        </NuxtLink>
        <NuxtLink
          :to="{ name: 'companies-id-employee' }"
          class="nav-link"
          exact>
          <img src="/assets/svgs/ic-users.svg" alt="" />
          Employees
        </NuxtLink>
        <NuxtLink :to="{ name: 'companies-id-teams' }" class="nav-link">
          <img src="/assets/svgs/ic-briefcase.svg" alt="" />
          My Teams
        </NuxtLink>
        <NuxtLink :to="{ name: 'companies-id-roles' }" class="nav-link">
          <img src="/assets/svgs/ic-flag.svg" alt="" />
          Roles
        </NuxtLink>
      </div>
      <div class="flex flex-col gap-4">
        <div class="text-sm text-grey">Others</div>
        <a href="#" class="nav-link">
          <img src="/assets/svgs/ic-box.svg" alt="" />
          Insurances
        </a>
        <a href="#" class="nav-link">
          <img src="/assets/svgs/ic-home.svg" alt="" />
          Company
        </a>
        <a href="#" class="nav-link">
          <img src="/assets/svgs/ic-gift.svg" alt="" />
          Rewards
        </a>
        <a href="#" class="nav-link">
          <img src="/assets/svgs/ic-settings.svg" alt="" />
          Settings
        </a>
        <button @click="$auth.logout()" class="nav-link">
          <img src="/assets/svgs/ic-signout.svg" alt="" />
          Logout
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  auth: false,

  
}
</script>

<style scoped>
.nuxt-link-active {
    font-weight: bold;
}

.nuxt-link-exact-active {
    font-weight: bold;
    align-items: center;
    background-color: rgb(70, 64, 222);
    border-bottom-color: rgb(229, 231, 235);
    border-bottom-left-radius: 16px;
    border-bottom-right-radius: 16px;
    border-bottom-style: solid;
    border-bottom-width: 0px;
    border-left-color: rgb(229, 231, 235);
    border-left-style: solid;
    border-left-width: 0px;
    border-right-color: rgb(229, 231, 235);
    border-right-style: solid;
    border-right-width: 0px;
    border-top-color: rgb(229, 231, 235);
    border-top-left-radius: 16px;
    border-top-right-radius: 16px;
    border-top-style: solid;
    border-top-width: 0px;
    box-sizing: border-box;
    color: rgb(255, 255, 255);
    column-gap: 16px;
    display: flex;
    font-family: Poppins, sans-serif;
    font-feature-settings: normal;
    font-weight: 600;
    line-height: 24px;
    padding-bottom: 11px;
    padding-left: 11px;
    padding-right: 11px;
    padding-top: 11px;
    row-gap: 16px;
    tab-size: 4;
    text-decoration-color: rgb(255, 255, 255);
    text-decoration-line: none;
    text-decoration-style: solid;
    
}

</style>