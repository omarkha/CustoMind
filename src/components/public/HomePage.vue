<template>
  <div class="page">
    <!-- Hero Section -->
    <div class="hero">
      <div class="uvp">
        <h1 class="brand-name">CustoMind</h1>
        <h2>Transform Customer Data Into Competitive Advantage</h2>
        <hr class="divider" />

        <!-- Value Propositions -->
        <div class="value-props">
          <p v-motion="valuePropAnimation" class="value-prop">
            Unlock the power of behavioral intelligence with our AI-driven
            customer mapping platform.

            <span class="highlight">Go beyond demographics</span> to understand
            the why behind customer decisions and create experiences that drive
            loyalty and revenue.
          </p>
        </div>

        <div class="btn-group">
          <button
            id="cta-second"
            class="btn-secondary"
            v-motion="buttonAnimation"
          >
            <font-awesome-icon :icon="['fas', 'map-marked-alt']" /> See Platform
            Demo
          </button>
          <button
            id="cta-first"
            class="btn-primary"
            v-motion="buttonAnimation"
            :delay="100"
          >
            <font-awesome-icon :icon="['fas', 'rocket']" /> Start Your Free
            Trial
          </button>
        </div>
        <div class="trust-signals">
          <div class="trust-badge" v-motion="trustBadgeAnimation">
            <font-awesome-icon :icon="['fas', 'shield-alt']" />
            Enterprise-Grade Security
          </div>
          <div class="trust-badge" v-motion="trustBadgeAnimation" :delay="100">
            <font-awesome-icon :icon="['fas', 'chart-line']" /> Proven ROI
          </div>
        </div>
      </div>
      <div class="brand-visual">
        <img
          v-motion="parallaxAnimation"
          src="@/assets/brain.jpg"
          alt="AI-powered customer intelligence visualization"
          class="hero-image"
        />
        <div class="glow-effect"></div>
      </div>
    </div>

    <!-- Services Section -->
    <div class="services">
      <h2 class="section-title" v-motion="sectionTitleAnimation">
        360° Customer Intelligence
      </h2>
      <p class="section-subtitle" v-motion="sectionSubtitleAnimation">
        Combine multiple data dimensions for complete customer understanding
      </p>

      <div class="services-grid">
        <div
          class="service"
          v-for="(service, index) in services"
          :key="service.title"
          v-motion="serviceCardAnimation(index)"
        >
          <div class="service-header">
            <div class="icon-wrapper">
              <font-awesome-icon :icon="service.icon" class="service-icon" />
            </div>
            <h3>{{ service.title }}</h3>
            <p class="service-description">{{ service.description }}</p>
          </div>
          <hr class="service-divider" />
          <ul class="features">
            <li v-for="feature in service.features" :key="feature">
              <font-awesome-icon :icon="['fas', 'check-circle']" />
              <template v-if="feature.includes(':')">
                <strong>{{ feature.split(":")[0] }}</strong
                >: {{ feature.split(":")[1] }}
              </template>
              <template v-else>
                {{ feature }}
              </template>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { library } from "@fortawesome/fontawesome-svg-core";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { ref } from "vue";

// Font Awesome icons setup
import {
  faMapMarkedAlt,
  faRocket,
  faShieldAlt,
  faChartLine,
  faCheckCircle,
  faGlobe,
  faBrain,
  faComments,
} from "@fortawesome/free-solid-svg-icons";

library.add(
  faMapMarkedAlt,
  faRocket,
  faShieldAlt,
  faChartLine,
  faCheckCircle,
  faGlobe,
  faBrain,
  faComments
);

// Motion animations
const valuePropAnimation = ref({
  initial: { opacity: 0, y: 20 },
  enter: { opacity: 1, y: 0, transition: { duration: 500 } },
});

const buttonAnimation = ref({
  initial: { opacity: 0, y: 20 },
  enter: { opacity: 1, y: 0, transition: { duration: 500 } },
});

const trustBadgeAnimation = ref({
  initial: { opacity: 0, scale: 0.8 },
  enter: { opacity: 1, scale: 1, transition: { duration: 500 } },
});

const parallaxAnimation = ref({
  initial: { y: -50 },
  visible: { y: 0 },
  hovered: { y: -10 },
  tapped: { y: -5 },
  transition: { type: "spring", stiffness: 300, damping: 20 },
});

const sectionTitleAnimation = ref({
  initial: { opacity: 0, y: 20 },
  visibleOnce: { opacity: 1, y: 0, transition: { duration: 500 } },
});

const sectionSubtitleAnimation = ref({
  initial: { opacity: 0, y: 20 },
  visibleOnce: { opacity: 1, y: 0, transition: { duration: 500, delay: 100 } },
});

const serviceCardAnimation = (index) => ({
  initial: { opacity: 0, y: 50 },
  visibleOnce: {
    opacity: 1,
    y: 0,
    transition: {
      duration: 500,
      delay: 100 * index,
    },
  },
});

// Services data
const services = [
  {
    icon: ["fas", "globe"],
    title: "Demographic Profiling",
    description: "Understand who your customers are",
    features: [
      "Location: Geographic distribution analysis",
      "Income: Spending capacity segmentation",
      "Education: Career level correlations",
      "Life Stage: Family and age grouping",
      "Culture: Background and preference mapping",
    ],
  },
  {
    icon: ["fas", "brain"],
    title: "Psychographic Insights",
    description: "Discover why they make decisions",
    features: [
      "Values: Core motivation identification",
      "Lifestyle: Daily habit patterns",
      "Personality: Archetype classification",
      "Brands: Affinity scoring",
      "Pain Points: Frustration hotspots",
    ],
  },
  {
    icon: ["fas", "comments"],
    title: "Behavioral Mapping",
    description: "Learn how they engage with your brand",
    features: [
      "Journeys: Purchase path visualization",
      "Channels: Preferred interaction points",
      "Responses: Campaign reaction patterns",
      "Feedback: Sentiment analysis",
      "Loyalty: Retention drivers",
    ],
  },
];
</script>

<style scoped lang="scss">
/* Base Styles */
.page {
  width: 100%;
  max-width: 100vw;
  background: #03040f;
  color: #fff;
  overflow-x: hidden;
  font-family: "Inter", -apple-system, BlinkMacSystemFont, sans-serif;
}

.value-props {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.features {
  li {
    strong {
      color: hsl(55, 100%, 50%);
      font-weight: 600;
    }
  }
}

.highlight {
  color: hsl(55, 100%, 50%);
  font-weight: 700;
}

/* Hero Section */
.hero {
  height: 90vh;
  padding: 0 10vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 2rem;
  position: relative;
  overflow: hidden;

  @media (min-width: 1024px) {
    flex-direction: row;
    gap: 5rem;
  }

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: hsl(235, 67%, 23.6%);
    box-shadow: inset 0 -38vh 38vh 3px #03040f;
    background-image: url("@/assets/baghdad-15.jpg");
    background-size: cover;
    background-blend-mode: overlay;
    z-index: 0;
  }

  .uvp {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    width: 100%;
    text-align: center;
    padding: 2rem;
    border-radius: 1rem;
    background: rgba(3, 4, 15, 0.7);
    backdrop-filter: blur(8px);

    @media (min-width: 768px) {
      text-align: left;
      align-items: flex-start;
      background: rgba(3, 4, 15, 0.5);
    }

    .brand-name {
      font-family: "PT Sans", sans-serif;
      color: hsl(55, 100%, 50%);
      font-size: clamp(2.5rem, 8vw, 4.5rem);
      text-shadow: 0.25rem 0.25rem 1px hsl(232, 100%, 62%);
      margin-bottom: 0.5rem;
      line-height: 1;
    }

    h2 {
      font-size: clamp(1.5rem, 4vw, 2.5rem);
      line-height: 1.3;
      color: #fff;
      font-weight: 700;
      margin-bottom: 0.5rem;
    }

    .divider {
      width: 100%;
      max-width: 400px;
      height: 3px;
      background: linear-gradient(90deg, hsl(55, 100%, 50%), transparent);
      border: none;
      margin: 0;

      @media (min-width: 768px) {
        background: linear-gradient(90deg, hsl(55, 100%, 50%), transparent);
      }
    }

    .value-prop {
      font-size: clamp(1rem, 2vw, 1.25rem);
      line-height: 1.6;
      color: hsl(232, 100%, 85%);
      margin-bottom: 1.5rem;
    }

    .btn-group {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      justify-content: center;
      margin-bottom: 1.5rem;

      @media (min-width: 768px) {
        justify-content: flex-start;
      }

      button {
        font-size: clamp(0.9rem, 2vw, 1rem);
        font-weight: 600;
        border-radius: 2rem;
        padding: 0.8rem 1.8rem;
        border: none;
        cursor: pointer;
        transition: all 0.3s ease;
        display: flex;
        align-items: center;
        gap: 0.5rem;

        svg {
          font-size: 0.9em;
        }
      }

      .btn-primary {
        background-color: hsl(235, 67%, 50%);
        color: #fff;
        box-shadow: 0 4px 15px rgba(56, 86, 194, 0.4);

        &:hover {
          transform: translateY(-3px);
          box-shadow: 0 8px 25px rgba(56, 86, 194, 0.6);
          background-color: hsl(235, 67%, 45%);
        }
      }

      .btn-secondary {
        background: transparent;
        color: hsl(232, 100%, 85%);
        border: 2px solid hsl(55, 67%, 50%);

        &:hover {
          background: rgba(255, 215, 0, 0.1);
          box-shadow: 0 0 20px rgba(255, 215, 0, 0.3);
        }
      }
    }

    .trust-signals {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      font-size: 0.8rem;

      @media (min-width: 768px) {
        justify-content: flex-start;
      }

      .trust-badge {
        display: flex;
        align-items: center;
        gap: 0.5rem;
        padding: 0.5rem 1rem;
        background: rgba(255, 255, 255, 0.1);
        border-radius: 2rem;
        color: hsl(55, 67%, 80%);

        svg {
          color: hsl(55, 100%, 50%);
        }
      }
    }
  }

  .brand-visual {
    position: relative;
    margin-top: 2rem;
    width: 100%;
    max-width: 500px;
    display: flex;
    justify-content: center;
    align-items: center;

    .hero-image {
      width: 100%;
      max-width: 350px;
      border-radius: 50%;
      border: 3px solid hsl(235, 67%, 50%);
      position: relative;
      z-index: 2;
      animation: float 6s ease-in-out infinite;
      box-shadow: 0 0 50px hsla(235, 67%, 50%, 0.5);
    }

    .glow-effect {
      position: absolute;
      width: 120%;
      height: 120%;
      background: radial-gradient(
        circle,
        hsla(235, 67%, 50%, 0.3) 0%,
        transparent 70%
      );
      border-radius: 50%;
      animation: pulse 8s ease-in-out infinite alternate;
    }
  }
}

/* Services Section */
.services {
  padding: 6rem 5vw;
  max-width: 1400px;
  margin: 0 auto;

  .section-title {
    font-size: clamp(1.8rem, 4vw, 2.5rem);
    text-align: center;
    color: hsl(55, 100%, 50%);
    margin-bottom: 1rem;
    font-weight: 700;
  }

  .section-subtitle {
    text-align: center;
    font-size: clamp(1rem, 2vw, 1.25rem);
    color: hsl(55, 67%, 80%);
    max-width: 700px;
    margin: 0 auto 3rem;
    line-height: 1.6;
  }

  .services-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;

    @media (min-width: 768px) {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  .service {
    background: linear-gradient(145deg, #0a0f2e 0%, #070b27 100%);
    border-radius: 1rem;
    padding: 2rem;
    transition: all 0.3s ease;
    border: 1px solid rgba(56, 86, 194, 0.2);
    position: relative;
    overflow: hidden;
    z-index: 1;

    &:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 30px rgba(56, 86, 194, 0.3);
      border-color: hsla(55, 100%, 50%, 0.3);

      .service-icon {
        transform: scale(1.1);
        color: hsl(55, 100%, 50%);
      }
    }

    .service-header {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-bottom: 1.5rem;

      .icon-wrapper {
        width: 80px;
        height: 80px;
        background: rgba(56, 86, 194, 0.2);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 1rem;
      }

      .service-icon {
        font-size: 2rem;
        color: hsl(235, 67%, 50%);
        transition: all 0.3s ease;
      }

      h3 {
        font-size: 1.5rem;
        color: #fff;
        text-align: center;
        margin-bottom: 0.5rem;
      }

      .service-description {
        color: hsl(55, 67%, 80%);
        text-align: center;
        font-size: 0.9rem;
        margin-bottom: 0;
      }
    }

    .service-divider {
      width: 50%;
      height: 2px;
      background: linear-gradient(
        90deg,
        transparent,
        hsl(55, 100%, 50%),
        transparent
      );
      border: none;
      margin: 1.5rem auto;
    }

    .features {
      padding-left: 0;
      list-style: none;

      li {
        margin-bottom: 1rem;
        display: flex;
        align-items: flex-start;
        gap: 0.75rem;
        font-size: 0.95rem;
        line-height: 1.5;
        color: hsl(55, 67%, 80%);

        .feature-icon {
          color: hsl(55, 100%, 50%);
          margin-top: 0.2rem;
          flex-shrink: 0;
        }
      }
    }
  }
}

/* Animations */
@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-15px);
  }
}

@keyframes pulse {
  0% {
    transform: scale(1);
    opacity: 0.6;
  }
  100% {
    transform: scale(1.1);
    opacity: 0.3;
  }
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .hero {
    padding: 3rem 5vw;
    text-align: center;
    min-height: fit-content;
    .uvp {
      align-items: center;
      text-align: center;

      .divider {
        margin: 1rem auto;
      }
    }

    .brand-visual {
      .hero-image {
        max-width: 250px;
      }
    }
  }

  .services {
    padding: 4rem 5vw;
  }
}
</style>
