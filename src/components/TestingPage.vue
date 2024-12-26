<script setup >
import { ref } from 'vue';
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
  UserGroupIcon as SuppliersIcon,
  ArrowUpTrayIcon,
  ArrowDownTrayIcon,
  ArchiveBoxIcon,
  BuildingStorefrontIcon,
  BeakerIcon,
  BookOpenIcon,
  ChartPieIcon,
  ChartBarSquareIcon,
  BanknotesIcon
} from '@heroicons/vue/24/outline';

const activeDropdown = ref('');

const menuItems = [
  {
    name: 'Employ',
    icon: UserGroupIcon,
    items: [
      { name: 'Add Employee', icon: UserPlusIcon },
      { name: 'Employee List', icon: UserIcon },
      { name: 'Attendance', icon: ClockIcon }
    ]
  },
  {
    name: 'Purchase',
    icon: ShoppingCartIcon,
    items: [
      { name: 'New Purchase', icon: PlusCircleIcon },
      { name: 'Purchase History', icon: ClipboardDocumentListIcon },
      { name: 'Suppliers', icon: SuppliersIcon }
    ]
  },
  {
    name: 'Data',
    icon: DocumentTextIcon,
    items: [
      { name: 'Import Data', icon: ArrowUpTrayIcon },
      { name: 'Export Data', icon: ArrowDownTrayIcon },
      { name: 'Backup', icon: ArchiveBoxIcon }
    ]
  },
  {
    name: 'Khatas',
    icon: DocumentDuplicateIcon,
    items: [
      { name: 'Mandi Khata', icon: BuildingStorefrontIcon },
      { name: 'Mustard Oil Khata', icon: BeakerIcon },
      { name: 'Daily Khata', icon: BookOpenIcon }
    ]
  },
  {
    name: 'Analysis',
    icon: ChartBarIcon,
    items: [
      { name: 'Sales Report', icon: ChartPieIcon },
      { name: 'Inventory Report', icon: ChartBarSquareIcon },
      { name: 'Financial Report', icon: BanknotesIcon }
    ]
  }
];

const toggleDropdown = (name) => {
  activeDropdown.value = activeDropdown.value === name ? '' : name;
};

const handleFactoryReset = () => {
  console.log('Factory Reset triggered');
};
</script>

<template>
  <div class="app">
    <!-- Navbar -->
    <nav class="navbar">
      <div class="navbar-content">
        <div class="logo">Necotaily Software</div>
        <button class="reset-button" @click="handleFactoryReset">
          Factory Reset
        </button>
      </div>
    </nav>

    <div class="main-container">
      <!-- Sidebar -->
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
          <h1>Welcome to Necotaily Software</h1>
          
          <section class="intro-section">
            <h2>Streamline Your Business Operations</h2>
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

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-content">
        <div class="footer-info">
          <h3>Necotaily Software</h3>
          <p>Streamlining Your Business Operations</p>
        </div>
        <div class="footer-copyright">
          © {{ new Date().getFullYear() }} Necotaily Software. All rights reserved.
        </div>
      </div>
    </footer>
  </div>
</template>

<style>
:root {
  --primary-color: #8B5CF6;
  --primary-dark: #6D28D9;
  --secondary-color: #1F2937;
  --secondary-dark: #111827;
  --text-light: #F3F4F6;
  --text-gray: #9CA3AF;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  background-color: var(--secondary-dark);
  color: var(--text-light);
  min-height: 100vh;
}

.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

/* Navbar styles */
.navbar {
  background-color: var(--secondary-dark);
  padding: 1rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.navbar-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: var(--primary-color);
}

.reset-button {
  background-color: var(--primary-color);
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: background-color 0.2s;
}

.reset-button:hover {
  background-color: var(--primary-dark);
}

/* Main container styles */
.main-container {
  display: flex;
  flex: 1;
  flex-direction: row;
 
}

/* Sidebar styles */
.sidebar {
  width: 16rem;
  background-color: var(--secondary-color);
  padding: 1rem;
  height: 100vh;
  margin-top: 0px;
}

.menu-item {
  margin-bottom: 0.5rem;
}

.menu-button {
  width: 100%;
  background: none;
  border: none;
  padding: 0.75rem;
  color: var(--text-light);
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
  color: var(--primary-color);
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
  color: var(--text-gray);
  text-decoration: none;
  border-radius: 0.5rem;
  transition: background-color 0.2s;
}

.dropdown-item:hover {
  background-color: rgba(139, 92, 246, 0.1);
  color: var(--text-light);
}

/* Main content styles */
.main-content {
  flex: 1;
  padding: 2rem;
}

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

/* Footer styles */
.footer {
  background-color: var(--secondary-dark);
  padding: 1.5rem;
  margin-top: auto;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 1rem;
}

@media (min-width: 768px) {
  .footer-content {
    flex-direction: row;
    justify-content: space-between;
    text-align: left;
  }
}

.footer-info h3 {
  color: var(--primary-color);
  font-size: 1.125rem;
  margin-bottom: 0.25rem;
}

.footer-info p {
  font-size: 0.875rem;
}

.footer-copyright {
  color: var(--text-gray);
  font-size: 0.875rem;
}
</style>