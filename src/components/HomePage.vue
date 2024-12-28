<template>
<div class="main-template">
  <nav class="navbar">
    <div class="navbar__logo">NEOTAILY</div>
    <ul class="navbar__links" :class="{ 'navbar__links--active': isMenuOpen }">
    </ul>
    <button @click="redricttoAdmin()" class="navbar__signup">Factory Reset</button>
    <div class="navbar__toggle" @click="toggleMenu">
      <span :class="{ 'navbar__toggle--open': isMenuOpen }"></span>
      <span :class="{ 'navbar__toggle--open': isMenuOpen }"></span>
      <span :class="{ 'navbar__toggle--open': isMenuOpen }"></span>
      <div v-if="isMenuOpen">toggleMenu</div>
    </div>
  </nav>
  <div class="main-homepage">
    <div class="main-page">
      <div class="sidebar">
        <div class="menu">
          <div v-for="item in menuItems" :key="item.name" class="menu-item">
            <button
              @click="toggleDropdown(item.name)"
              class="menu-button"
              :class="{ active: activeDropdown === item.name }"
            >
              <div class="menu-button-content">
                <component :is="item.icon" class="menu-icon" />
                <span>{{ item.name }}</span>
              </div>
              <svg
                class="dropdown-arrow"
                :class="{ rotated: activeDropdown === item.name }"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
              >
                <path d="M19 9l-7 7-7-7" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
            </button>
            <div
              v-if="activeDropdown === item.name"
              class="dropdown-menu"
            >
              <a
                v-for="subItem in item.items"
                :key="subItem.name"
                @click.prevent="navigateToRoute(subItem.path, subItem.name)"
                href="#"
                class="dropdown-item"
              >
                <component :is="subItem.icon" class="submenu-icon" />
                {{ subItem.name }}
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Main Content -->
      <main class="main-content">
        <div class="content-container">
          <h1 class="heading-main-content">Welcome to Necotaily Software</h1>
          
          <section class="intro-section">
            <h2 class="intero">Streamline Your Business Operations</h2>
            <p>
              Necotaily Software provides comprehensive solutions for managing your business efficiently.
              From employee management to financial analysis, we've got you covered.
            </p>
          </section>

          <div class="features-grid">
            <div class="feature-card">
              <h3>Key Features</h3>
              <ul>
                <li>Complete Employee Management</li>
                <li>Purchase Tracking System</li>
                <li>Digital Khata Management</li>
                <li>Advanced Data Analysis</li>
                <li>Comprehensive Reporting</li>
              </ul>
            </div>

            <div class="feature-card">
              <h3>Benefits</h3>
              <ul>
                <li>Increased Productivity</li>
                <li>Better Financial Control</li>
                <li>Real-time Data Access</li>
                <li>Simplified Operations</li>
                <li>Enhanced Decision Making</li>
              </ul>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>
</div>
</template>

<script setup>
import { useRouter } from "vue-router";
import { ref } from "vue";
import {
  UserGroupIcon,
  ShoppingCartIcon,
  DocumentTextIcon,
  ChartBarIcon,
  DocumentDuplicateIcon,
  UserPlusIcon,
  UserIcon,
  ClockIcon,
  PlusCircleIcon,
  ClipboardDocumentListIcon,
  // ArrowUpTrayIcon,
  // ArrowDownTrayIcon,
  // ArchiveBoxIcon,
  // BuildingStorefrontIcon,
  // BeakerIcon,
  BookOpenIcon,
  // ChartPieIcon,
  // ChartBarSquareIcon,
  BanknotesIcon
} from '@heroicons/vue/24/outline';

const router = useRouter();
const isMenuOpen = ref(false);
const activeDropdown = ref("");

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const menuItems = [
  {
    name: "Attendance",
    icon: ClockIcon,
    items: [
      { name: "Jinning Mistri", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Saplar", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Jharkhand (Labor)", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Bihari Labor", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Packaging", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Munim", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Sr Manager", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Market Manager", icon: UserIcon, path: "/Employee-Attendance" },
      { name: "Driver", icon: UserIcon, path: "/Employee-Attendance" },
    ],
  },
  {
    name: "Employee",
    icon: UserGroupIcon,
    items: [
      { name: "Add Employees", icon: UserPlusIcon, path: "/Add-Employee" },
      { name: "Employee Payroll", icon: BanknotesIcon, path: "/selery-Managment" },
      { name: "Employee Payroll History", icon: DocumentTextIcon, path: "/Departments" },
    ],
  },
  {
    name: "Purchases",
    icon: ShoppingCartIcon,
    items: [
      { name: "+ Mandi Purchase Data", icon: PlusCircleIcon, path: "/Mandi-purchase-form" },
      { name: "+ Direct Purchase Data", icon: PlusCircleIcon, path: "/direct-purchase-Form" },
      { name: "+ Brocker Purchase Data", icon: PlusCircleIcon, path: "/broker-purchase-Form" },
    ],
  },
  {
    name: "Purchase Data",
    icon: DocumentTextIcon,
    items: [
      { name: "Mandi Purchase", icon: ClipboardDocumentListIcon, path: "/Mandi-Purchase-Detail" },
      { name: "Direct Purchase", icon: ClipboardDocumentListIcon, path: "/Driect-Purchase-Detail" },
      { name: "Brocker Purchase", icon: ClipboardDocumentListIcon, path: "/Brocker-Purchase-Detail" },
    ],
  },
  {
    name: "Khata",
    icon: DocumentDuplicateIcon,
    items: [
      { name: "Musterd-Oil KhataBook", icon: BookOpenIcon, path: "/Mustard-Oil-khatabook" },
      { name: "Cutton-Cake KhataBook", icon: BookOpenIcon, path: "/Cotton-Cake-khatabook" },
      { name: "Row of MusterdOil KhataBook", icon: BookOpenIcon, path: "/Row-Of-MustardOil-khatabook" },
      { name: "Row Of CuttonCake KhataBook", icon: BookOpenIcon, path: "/Row-of-cutton-khatabook" },
    ],
  },
  {
    name: "Suspance",
    icon: ChartBarIcon,
    items: [
      { name: "Add Suspance", icon: PlusCircleIcon, path: "/Suspance-form" },
      { name: "Suspance History", icon: DocumentTextIcon, path: "/Suspance-History" },
    ],
  },
  {
    name: "Sell Product",
    icon: ShoppingCartIcon,
    items: [
      { name: "Generate Bill", icon: DocumentTextIcon, path: "/Sell-product-Form" },
      { name: "See Bills", icon: DocumentTextIcon, path: "/Suspance-History" },
    ],
  },
];

const toggleDropdown = (name) => {
  activeDropdown.value = activeDropdown.value === name ? "" : name;
};

const navigateToRoute = (path, name) => {
  console.log("Navigating to:", path, "with name:", name);
  router.push({
    path,
    query: { name },
  });
};

const redricttoAdmin = () => {
  router.push('/Admin');
};
</script>
<style lang="scss" scoped>
/* Variables */
$navbar-bg-color: #1b1b1b;
$navbar-link-color: #319c9c;
$navbar-hover-color: #ffffff;
$navbar-toggle-color: #fff;
$navbar-signup-bg-color: #f9a826;
$navbar-signup-hover-color: darken($navbar-signup-bg-color, 10%);
$breakpoint: 768px;
$font-family: "Inter";




// :root {
//   --bg-primary: #0a0a0a;
//   --bg-secondary: #141414;
//   --bg-tertiary: #1f1f1f;
//   --text-primary: #e6e6e6;
//   --text-secondary: #a0a0a0;
//   --primary-color: #2cbb5d;
//   --primary-hover: #249d4d;
//   --secondary-color: #2d2d2d;
//   --border-color: #2d2d2d;
//   --card-bg: #141414;
//   --danger: #ff4d4f;
//   --success: #2cbb5d;
//   --warning: #ffc107;
// }


:root {
  --primary-color: #8B5CF6;
  --primary-dark: #6D28D9;
  --secondary-color: #1F2937;
  --secondary-dark: #111827;
  --secondary-darkk: #1c2332;
  
  --text-light: #F3F4F6;
  --text-gray: #9CA3AF;
}




.cursor{
  cursor: pointer;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background-color: #1c2332;
  // background-color: white;
  color:#6D28D9 ;
  box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
  font-family: $font-family;

  &__logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: #6D28D9;
  }

  &__links {
    list-style: none;
    display: flex;
    gap: 1.5rem;

    li {
      a {
        color: $navbar-link-color;
        text-decoration: none;
        font-size: 1rem;
        transition: color 0.3s;
        font-weight: 500;

        &:hover {
          color: $navbar-hover-color;
        }
      }
    }

    /* Show links in a vertical stack when active on smaller screens */
    &--active {
      display: block;
    }
  }

  /* Sign Up Button */
  &__signup {
    padding: 0.5rem 1rem;
    background-color: #6D28D9;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s;

    &:hover {
      background-color: #6D28D9;
    }
  }

  /* Toggle Button for Mobile */
  &__toggle {
    display: none;
    cursor: pointer;
    flex-direction: column;
    gap: 0.3rem;

    span {
      display: block;
      width: 25px;
      height: 3px;
      background-color: $navbar-toggle-color;
      transition: transform 0.3s;
    }

    /* Toggle Animation */
    &--open {
      &:nth-child(1) {
        transform: translateY(8px) rotate(45deg);
      }

      &:nth-child(2) {
        opacity: 0;
      }

      &:nth-child(3) {
        transform: translateY(-8px) rotate(-45deg);
      }
    }
  }
}


/* Responsive Styles */
@media (max-width: $breakpoint) {
  .navbar {
    &__links {
      position: absolute;
      top: 100%;
      left: 0;
      right: 0;
      background-color: $navbar-bg-color;
      flex-direction: column;
      align-items: center;
      gap: 1rem;
      padding: 1rem;
      display: none;
    }

    &__links--active {
      display: flex;
    }

    &__signup {
      display: none;
    }

    &__toggle {
      display: flex;
    }
  }
}
.navbar__signup{
  a{
    text-decoration: none;
    color: white;
  }
}

.main-homepage {
  display: flex;
  height: 100vh;
  background-color: #f4f7fc;
  
  color: #333;

  .main-page {
    display: flex;
    width: 100%;
  }

  // .sidebar {
  //   width: 300px;
  //   // background-color: #1f2937;
  //   background-color: var(--secondary-color);
  //   color: #fff;
  //   padding: 1rem;
  //   box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
  //   overflow-y: auto;
  //   margin-top: 1.5rem;
  //   margin-left: 1.5rem;
  //   border-radius: 10px;

  //   .sidebar__menu {
  //     list-style: none;
  //     padding: 0;

  //     .sidebar__item {
  //       margin-bottom: 1rem;

  //       .sidebar__link {
  //         display: flex;
  //         justify-content: space-between;
  //         padding: 0.75rem;
  //         cursor: pointer;
  //         font-weight: 600;
  //         font-size: 1rem;
  //         // color: #fff;
  //         color: var(--text-light);
  //         border-radius: 4px;
  //         transition: background 0.3s;

  //         &:hover {
  //           background-color: rgba(139, 92, 246, 0.1);
           
  //         }

  //         .arrow--down {
  //           transform: rotate(180deg);
  //           transition: transform 0.3s;
  //         }
  //       }

  //       .sidebar__dropdown {
  //         margin-top: 0.5rem;
  //         list-style: none;
  //         padding-left: 1rem;

  //         &.sidebar__dropdown--child {
  //           padding-left: 1.5rem;
  //           // background-color: #f5f5f5;
  //           background-color: rgba(139, 92, 246, 0.1);
  //           border-radius: 4px;
  //         }

  //         li {
  //           padding: 0.5rem;
  //           // background-color: #f5f5f5;
  //           background-color: rgba(139, 92, 246, 0.1);
  //           border-radius: 4px;

  //           a {
  //             color: #000;
  //             text-decoration: none;
  //             transition: color 0.2s;

  //             &:hover {
  //               // color: white;
  //               background-color: rgba(139, 92, 246, 0.1);
  //             }
  //           }

  //           &:hover {
  //             // background-color: #10898d;
  //             background-color: rgba(139, 92, 246, 0.1);
  //             color: var(--text-light);
  //           }
  //         }
  //       }
  //     }
  //   }
  // }
  .sidebar {
  width: 16rem;
  background-color:#1F2937;
  padding: 1rem;
  height: 100vh;
  margin-top: 0px;
}

.menu-item {
  margin-bottom: 0.5rem;
}
.heading-main-content{
  font-size: 2.5rem;
    font-weight: bold;
    color: #6D28D9;
}

.menu-button {
  width: 100%;
  background: none;
  border: none;
  padding: 0.75rem;
  color:#F3F4F6;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  border-radius: 0.5rem;
  transition: background-color 0.2s;
}

.menu-button:hover {
  background-color: rgba(139, 92, 246, 0.1);
}

.menu-button.active {
  background-color: rgba(139, 92, 246, 0.1);
}

.menu-button-content {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.menu-icon, .submenu-icon {
  width: 1.25rem;
  height: 1.25rem;
  color: #8B5CF6;
}

.dropdown-arrow {
  width: 1rem;
  height: 1rem;
  transition: transform 0.2s;
}

.dropdown-arrow.rotated {
  transform: rotate(180deg);
}

.dropdown-menu {
  margin-top: 0.5rem;
  padding-left: 3rem;
}

.dropdown-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.5rem 0.75rem;
  color: #9CA3AF;
  text-decoration: none;
  border-radius: 0.5rem;
  transition: background-color 0.2s;
}

.dropdown-item:hover {
  background-color: rgba(139, 92, 246, 0.1);
  color: #F3F4F6;
}

.main-content{
  background-color: #111827
}
  .content-area {
    flex: 1;
    padding: 1.5rem;

    // .main-content {
    //   display: flex;
    //   // justify-content: center;
    //   flex-direction: column;
    //   align-items: center;
    //   background: #ffffff;
    
    //   border-radius: 8px;
    //   box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
    //   height: 97vh;

    //   .img-part {
    //     width: 100%;

    //     .img-render {
    //       display: flex;
    //       // gap: 5rem;
    //       justify-content: space-around;
    //       margin-top: 6px;
    //       // background-color: #10898d;

    //       .center {

    //         display: flex;
    //         flex-direction: column;
    //         align-items: center;
    //         gap: 2rem;
    //         width: fit-content;

    //         .image {
    //           border-radius: 50%;
    //           box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
    //           transition: transform 0.3s;

    //           &:hover {
    //             transform: scale(1.05);
    //           }
    //         }

    //         .grandfather {
    //           height: 200px;
    //           width: 200px;
    //           object-fit: cover;
    //         }

    //         .father {
    //           height: 200px;
    //           width: 200px;
    //           object-fit: cover;
    //         }

    //         .son {
    //           height: 200px;
    //           width: 200px;
    //           object-fit: cover;
    //         }
    //       }
    //     }
    //   }

    //   .main-about-content {
    //     margin-top: 18px;
    //     padding: 20px;
    //   }
    // }
    

.content-container {
  background-color: var(--secondary-color);
  padding: 2rem;
  border-radius: 0.5rem;
}

h1 {
  font-size: 2.5rem;
  color: var(--primary-color);
  margin-bottom: 1.5rem;
}

.intro-section {
  margin-bottom: 2rem;

}

h2 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: white;
}

.intero{
  color: white !important;
}
p {
  color: var(--text-gray);
  line-height: 1.6;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.feature-card {
  background-color: var(--secondary-dark);
  padding: 1.5rem;
  border-radius: 0.5rem;
  border: 1px solid rgba(139, 92, 246, 0.2);
}

.feature-card h3 {
  color: var(--primary-color);
  font-size: 1.25rem;
  margin-bottom: 1rem;
}

.feature-card ul {
  list-style: none;
}

.feature-card li {
  color: var(--text-gray);
  margin-bottom: 0.5rem;
  padding-left: 1.5rem;
  position: relative;
}

.feature-card li::before {
  content: "•";
  color: var(--primary-color);
  position: absolute;
  left: 0;
}


  }
}
.intero{
  color: white !important;
}
</style>
