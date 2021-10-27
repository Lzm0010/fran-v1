<template>
  <div id="app">
    <!-- Nav Bar -->
    <nav>
      <ul>
        <li @click="switchTab('')">
          <div class="logo">
            <span class="highlight">Francesca</span>
            <span class="subtext">Barker McCormick</span>
          </div>
        </li>
        <li
          class="nav-links"
          v-for="tab in tabs"
          :key="tab"
          @click="switchTab(tab)"
        >
          {{ tab }}
        </li>
        <li class="mobile-nav">
          <a href="javascript:void(0);" @click="showNav()" class="mobile-menu">
            <font-awesome-icon :icon="['fas', 'bars']" />
          </a>
        </li>
      </ul>
    </nav>
    <ul v-show="toggleMobileNav === true" class="mobile-links">
      <li
        class="mobile-link"
        v-for="tab in tabs"
        :key="tab"
        @click="switchTab(tab)"
      >
        {{ tab }}
      </li>
    </ul>

    <main class="main">
      <!-- Landing Page -->
      <section v-show="activeTab === ''">
        <h2>Francesca Barker McCormick</h2>
        <ul class="landing-links">
          <li>
            <a href="https://www.imdb.com/name/nm11906396/" target="_blank"
              >IMDb</a
            >
          </li>
          <li>
            <a
              href="https://resumes.actorsaccess.com/francescabmccormick"
              target="_blank"
              >Actors Access</a
            >
          </li>
          <li>
            <a
              href="https://app.castingnetworks.com/talent/public-profile/b9b305d6-35e3-11ec-9c45-2b5241d49a43"
              target="_blank"
              >LA Casting</a
            >
          </li>
          <li>
            <a
              href="https://www.backstage.com/u/francesca-mccormick/"
              target="_blank"
              >Backstage</a
            >
          </li>
        </ul>
        <img
          class="landing-image"
          src="@/assets/images/landingfran.jpg"
          alt="Fran at Vogue Event"
        />
      </section>

      <!-- About Tab -->
      <section v-show="activeTab === 'About'">
        <h2>About Me</h2>
        <div class="about-me">
          <div class="about-me-item">
            <p>
              Francesca Barker McCormick (born April 16, 1993) is a Hispanic
              American actress.
            </p>
            <p>
              Prior to her career in film and television, her inherent eye for
              fashion and shows such as Sweet Home Alabama, Sex and the City,
              Gossip Girl, and The Devil Wears Prada influenced her decision to
              move to New York City to begin work within the luxury fashion
              industry. Francesca produced numerous events with Escada, Vogue,
              GQ, Vanity Fair, Balmain, Fendi, Ralph Lauren, and many more - the
              pinnacle being Vogue’s Met Gala! She also worked as a Vogue Market
              Stylist, acting as a representative of the brand and hosting
              events on their behalf.
            </p>
            <p>
              It was through her hosting of events onscreen and off, that her
              passion for performing ignited once again. After 6 years within
              the corporate fashion world, Francesca gave her acting career
              center stage. Barker McCormick has since landed roles in three
              series pilots (Skylife, SinFull, Justice Soldier of God) and three
              films (Ill Intentions, How to Find Love in a Pandemic, Game of
              Chess).
            </p>
            <p>
              Outside of acting, Francesca continues her work in the event world
              as the Project Director for Gina’s Collective, an advisory for
              tech-enabled nonprofits. She also serves on the event committee
              for the Princess Grace Kelly Foundation, an organization dedicated
              to upholding the legacy of Princess Grace of Monaco, and elevating
              extraordinary emerging artists in theater, dance and film through
              career-advancing grants.
            </p>
            <p>
              She is married to Lee McCormick and together, they have an
              adorable French Bulldog, Penelope.
            </p>
          </div>
          <div class="about-me-item about-me-item-img">
            <div class="about-me-img-frame">
              <img
                class="about-me-img"
                src="@/assets/images/aboutfran.jpg"
                alt="About Francesca"
              />
            </div>
          </div>
        </div>
      </section>

      <!-- Photos Tab -->
      <section v-show="activeTab === 'Photos'">
        <h2>Photos</h2>
        <div class="headshots">
          <img
            class="headshot"
            v-for="(headshot, index) in headshots"
            :key="index"
            :src="getImgUrl(headshot)"
            :alt="`Francesca Headshot ${index}`"
          />
        </div>
      </section>

      <!-- Video Tab -->
      <section v-show="activeTab === 'Video'">
        <h2>Video</h2>
        <div class="resume-container">
          <div class="video-frame">
            <iframe
              class="video-iframe"
              src="https://www.youtube.com/embed/HS7Uac4KzCw"
              frameborder="0"
              allowfullscreen
            >
            </iframe>
          </div>
        </div>
      </section>

      <!-- Resume Tab -->
      <section v-show="activeTab === 'Resume'">
        <div class="resume-header">
          <h2>Resume</h2>
          <a
            :href="`${publicPath}francescamccormickresume.pdf`"
            target="_blank"
            class="download-button"
            >Download</a
          >
        </div>
        <div class="resume-container">
          <div class="resume-frame">
            <img
              :src="getImgUrl(resumeImg)"
              alt="Francesca's Resume"
              class="resume-image"
            />
          </div>
        </div>
      </section>

      <!-- Resume Tab -->
      <section v-show="activeTab === 'Reviews'">
        <h2>Reviews</h2>
        <div class="reviews-container">
          <div class="reviews-frame">
            <div class="reviews">
              <div class="review">
                <div class="header-row">
                  <h4>Skylife - Ashley</h4>
                  <img
                    class="review-image"
                    :src="getPng('skylife')"
                    alt="Skylife"
                  />
                </div>
                <p>
                  “You think it is a given but the fact that Francesca knew her
                  lines inside and out, where I was not distracted by an actor
                  searching for his/her lines or stumbling over words… I was
                  simply focused on the performance and thinking to myself ‘this
                  actress captures the essence of the character’s
                  eloquence/frustration and emotional bandwidth’. I kept
                  watching the screen for any signs of dishonesty in the
                  performance but I could find none. An actor gets a few seconds
                  or a few minutes to showcase his/her ability to
                  deliver…preparation /performance dictates the former or the
                  latter.
                </p>
                <p>
                  As a writer who spends an enormous amount of time developing
                  characters and their stories, I work very hard building the
                  ideal cast. It takes me more time than most to find the ideal
                  talent only because I know my characters so well and the world
                  in which they live. What I see and hear in my head is not
                  always easy to match beyond my imagination. You want talent
                  that can deliver. Talent who will put in the work. Not
                  everyone is willing to do that.
                </p>
                <p>
                  I am extremely satisfied and pleased with the cast assembled
                  for SKYLIFE - ‘Heroes and Heroines’ (proof of concept). When
                  an actor is right for a role, when research and rehearsals are
                  fully explored… it makes for a much smoother production and
                  authentic performance.
                </p>
                <p>
                  It was evident Francesca understood the essence of Ashley, her
                  inner and outer struggles… Francesca made it effortless. It
                  was a pleasure to watch Francesca bring this character to
                  life. ”
                </p>
                <p class="reviewer">- Marvalee Peart</p>
              </div>
              <div class="review">
                <div class="header-row">
                  <h4>How to Find Love In A Pandemic - Summer</h4>
                  <img
                    class="review-image"
                    :src="getPng('howtofindlove')"
                    alt="How to Find Love in a Pandemic"
                  />
                </div>
                <p>
                  “Francesca is a joy to work with! Her eagerness to dive into
                  the work, the character development she brought to the role,
                  and her comedic timing all stood out to us. She took what we
                  wrote and brought her own unique choices to Summer to create a
                  hilarious and full character. On top of that, she is a warm,
                  kind, and supportive supportive presence in any room. We can’t
                  wait to work with her again!”
                </p>
                <p class="reviewer">- Joe Bridgewood & Emily Blake Anderson</p>
              </div>
              <div class="review">
                <h4>SinFull - Dr. Alicia Serrano</h4>
                <p>
                  “Watching Francesca bring Dr. Alicia to life was such a
                  powerfully beautiful moment to witness as a writer. She
                  painted her in ways that I hadn't even imagined and brought
                  such a riveting sense of compassion and heartbreak to the
                  role. I think the audience will be quite taken by her ability
                  to ground you, the viewer, into the intimacy of Alicia's inner
                  turmoil. ”
                </p>
                <p class="reviewer">- Asha Etchison</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Contact Tab -->
      <section v-show="activeTab === 'Contact'">
        <div class="header-row">
          <h2>Contact</h2>
          <a
            class="insta-link"
            href="https://www.instagram.com/francescabmccormick/?hl=en"
            target="_blank"
          >
            <font-awesome-icon :icon="['fab', 'instagram']" />
            Instagram
          </a>
        </div>
        <div class="form-container">
          <form @submit.prevent="sendEmail">
            <input
              class="form-group"
              v-model="name"
              type="text"
              name="name"
              id="name"
              placeholder="Name"
            />
            <input
              class="form-group"
              v-model="email"
              name="email"
              type="email"
              id="email"
              placeholder="Email"
            />
            <textarea
              class="form-group form-group-textarea"
              v-model="message"
              name="message"
              id="message"
              placeholder="Add a message"
            ></textarea>
            <button class="submit-button" type="submit" value="Send">
              Submit
            </button>
          </form>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import emailjs from "emailjs-com";

export default {
  name: "App",
  data: function () {
    return {
      toggleMobileNav: false,
      publicPath: process.env.BASE_URL,
      tabs: ["About", "Photos", "Video", "Resume", "Reviews", "Contact"],
      activeTab: "",
      resumeImg: "francescamccormickresume",
      headshots: ["fran0", "fran1", "fran2", "fran3", "fran4", "fran5"],
      name: "",
      email: "",
      message: "",
    };
  },
  methods: {
    switchTab(tab) {
      this.activeTab = tab;
      if (this.toggleMobileNav === true) {
        this.toggleMobileNav = false;
      }
    },
    showNav() {
      this.toggleMobileNav = !this.toggleMobileNav;
    },
    getImgUrl(img) {
      var images = require.context("./assets/images", false, /\.jpg$/);
      return images("./" + img + ".jpg");
    },
    getPng(img) {
      var images = require.context("./assets/images", false, /\.png$/);
      return images("./" + img + ".png");
    },
    sendEmail(e) {
      try {
        emailjs.sendForm(
          "service_i53z8am",
          "template_atl4edp",
          e.target,
          "user_12FyiUAE9iIeOxJijTOfS",
          {
            name: this.name,
            email: this.email,
            message: this.message,
          }
        );
      } catch (error) {
        console.log({ error });
      }
      this.name = "";
      this.email = "";
      this.message = "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

@font-face {
  font-family: "AmsterdamOne";
  src: url("./assets/fonts/amsterdamOne.ttf");
}

@font-face {
  font-family: "crushed";
  src: url("./assets/fonts/crushed.ttf");
}

body {
  margin: 0;
  background-color: #fad0c6;
  font-family: "Open Sans", Arial, Helvetica, sans-serif;
}

h2 {
  font-family: "crushed", Arial, Helvetica, sans-serif;
  font-size: 6rem;
  color: #f56200;
}

.header-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Navigation */

nav {
  font-family: "AmsterdamOne", sans-serif;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  margin: 0;
  background-color: #ad2a67;
  border-bottom: 1rem solid #f56200;
}

nav ul {
  display: flex;
  justify-content: space-evenly;
  list-style: none;
}

.mobile-nav {
  display: none;

  a {
    text-decoration: none;
    color: #fad0c6;
  }
}

.highlight {
  color: #f56200;
}

/* .subtext {
    font-family: 'crushed';
    position: absolute;
} */

nav li {
  padding: 1.25rem;
  margin: 0 0.3125rem;
  color: #fad0c6;
  font-size: 1.25rem;
  cursor: pointer;
}

nav li:hover {
  color: #f56200;
}

/* Main Section */

.main {
  padding: 8rem 10rem;
}

/* Landing Page */

.landing-image {
  margin-top: -4rem;
  height: 100%;
  width: 100%;
  border: 4rem solid #ad2a67;
  border-radius: 4px;
}

.landing-links {
  margin-top: -4rem;
  list-style: none;
  display: flex;
  justify-content: space-around;
  padding: 1rem 0;
  font-family: "crushed", Arial, Helvetica, sans-serif;
  li {
    padding: 2rem;
    &:hover {
      background-color: white;
    }
  }
  a {
    font-size: 2.5rem;
    color: #ad2a67;
    text-decoration: none;
  }
}

/* About Me Page */

.about-me {
  display: flex;
  justify-content: space-evenly;
  color: #ad2a67;
  letter-spacing: 0.07em;
}

.about-me-img-frame {
  background-color: #ad2a67;
  padding: 0.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  border-radius: 4px;
}

.about-me-img {
  width: 68%;
  height: 85%;
}

.about-me-item {
  padding: 1rem;
  flex: 1 1 0;
}

/* Photos Page */

.headshots {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  align-items: flex-start;
}

.headshot {
  padding-bottom: 0.5rem;
  width: 21rem;
}

/* Video Page */

.video-frame {
  background-color: #ad2a67;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 4px;
  padding: 2rem;
}

.video-iframe {
  height: 43rem;
  width: 50rem;
}

/* Resume Page */

.resume-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.download-button {
  text-decoration: none;
  border: 3px solid #f56200;
  height: 3.125rem;
  width: 10rem;
  background-color: #ad2a67;
  color: white;
  border-radius: 4px;
  /* margin: 0 auto; */
  display: flex;
  align-items: center;
  justify-content: center;

  &:hover {
    background-color: white;
    color: #ad2a67;
  }
}

.resume-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.resume-frame {
  background-color: #ad2a67;
  width: 80%;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 4px;
  padding: 2rem;
}

.resume-image {
  width: 100%;
  height: 70%;
}

/* Reviews Page */

.reviews-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.reviews-frame {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  background-color: #ad2a67;
  border-radius: 4px;
  width: 80%;
}

.reviews {
  background-color: white;
  display: flex;
  flex-direction: column;
  border-radius: 4px;
  padding: 3rem;

  .review {
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    h4 {
      color: #ad2a67;
    }

    .review-image {
      height: 30%;
      width: 30%;
    }

    .reviewer {
      color: #f56200;
    }
  }
}

/* Contact Page */

.insta-link {
  text-decoration: none;
  background-color: #ad2a67;
  color: white;
  padding: 1.3rem;
  border: 3px solid #f56200;
  border-radius: 4px;
  margin-right: 2.5rem;

  &:hover {
    background-color: white;
    color: #ad2a67;
  }
}

.form-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

form {
  padding: 2rem;
  width: 80%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #ad2a67;
  border-radius: 4px;
}

.form-group {
  max-width: 100%;
  width: 100%;
  height: 3.125rem;
  background-color: white;
  border: 3px solid #f56200;
  border-radius: 4px;
  margin-bottom: 1.5rem;
  padding-left: 0.5rem;
  font-size: 1rem;
  font-family: "Open Sans", Arial, Helvetica, sans-serif;

  &:hover {
    background-color: #fad0c6;
  }
}

.form-group-textarea {
  height: 6.25rem;
  padding-top: 0.75rem;
}

.submit-button {
  height: 3.125rem;
  width: 50%;
  background-color: #f56200;
  color: white;
  border: 3px solid white;
  border-radius: 4px;
  margin: 0 auto;
  cursor: pointer;
  font-size: 1rem;

  &:hover {
    background-color: white;
    color: #f56200;
  }
}

@media screen and (max-width: 900px) {
  .main {
    padding: 6rem 1rem;
  }

  nav ul {
    justify-content: space-around;
    align-items: center;
    padding: 0;
  }

  nav li {
    padding: 0;
    margin: 0;
  }

  .mobile-nav {
    display: block;
    padding: 0.5rem;
    font-size: 1.5rem;
  }

  .mobile-links {
    background-color: #ad2a67;
    padding: 0;
    position: absolute;
    top: 7.6rem;
    text-align: center;
    display: block;
    width: 100%;
  }

  .mobile-link {
    font-family: "AmsterdamOne", sans-serif;
    padding: 0.7rem;
    font-size: 1rem;
    color: #fad0c6;
    list-style: none;
  }

  .nav-links {
    display: none;
  }

  .logo {
    font-size: 1rem;
  }

  h2 {
    font-size: 3.75rem;
  }

  .landing-image {
    border: 0.5rem solid #ad2a67;
  }

  .landing-links {
    align-items: center;
    a {
      font-size: 0.8rem;
    }
  }

  .about-me {
    display: flex;
    flex-wrap: wrap;
    letter-spacing: 0.07em;
  }

  .about-me-img-frame {
    background-color: #ad2a67;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 4px;
  }

  .about-me-img {
    width: 100%;
    height: 100%;
    border: 0.5rem solid #ad2a67;
  }

  .about-me-item {
    padding: 0.5rem;
    flex: 0 1 auto;
    flex-basis: 100%;
  }

  .about-me-item-img {
    margin-top: -2rem;
    order: -1;
  }

  .video-frame {
    width: 90%;
    padding: 0.5rem;
  }

  .video-iframe {
    height: 100%;
    width: 100%;
  }

  .resume-frame {
    width: 100%;
    padding: 0.5rem;
  }

  .review-image {
    flex-basis: 95%;
  }

  .insta-link {
    margin-right: 0;
    padding: 0.81rem;
  }
}
</style>
