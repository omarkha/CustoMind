<template>
  <footer class="site-footer">
    <div class="footer-content">
      <div class="footer-brand">
        <h2 class="footer-logo">CustoMind</h2>
        <p class="footer-tagline">
          AI-powered customer intelligence to transform your business strategy
        </p>
        <div class="newsletter">
          <h4>Get Insights Delivered</h4>
          <form @submit.prevent="subscribeNewsletter">
            <input
              type="email"
              placeholder="Your business email"
              required
              v-model="email"
            />
            <button type="submit">
              <font-awesome-icon icon="fa-solid fa-paper-plane" />
            </button>
          </form>
        </div>
      </div>

      <div class="footer-links">
        <div class="link-group">
          <h3 class="link-heading">Platform</h3>
          <ul>
            <li><a href="#features">Features</a></li>
            <li><a href="#solutions">Solutions</a></li>
            <li><a href="#pricing">Pricing</a></li>
            <li><a href="#demo">Request Demo</a></li>
          </ul>
        </div>

        <div class="link-group">
          <h3 class="link-heading">Resources</h3>
          <ul>
            <li><a href="#blog">Blog</a></li>
            <li><a href="#casestudies">Case Studies</a></li>
            <li><a href="#webinars">Webinars</a></li>
            <li><a href="#guides">Guides</a></li>
          </ul>
        </div>

        <div class="link-group">
          <h3 class="link-heading">Company</h3>
          <ul>
            <li><a href="#about">About Us</a></li>
            <li><a href="#careers">Careers</a></li>
            <li><a href="#contact">Contact</a></li>
            <li><a href="#press">Press</a></li>
          </ul>
        </div>
      </div>

      <div class="footer-social">
        <h3 class="social-heading">Connect With Us</h3>
        <div class="social-icons">
          <a href="#" class="social-icon" aria-label="Instagram">
            <font-awesome-icon :icon="['fab', 'instagram']" />
          </a>
          <a href="#" class="social-icon" aria-label="TikTok">
            <font-awesome-icon :icon="['fab', 'tiktok']" />
          </a>
          <a href="#" class="social-icon" aria-label="YouTube">
            <font-awesome-icon :icon="['fab', 'youtube']" />
          </a>
          <a href="#" class="social-icon" aria-label="LinkedIn">
            <font-awesome-icon :icon="['fab', 'linkedin']" />
          </a>
          <a href="#" class="social-icon" aria-label="Twitter">
            <font-awesome-icon :icon="['fab', 'twitter']" />
          </a>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <div class="legal-links">
        <a href="#privacy">Privacy Policy</a>
        <a href="#terms">Terms of Service</a>
        <a href="#cookies">Cookie Policy</a>
      </div>
      <div class="copyright">
        &copy; {{ new Date().getFullYear() }} CustoMind. All rights reserved.
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref } from "vue";
import { library } from "@fortawesome/fontawesome-svg-core";
import {
  faInstagram,
  faTiktok,
  faYoutube,
  faLinkedin,
  faTwitter,
} from "@fortawesome/free-brands-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

// Add icons to library
library.add(faInstagram, faTiktok, faYoutube, faLinkedin, faTwitter);
const email = ref("");

const subscribeNewsletter = () => {
  // Handle newsletter subscription
  console.log("Subscribed with:", email.value);
  email.value = "";
  // You would typically call an API here
};
</script>

<style lang="scss" scoped>
.site-footer {
  background: linear-gradient(to bottom, transparent, hsl(233, 70%, 10%));
  color: #fff;
  padding: 4rem 5vw 2rem;
  position: relative;
  overflow: hidden;

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 1px;
    background: linear-gradient(
      90deg,
      transparent,
      hsl(55, 100%, 50%),
      transparent
    );
  }

  .footer-content {
    display: grid;
    grid-template-columns: 1fr;
    gap: 3rem;
    max-width: 1400px;
    margin: 0 auto;

    @media (min-width: 768px) {
      grid-template-columns: 1fr 2fr;
    }

    @media (min-width: 1024px) {
      grid-template-columns: 1fr 1.5fr 1fr;
    }
  }

  .footer-brand {
    .footer-logo {
      font-family: "PT Sans", sans-serif;
      font-size: 2.5rem;
      color: hsl(55, 100%, 50%);
      text-shadow: 2px 2px 2px hsl(232, 100%, 62%);
      margin-bottom: 1rem;
    }

    .footer-tagline {
      color: hsl(232, 100%, 85%);
      line-height: 1.6;
      margin-bottom: 2rem;
      font-size: 1.1rem;
    }

    .newsletter {
      h4 {
        color: hsl(55, 67%, 80%);
        margin-bottom: 1rem;
        font-size: 1rem;
      }

      form {
        display: flex;
        border-radius: 2rem;
        overflow: hidden;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);

        input {
          flex: 1;
          padding: 0.8rem 1.2rem;
          border: none;
          background: rgba(255, 255, 255, 0.1);
          color: #fff;
          font-size: 0.9rem;

          &::placeholder {
            color: hsl(232, 100%, 75%);
          }

          &:focus {
            outline: 2px solid hsl(55, 100%, 50%);
          }
        }

        button {
          background: hsl(235, 67%, 50%);
          color: #fff;
          border: none;
          padding: 0 1.2rem;
          cursor: pointer;
          transition: all 0.3s ease;

          &:hover {
            background: hsl(235, 67%, 45%);
          }
        }
      }
    }
  }

  .footer-links {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;

    @media (min-width: 768px) {
      grid-template-columns: repeat(3, 1fr);
    }

    .link-group {
      .link-heading {
        color: hsl(55, 100%, 50%);
        font-size: 1.1rem;
        margin-bottom: 1.5rem;
        padding-bottom: 0.5rem;
        border-bottom: 2px solid hsl(55, 100%, 50%);
        width: fit-content;
      }

      ul {
        list-style: none;
        padding: 0;
        margin: 0;

        li {
          margin-bottom: 0.8rem;

          a {
            color: hsl(232, 100%, 85%);
            text-decoration: none;
            transition: all 0.3s ease;
            display: inline-block;
            padding: 0.2rem 0;
            position: relative;

            &::after {
              content: "";
              position: absolute;
              bottom: 0;
              left: 0;
              width: 0;
              height: 1px;
              background: hsl(55, 100%, 50%);
              transition: width 0.3s ease;
            }

            &:hover {
              color: hsl(55, 100%, 50%);

              &::after {
                width: 100%;
              }
            }
          }
        }
      }
    }
  }

  .footer-social {
    .social-heading {
      color: hsl(55, 100%, 50%);
      font-size: 1.1rem;
      margin-bottom: 1.5rem;
      text-align: center;

      @media (min-width: 1024px) {
        text-align: left;
      }
    }

    .social-icons {
      display: flex;
      justify-content: center;
      gap: 1.5rem;
      flex-wrap: wrap;

      @media (min-width: 1024px) {
        justify-content: flex-start;
      }

      .social-icon {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.1);
        display: flex;
        align-items: center;
        justify-content: center;
        color: hsl(232, 100%, 75%);
        font-size: 1.2rem;
        transition: all 0.3s ease;

        &:hover {
          background: hsl(235, 67%, 50%);
          color: #fff;
          transform: translateY(-3px);
        }
      }
    }
  }

  .footer-bottom {
    margin-top: 3rem;
    padding-top: 2rem;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    color: hsl(232, 100%, 75%);
    font-size: 0.9rem;

    @media (min-width: 768px) {
      flex-direction: row;
      justify-content: space-between;
    }

    .legal-links {
      display: flex;
      gap: 1.5rem;
      flex-wrap: wrap;
      justify-content: center;

      a {
        color: inherit;
        text-decoration: none;
        transition: color 0.3s ease;

        &:hover {
          color: hsl(55, 100%, 50%);
        }
      }
    }
  }
}
</style>
