<template>
  <div>
    <nav class="navbar">
      <div class="navbar__logo">Shri Vinayk</div>
      <ul
        class="navbar__links"
        :class="{ 'navbar__links--active': isMenuOpen }"
      >
        <!-- <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#contact">Contact</a></li> -->
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
        <aside class="sidebar">
          <ul class="sidebar__menu">
            <!-- Sidebar Menu -->
            <li
              class="sidebar__item cursor"
              v-for="(label, key) in sidebarItems"
              :key="key"

            >
              <div class="sidebar__link" @click="toggleDropdown(key)">
                {{ label.title }}
                <span :class="{ 'arrow--down': dropdowns[key] }">▼</span>
              </div>
              <ul v-show="dropdowns[key]" class="sidebar__dropdown">
                <li v-for="(subItem, subKey) in label.subItems" :key="subKey">
                  <template v-if="subItem.hasDropdown">
                    <div
                      class="sidebar__link"
                      @click.stop="toggleDropdown(subItem.key)"
                    >
                      <!-- <a
                   
                       @click.prevent="navigateToRoute(subItem.name)"
                      >
                        {{ subItem.name }}
                      </a> -->
                      <a
                @click.prevent="navigateToRoute(subItem.link, subItem.name)"
              >
                {{ subItem.name }}
              </a>
                      <span :class="{ 'arrow--down': dropdowns[subItem.key] }"
                        >▼</span
                      >
                    </div>
                    <ul
                      v-show="dropdowns[subItem.key]"
                      class="sidebar__dropdown sidebar__dropdown--child"
                    >
                      <li
                        v-for="(childItem, childKey) in subItem.childItems"
                        :key="childKey"
                      >
                        <!-- <a :href="childItem.link"     @click.prevent="navigateToRoute(childItem.name)">{{ childItem.name }}</a> -->
                        <a
                    @click.prevent="navigateToRoute(childItem.link, childItem.name)"
                  >
                    {{ childItem.name }}
                  </a>
                    </li>
                    </ul>
                  </template>
                  <template v-else>
                    <!-- <a  @click.prevent="navigateToRoute(subItem.name)" :href="subItem.link">{{ subItem.name }} </a>
                  -->
                  <a
                @click.prevent="navigateToRoute(subItem.link, subItem.name)"
              >
                {{ subItem.name }}
              </a>
                  </template>
                </li>
              </ul>
            </li>
          </ul>
        </aside>
        <main class="content-area">
          <div class="main-content">
            <div class="img-part">
              <div class="img-render">
                <div class="center">
                  <img
                    class="image grandfather"
                    src="../assets/grandfather.jpg"
                    alt="Grandfather"
                  />
                
                </div>
                <div class="center">
                  <img
                    class="image father"
                    src="../assets/father.jpg"
                    alt="Father"
                  />
                
                </div>
                <div class="center">
                  <img class="image son" src="../assets/son.jpg" alt="Son" />
                 
                </div>
              </div>
            </div>
            <div class="main-about-content">
              Lorem ipsum dolor sit amet. Est enim ipsam est quod earum qui unde
              obcaecati ad adipisci quam. Est ratione voluptate aut odit dolores
              qui nisi earum. Est tempora fuga eum eligendi magni ut dolores
              quidem nam dolores dolores sit nobis voluptatem. Ut nobis
              necessitatibus aut velit rerum est molestiae molestiae ea
              assumenda molestias eum nihil recusandae aut veritatis recusandae.
              Est vero cumque et alias enim est ratione adipisci ut aperiam
              tempora et quia alias eos doloremque iste est commodi dolores! Ea
              placeat odit ex deserunt repellendus id voluptas beatae aut
              recusandae dolore ad saepe corporis qui explicabo error aut
              possimus architecto. At accusamus molestiae 33 rerum itaque nam
              quidem voluptas sed voluptas ipsam cum aperiam dolorum. Aut iure
              distinctio non odio nihil At tempora rerum qui architecto tempore
              est rerum illo.
            </div>
           
          </div>
        </main>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

// const navigateToRoute = (name) => {
//   console.log("Navigating to:", name);
 
//   router.push({
//     path: "/Employee-Attendance", 
//     query: { name },
//   });
// };

const navigateToRoute = (path, name) => {
  console.log("Navigating to:", path, "with name:", name);
  router.push({
    path,
    query: { name },
  });
};
const redricttoAdmin = ()=>{
  router.push('/Landing-Page')
}

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const dropdowns = ref({
  attendence: false,
  employee: false,
  purchases: false,
  khata: false,
  sales: false,
  anlysis: false,
  salary: false, // Added for the "Basic Salary" dropdown
});

const sidebarItems = {
  attendence: {
    title: "Attendance",
    subItems: [
      { name: "Jinning Mistri", link: "/Employee-Attendance" },
      { name: "Saplar",link: "/Employee-Attendance" },
      { name: "Jharkhand (Labor)",link: "/Employee-Attendance" },
      { name: "Bihari Labor",link: "/Employee-Attendance" },
      { name: "Packaging",link: "/Employee-Attendance" },
      { name: "Munim",link: "/Employee-Attendance" },
      { name: "Sr Manager",link: "/Employee-Attendance" },
      { name: "Market Manager",link: "/Employee-Attendance" },
      { name: "Driver",link: "/Employee-Attendance" },
    ],
  },
  employee: {
    title: "Employee",
    subItems: [
      { name: "Add Employees", link: "/Add-Employee" },
      { name: "Employee Payroll ", link: "/selery-Managment" },
      { name: "Employee Payroll History", link: "/Departments" },


    ],
  },
  purchases: {
    title: "Purchases",
    subItems: [
      { name: "+ Mandi Purchase Data", link: "/Mandi-purchase-form" },
      { name: "+ Direct Purchase Data", link: "/direct-purchase-Form" },
      { name: "+ Brocker Purchase Data", link: "/broker-purchase-Form" },
    ],
  },
  //done
  sales: {
    title: "Purchase Data",
    subItems: [
    { name: " Mandi Purchase", link: "/Mandi-Purchase-Detail" },
      { name: "Direct Purchase ", link: "/Driect-Purchase-Detail" },
      { name: "Brocker Purchase ", link: "/Brocker-Purchase-Detail" },
    ],
  }, 
  //done
  khata: {
    title: "Khata",
    subItems: [
      { name: "Musterd-Oil KhataBook", link: "/Mustard-Oil-khatabook" },
      { name: "Cutton-Cake KhataBook", link: "/Cotton-Cake-khatabook" },
      { name: "Row of MusterdOil KhataBook", link: "/Row-Of-MustardOil-khatabook" },
      { name: "Row Of CuttonCake KhataBook", link: "/Row-of-cutton-khatabook" },
    ],
  },
  //we have to make suspance page 
  anlysis: {
    title: "Suspance",
    subItems: [
      { name: "Add Suspance", link: "/Suspance-form" },
      { name: "Suspance History", link: "/Suspance-History" },
     
     
    ],
  },
  sell_product: {
    title: "Sell Product",
    subItems: [
      { name: "Generate Bill", link: "/Sell-product-Form" },
      { name: "See Biils", link: "/Suspance-History" },
     
     
    ],
  },
};

const toggleDropdown = (dropdown) => {
  dropdowns.value[dropdown] = !dropdowns.value[dropdown];
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

.cursor{
  cursor: pointer;
}
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background-color: $navbar-bg-color;
  // background-color: white;
  color: $navbar-link-color;
  box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
  font-family: $font-family;

  &__logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: $navbar-link-color;
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
    background-color: $navbar-signup-bg-color;
    color: $navbar-bg-color;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s;

    &:hover {
      background-color: $navbar-signup-hover-color;
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

  .sidebar {
    width: 300px;
    // background-color: #1f2937;
    background-color: #ffffff;
    color: #fff;
    padding: 1rem;
    box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
    overflow-y: auto;
    margin-top: 1.5rem;
    margin-left: 1.5rem;
    border-radius: 10px;

    .sidebar__menu {
      list-style: none;
      padding: 0;

      .sidebar__item {
        margin-bottom: 1rem;

        .sidebar__link {
          display: flex;
          justify-content: space-between;
          padding: 0.75rem;
          cursor: pointer;
          font-weight: 600;
          font-size: 1rem;
          // color: #fff;
          color: #000;
          border-radius: 4px;
          transition: background 0.3s;

          &:hover {
            background-color: #374151;
            color: #ffff;
          }

          .arrow--down {
            transform: rotate(180deg);
            transition: transform 0.3s;
          }
        }

        .sidebar__dropdown {
          margin-top: 0.5rem;
          list-style: none;
          padding-left: 1rem;

          &.sidebar__dropdown--child {
            padding-left: 1.5rem;
            background-color: #f5f5f5;
            border-radius: 4px;
          }

          li {
            padding: 0.5rem;
            background-color: #f5f5f5;
            border-radius: 4px;

            a {
              color: #000;
              text-decoration: none;
              transition: color 0.2s;

              &:hover {
                color: white;
              }
            }

            &:hover {
              background-color: #10898d;
            }
          }
        }
      }
    }
  }

  .content-area {
    flex: 1;
    padding: 1.5rem;

    .main-content {
      display: flex;
      // justify-content: center;
      flex-direction: column;
      align-items: center;
      background: #ffffff;
    
      border-radius: 8px;
      box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
      height: 97vh;

      .img-part {
        width: 100%;

        .img-render {
          display: flex;
          // gap: 5rem;
          justify-content: space-around;
          margin-top: 6px;
          // background-color: #10898d;

          .center {

            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2rem;
            width: fit-content;

            .image {
              border-radius: 50%;
              box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
              transition: transform 0.3s;

              &:hover {
                transform: scale(1.05);
              }
            }

            .grandfather {
              height: 200px;
              width: 200px;
              object-fit: cover;
            }

            .father {
              height: 200px;
              width: 200px;
              object-fit: cover;
            }

            .son {
              height: 200px;
              width: 200px;
              object-fit: cover;
            }
          }
        }
      }

      .main-about-content {
        margin-top: 18px;
        padding: 20px;
      }
    }
  }
}
</style>
