<script>
export default {
  name: 'BackgroundComponent',

  props: {
    mainColor: {
      type: String,
      default: '#fff'
    },
    secondFlipColor: {
      type: String,
      default: '#fff'
    },
    labelColor: {
      type: String,
      default: '#fff'
    },
    deadline: {
      type: String,
      default: '2024-11-30 20:00:00'
    }
  },

  mounted() {
    // Dynamically load Mailchimp validation script
    const script = document.createElement('script')
    script.src = '//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js'
    script.type = 'text/javascript'
    document.body.appendChild(script)

    // Mailchimp inline script
    const inlineScript = document.createElement('script')
    inlineScript.type = 'text/javascript'
    inlineScript.innerHTML = `
      (function ($) {
        window.fnames = new Array();
        window.ftypes = new Array();
        fnames[0] = 'EMAIL';
        ftypes[0] = 'email';
        fnames[1] = 'FNAME';
        ftypes[1] = 'text';
        fnames[2] = 'LNAME';
        ftypes[2] = 'text';
        fnames[3] = 'ADDRESS';
        ftypes[3] = 'address';
        fnames[4] = 'PHONE';
        ftypes[4] = 'phone';
        fnames[5] = 'BIRTHDAY';
        ftypes[5] = 'birthday';
      })(jQuery);
      var $mcj = jQuery.noConflict(true);
    `
    document.body.appendChild(inlineScript)
  }
}
</script>

<template>
  <div class="background-container">
    <div class="overlay"></div>
    <div class="content">
      <img class="logo" src="/src/assets/logo.png" />
      <div class="text">
        <h1>Your Next Show</h1>
        <p>Connecting Artists, Promoters, and Venues for Unforgettable Live Events.</p>
      </div>
      <vue3-flip-countdown
        :main-color="mainColor"
        :second-flip-color="secondFlipColor"
        :label-color="labelColor"
        :deadline="deadline"
      />

      <div id="mc_embed_shell">
        <link
          href="//cdn-images.mailchimp.com/embedcode/classic-061523.css"
          rel="stylesheet"
          type="text/css"
        />
        <div id="mc_embed_signup">
          <form
            action="https://gmail.us22.list-manage.com/subscribe/post?u=81e5bebedf5b5d92076946fe4&amp;id=52d2c10cb1&amp;f_id=0063d0e1f0"
            method="post"
            id="mc-embedded-subscribe-form"
            name="mc-embedded-subscribe-form"
            class="validate"
            target="_blank"
          >
            <div id="mc_embed_signup_scroll">
              <h2>Subscribe To Get Updates</h2>
              <div class="indicates-required">
                <span class="asterisk">*</span> indicates required
              </div>
              <div class="mc-field-group">
                <label for="mce-EMAIL">Email Address <span class="asterisk">*</span></label>
                <input
                  type="email"
                  name="EMAIL"
                  class="required email"
                  id="mce-EMAIL"
                  required=""
                  value=""
                />
              </div>
              <div id="mce-responses" class="clear foot">
                <div class="response" id="mce-error-response" style="display: none"></div>
                <div class="response" id="mce-success-response" style="display: none"></div>
              </div>
              <div aria-hidden="true" style="position: absolute; left: -5000px">
                <input
                  type="text"
                  name="b_81e5bebedf5b5d92076946fe4_52d2c10cb1"
                  tabindex="-1"
                  value=""
                />
              </div>
              <div class="optionalParent">
                <div class="clear foot">
                  <input
                    type="submit"
                    name="subscribe"
                    id="mc-embedded-subscribe"
                    class="button"
                    value="Subscribe"
                  />
                  <p style="margin: 0px auto">
                    <a
                      href="http://eepurl.com/iVVKDw"
                      title="Mailchimp - email marketing made easy and fun"
                    >
                      <span
                        style="display: inline-block; background-color: black; border-radius: 4px"
                      >
                        <img
                          class="refferal_badge"
                          src="https://digitalasset.intuit.com/render/content/dam/intuit/mc-fe/en_us/images/intuit-mc-rewards-text-light.svg"
                          alt="Intuit Mailchimp"
                          style="
                            width: 220px;
                            height: 40px;
                            display: flex;
                            padding: 2px 0px;
                            justify-content: center;
                            align-items: center;
                          "
                        />
                      </span>
                    </a>
                  </p>
                </div>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Crimson+Pro:ital,wght@0,200..900;1,200..900&family=Raleway:ital,wght@0,100..900;1,100..900&display=swap');

body {
  font-family: Raleway, sans-serif;
}

#mc_embed_signup {
  background: rgba(0, 0, 0, 0.85);
  clear: left;
  font:
    14px Helvetica,
    Arial,
    sans-serif;
  max-width: 600px;
  width: 100%;
  padding: 10px;
}

.background-container {
  position: relative;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

h1 {
  font-size: 4rem;
  line-height: 1.5;
}

p {
  font-size: 1.5rem;
  line-height: 1.5;
}
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5); /* Adjust the opacity as needed */
}

.content {
  position: relative;
  z-index: 1;
  color: white; /* Adjust the text color as needed */
  text-align: center;
  padding-block: 2rem 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

header {
  line-height: 1.5;
  max-height: 100vh;
  width: 100%;
}

.logo {
  display: block;
  max-width: 200px;
  /* padding-top: 30px; */
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}

@media (max-width: 991px) {
  h1 {
    font-size: 3rem;
  }

  p {
    font-size: 1.25rem;
  }

  .logo {
    max-width: 150px;
  }
}

@media (max-width: 575px) {
  h1 {
    font-size: 2rem;
  }

  p {
    font-size: 1rem;
  }

  .content {
    gap: 1rem;
  }
}

@media (max-width: 400px) {
  #mc_embed_signup .button {
    width: 100%;
  }
}
</style>
