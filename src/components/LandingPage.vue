<template>
    <div class="mainconatainer">








        <nav class="navbar">
    <div class="container">
      <div class="navbar-content">
        <!-- Logo -->
        <div class="logo">NEOTAILY</div>

        <!-- Desktop Navigation -->
        <div class="desktop-nav">
          <a href="#features" class="nav-link">Features</a>
          <a href="#pricing" class="nav-link">Pricing</a>
          <a href="#about" class="nav-link">About</a>
          <!-- <button class="btn sign-in">Sign In</button> -->
          <button class="btn get-started">Get Started</button>
        </div>

        <!-- Mobile Menu Button -->
        <div class="mobile-menu-btn" @click="toggleMenu">
          <span>{{ isMenuOpen ? 'Close' : 'Menu' }}</span>
        </div>
      </div>

      <!-- Mobile Navigation -->
      <div v-if="isMenuOpen" class="mobile-nav">
        <a href="#features" class="nav-link">Features</a>
        <a href="#pricing" class="nav-link">Pricing</a>
        <a href="#about" class="nav-link">About</a>
        <button class="btn sign-in">Sign In</button>
        <button class="btn get-started">Get Started</button>
      </div>
    </div>
  </nav>



  <section class="hero">
    <div class="overlay"></div>
    <div class="container">
      <div class="content">
        <h1 class="headingg">Transform Your Business with Our Software</h1>
        <p class="subheading">
          Powerful, flexible, and easy to use. Our software helps you streamline your operations and boost productivity.
        </p>
        <div class="buttons">
          <button class="btn primary" @click="handleGetStarted">
            Get Started <span class="arrow">→</span>
          </button>
          <button class="btn outline">Watch Demo</button>
        </div>
      </div>
    </div>
  </section>




      <section id="features" class="section-features">
        <div class="container">
          <div class="text-center mb-16">
            <h2 class="title">Powerful Features</h2>
            <p class="description">
              Everything you need to streamline your workflow and boost productivity
            </p>
          </div>
          <div class="features-grid">
            <div
              v-for="(feature, index) in features"
              :key="index"
              class="feature-card"
            >
              <div class="icon">
                <component :is="feature.icon" class="icon-size" />
              </div>
              <h3 class="feature-title">{{ feature.title }}</h3>
              <p class="feature-description">{{ feature.description }}</p>
            </div>
          </div>
        </div>
      </section>
  
      <section class="section-steps">
        <div class="container">
          <div class="text-center mb-16">
            <h2 class="title">How It Works</h2>
            <p class="description">
              Get started in minutes with our simple four-step process
            </p>
          </div>
          <div class="steps-grid">
            <div v-for="(step, index) in steps" :key="index" class="step-card">
              <div class="step-content">
                <span class="step-number">{{ step.number }}</span>
                <h3 class="step-title">{{ step.title }}</h3>
                <p class="step-description">{{ step.description }}</p>
              </div>
              <ArrowRight
                v-if="index < steps.length - 1"
                class="step-arrow"
              />
            </div>
          </div>
        </div>
      </section>
  
      <section id="pricing" class="section-pricing">
        <div class="container">
          <div class="text-center mb-16">
            <h2 class="title">Simple, Transparent Pricing</h2>
            <p class="description">
              Choose the perfect plan for your business needs
            </p>
          </div>
          <div class="pricing-grid">
            <div
              v-for="(plan, index) in plans"
              :key="index"
              class="pricing-card"
              :class="{
                'popular-plan': plan.popular,
                'regular-plan': !plan.popular
              }"
            >
              <span v-if="plan.popular" class="popular-tag">
                Most Popular
              </span>
              <h3 class="plan-name">{{ plan.name }}</h3>
              <div class="plan-price">
                <span class="price">{{ plan.price }}</span>
                <span v-if="plan.price !== 'Custom'" class="per-year">/Year</span>
              </div>
              <p class="plan-description">{{ plan.description }}</p>
              <ul class="plan-features">
                <li v-for="(feature, featureIndex) in plan.features" :key="featureIndex" class="feature-item">
                  <Check class="check-icon" />
                  <span>{{ feature }}</span>
                </li>
              </ul>
              <button class="get-started-button">
                Get Started
              </button>
            </div>
          </div>
        </div>
      </section>


      <section class="testimonials-section">
    <div class="container">
      <div class="text-center mb-16">
        <h2 class="heading">What Our Clients Say</h2>
        <p class="subheading">
          Don't just take our word for it - hear from some of our satisfied customers
        </p>
      </div>
      <div class="testimonials-grid">
        <div
          v-for="(testimonial, index) in testimonials"
          :key="index"
          class="testimonial-card"
        >
          <div class="testimonial-header">
            <img
              :src="testimonial.image"
              :alt="testimonial.name"
              class="testimonial-image"
            />
            <div>
              <h4 class="testimonial-name">{{ testimonial.name }}</h4>
              <p class="testimonial-role">{{ testimonial.role }}</p>
            </div>
          </div>
          <div class="testimonial-rating">
            <span
              v-for="n in testimonial.rating"
              :key="n"
              class="star"
            >&#9733;</span>
          </div>
          <p class="testimonial-content">{{ testimonial.content }}</p>
        </div>
      </div>
    </div>
  </section>













      <footer class="footer">
    <div class="container">
      <div class="grid">
        <!-- Company Info -->
        <div>
          <h3 class="logo">SoftwareX</h3>
          <p class="description">Transforming businesses with powerful software solutions.</p>
          <div class="social-icons">
            <a href="#" class="icon">Facebook</a>
            <a href="#" class="icon">Twitter</a>
            <a href="#" class="icon">Instagram</a>
            <a href="#" class="icon">LinkedIn</a>
            <a href="#" class="icon">GitHub</a>
          </div>
        </div>

        <!-- Quick Links -->
        <div>
          <h4 class="heading">Quick Links</h4>
          <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">About Us</a></li>
            <li><a href="#">Features</a></li>
            <li><a href="#">Pricing</a></li>
          </ul>
        </div>

        <!-- Support -->
        <div>
          <h4 class="heading">Support</h4>
          <ul>
            <li><a href="#">Help Center</a></li>
            <li><a href="#">Documentation</a></li>
            <li><a href="#">API Reference</a></li>
            <li><a href="#">Contact Us</a></li>
          </ul>
        </div>

        <!-- Legal -->
        <div>
          <h4 class="heading">Legal</h4>
          <ul>
            <li><a href="#">Privacy Policy</a></li>
            <li><a href="#">Terms of Service</a></li>
            <li><a href="#">Cookie Policy</a></li>
            <li><a href="#">Security</a></li>
          </ul>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} SoftwareX. All rights reserved.</p>
      </div>
    </div>
  </footer>
    </div>
  </template>
  
  
  <script setup>
  import { Zap, Shield, Code2, Settings2, ArrowRight, Check, } from "lucide-vue-next";
  
  const features = [
    {
      icon: Zap,
      title: "Lightning Fast",
      description: "Experience blazing-fast performance with our optimized software architecture."
    },
    {
      icon: Shield,
      title: "Secure by Design",
      description: "Enterprise-grade security with end-to-end encryption and compliance features."
    },
    {
      icon: Code2,
      title: "Developer Friendly",
      description: "Extensive API documentation and SDKs for seamless integration."
    },
    {
      icon: Settings2,
      title: "Customizable",
      description: "Tailor the software to your needs with powerful customization options."
    }
  ];
  
  const steps = [
    { number: "01", title: "Sign Up", description: "Create your account in minutes with our simple onboarding process." },
    { number: "02", title: "Configure", description: "Customize the software settings according to your business needs." },
    { number: "03", title: "Integrate", description: "Connect with your existing tools and start importing your data." },
    { number: "04", title: "Launch", description: "Go live with your new streamlined workflow and boost productivity." }
  ];
  
  const plans = [
    {
      name: "Starter",
      price: "\u20B9 400",
      description: "Perfect for small teams",
      features: ["Up to 5 team members", "Basic analytics", "24/7 support", "API access"]
    },
    {
      name: "Pro",
      price: "\u20B9 700",
      description: "Best for growing businesses",
      features: [
        "Unlimited team members",
        "Advanced analytics",
        "Priority support",
        "Custom integrations",
        "Advanced security"
      ],
      popular: true
    },
    {
      name: "Enterprise",
      price: "Custom",
      description: "For large organizations",
      features: [
        "Unlimited everything",
        "Custom development",
        "Dedicated support",
        "SLA guarantee",
        "On-premise option"
      ]
    }
  ];
  
  const testimonials = [
    {
      name: "Sarah Johnson",
      role: "CEO at TechCorp",
      content: "This software has completely transformed how we operate. The productivity gains have been remarkable.",
      rating: 5,
      image: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=400&h=400&fit=crop"
    },
    {
      name: "Michael Chen",
      role: "CTO at StartupX",
      content: "The best decision we made was switching to this platform. The customization options are endless.",
      rating: 5,
      image: "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=400&h=400&fit=crop"
    },
    {
      name: "Emily Davis",
      role: "Operations Director",
      content: "Outstanding support team and feature-rich platform. It's everything we needed and more.",
      rating: 5,
      image: "https://images.unsplash.com/photo-1438761681033-6461ffad8d80?w=400&h=400&fit=crop"
    }
  ];
  </script>
<style>
/* General Container */
.mainconatainer{
    background: black;
    color: white;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}




.testimonials-section {
  padding: 5rem 0;
  background-color: rgba(128, 0, 128, 0.1); /* Purple background */
}

.container {
  width: 80%;
  margin: 0 auto;
}

.text-center {
  text-align: center;
}

.heading {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.subheading {
  color: #888;
  max-width: 800px;
  margin: 0 auto;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 2rem;
}

.testimonial-card {
  padding: 1.5rem;
  background-color: rgba(0, 0, 0, 0.5);
  border: 1px solid rgba(128, 0, 128, 0.2); /* Purple border */
  border-radius: 0.5rem;
}

.testimonial-header {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.testimonial-image {
  width: 3rem;
  height: 3rem;
  border-radius: 50%;
  margin-right: 1rem;
}

.testimonial-name {
  font-weight: 600;
}

.testimonial-role {
  font-size: 0.875rem;
  color: #888;
}

.testimonial-rating {
  margin-bottom: 1rem;
}

.star {
  color: #800080;
  font-size: 1.25rem;
}

.testimonial-content {
  color: #ddd;
  font-size: 1rem;
}

.hero {
  position: relative;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom right, rgba(78, 0, 128, 0.2), rgba(0, 0, 0, 1));
  z-index: 0;
}

.container {
  position: relative;
  z-index: 10;
  text-align: center;
}

.headingg {
  font-size: 3.75rem; /* 60px */
  font-weight: bold;
  margin-bottom: 1.5rem;
  background: linear-gradient(to right, #9b4de1, #7b5add);
  -webkit-background-clip: text;
  color: transparent;
}

.subheading {
  font-size: 1.25rem; /* 20px */
  color: #d1d5db; /* Gray-300 */
  margin-bottom: 2rem;
  max-width: 42rem;
  margin-left: auto;
  margin-right: auto;
}

.buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.btn {
  padding: 0.75rem 1.5rem;
  font-size: 1.125rem; /* 18px */
  font-weight: 600;
  border-radius: 0.375rem; /* 6px */
  display: inline-flex;
  align-items: center;
}

.primary {
  background-color: #6b4bce;
  color: white;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.primary:hover {
  background-color: #5a3fa7;
}

.outline {
  background-color: transparent;
  border: 2px solid #6b4bce;
  color: #6b4bce;
  cursor: pointer;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.outline:hover {
  background-color: #6b4bce;
  color: white;
}

.arrow {
  margin-left: 0.5rem;
  font-size: 1.25rem;
}

/* Section Styles */
section {
  padding-top: 80px;
  padding-bottom: 80px;
 
}

#features {
  background-color: #000000;
}

#pricing {
  background-color: rgb(1, 1, 1);
  
}

.section-steps {
  background-color: #000000;
}

.text-center {
  text-align: center;
}

.mb-16 {
  margin-bottom: 4rem;
}

/* Title Styles */
.title {
  font-size: 2.25rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.description {
  color: #a0aec0;
  max-width: 700px;
  margin: 0 auto;
  font-size: 1rem;
}

/* Grid Styles */
.features-grid, .steps-grid, .pricing-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
}



.footer {
  background-color: #000;
  color: #fff;
  padding: 40px 0;
  border-top: 1px solid rgba(128, 0, 128, 0.2);
}

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 40px;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  background: linear-gradient(to right, #9b4dca, #9a1de0);
  background-clip: text;
  color: transparent;
}

.description {
  color: #ccc;
}

.social-icons {
  display: flex;
  gap: 10px;
}

.icon {
  color: #ccc;
  text-decoration: none;
  font-size: 14px;
}

.icon:hover {
  color: #9b4dca;
}

.heading {
  font-size: 18px;
  font-weight: bold;
}

ul {
  list-style: none;
  padding: 0;
}

ul li {
  margin-bottom: 10px;
}

ul li a {
  color: #ccc;
  text-decoration: none;
}

ul li a:hover {
  color: #9b4dca;
}

.footer-bottom {
  text-align: center;
  margin-top: 20px;
}



@media(min-width: 768px) {
  .features-grid, .steps-grid, .pricing-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media(min-width: 1024px) {
  .features-grid, .steps-grid {
    grid-template-columns: repeat(4, 1fr);
  }
  .pricing-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Feature Card Styles */
.feature-card {
  padding: 1.5rem;
  border-radius: 0.375rem;
  border: 1px solid rgba(128, 90, 236, 0.2);
  transition: border-color 0.3s;
}

.feature-card:hover {
  border-color: rgba(128, 90, 236, 0.4);
}

.icon-size {
  width: 3rem;
  height: 3rem;
  color: #805ad5;
}

.feature-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.feature-description {
  color: #a0aec0;
}

/* Step Styles */
.step-card {
  position: relative;
}

.step-content {
  padding: 1.5rem;
  background-color: rgba(0, 0, 0, 0.5);
  border: 1px solid rgba(128, 90, 236, 0.2);
  border-radius: 0.375rem;
}

.step-number {
  font-size: 2.25rem;
  font-weight: 700;
  color: #805ad5;
  margin-bottom: 1rem;
}

.step-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.step-description {
  color: #a0aec0;
}

.step-arrow {
  position: absolute;
  top: 50%;
  right: -1rem;
  transform: translateY(-50%);
  color: #805ad5;
}

/* Pricing Card Styles */
.pricing-card {
  padding: 2rem;
  border: 1px solid rgba(128, 90, 236, 0.2);
  border-radius: 0.375rem;
}

.popular-plan {
  background-color: rgba(128, 90, 236, 0.1);
  border-color: #805ad5;
}

.regular-plan {
  border-color: rgba(128, 90, 236, 0.2);
}

.popular-tag {
  background-color: #805ad5;
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 1rem;
  font-size: 0.875rem;
  margin-bottom: 1rem;
  display: inline-block;
}

.plan-name {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.plan-price .price {
  font-size: 2.25rem;
  font-weight: 700;
}

.plan-price .per-year {
  color: #a0aec0;
}

.plan-description {
  color: #a0aec0;
  margin-bottom: 1.5rem;
}

.plan-features {
  list-style-type: none;
  padding-left: 0;
}

.feature-item {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.check-icon {
  width: 1.25rem;
  height: 1.25rem;
  color: #805ad5;
  margin-right: 0.5rem;
}

.get-started-button {
  width: 100%;
  background-color: #805ad5;
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 0.375rem;
  font-weight: 600;
  text-align: center;
  transition: background-color 0.3s;
}

.get-started-button:hover {
  background-color: #6b46c1;
}








.navbar {
  position: fixed;
  width: 100%;
  top: 0;
  background-color: rgba(22, 21, 21, 0.8);
  backdrop-filter: blur(10px);
  padding: 20px;
  z-index: 50;
  border-bottom: 1px solid rgba(128, 0, 128, 0.2);
}

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.navbar-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  background: linear-gradient(to right, #9b4dca, #9a1de0);
  background-clip: text;
  color: transparent;
}

.desktop-nav {
  display: flex;
  gap: 20px;
}

.nav-link {
  color: #ccc;
  text-decoration: none;
  font-size: 16px;
}

.nav-link:hover {
  color: #9b4dca;
}

.btn {
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

.sign-in {
  background: none;
  color: #9b4dca;
  border: 1px solid #9b4dca;
}

.get-started {
  background-color: #9b4dca;
  color: white;
}

.mobile-menu-btn {
  display: block;
  cursor: pointer;
  color: #ccc;
  font-size: 18px;
}

.mobile-nav {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

@media screen and (min-width: 768px) {
  .desktop-nav {
    display: flex;
  }

  .mobile-menu-btn {
    display: none;
  }

  .mobile-nav {
    display: none;
  }
}








</style>