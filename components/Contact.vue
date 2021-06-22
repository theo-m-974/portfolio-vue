<template>
  <div id="contact" class="section">
    <div class="contact">
      <h2>Contact</h2>

      <div class="contact-form">
        <form
          action="https://formsubmit.co/theo.moy4no@gmail.com"
          method="POST"
          name="emailForm"
        >
          <div class="error-message">
            <p v-show="!email.valid">Oh, please enter a valid email address.</p>
          </div>

          <fieldset>
            <div>
              <label class="label" for="name">Nom</label>
              <input
                id="name"
                v-model="name"
                type="text"
                name="name"
                required=""
              />
            </div>
            <div>
              <label class="label" for="email">Email</label>
              <input
                id="email"
                v-model="email.value"
                type="email"
                name="email"
                required=""
                :class="{ email, error: !email.valid }"
              />
            </div>
            <div>
              <label class="label" for="textarea">Message</label>
              <textarea
                id="textarea"
                v-model="message.text"
                class="message"
                name="textarea"
                required=""
                :maxlength="message.maxlength"
              ></textarea>
              <span class="counter"
                >{{ message.text.length }} / {{ message.maxlength }}</span
              >
            </div>
            <div>
              <input id="validate-button" type="submit" value="Envoyer" />
            </div>
          </fieldset>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Contact',

  data() {
    return {
      emailRegExp:
        // eslint-disable-next-line no-useless-escape
        /^[a-zA-Z0-9.!#$%&'*+\/=?^_`{|}~-]+@[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?(?:\.[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?)*$/,
      name: 'John Doe',
      email: {
        value: 'john@doe.com',
        valid: true,
      },
      message: {
        text: 'Message...',
        maxlength: 255,
      },
      submitted: false,
    }
  },

  watch: {
    // watching nested property
    'email.value'(value) {
      this.validate('email', value)
    },
  },

  methods: {
    // submit form handler
    submit() {
      this.submitted = true
    },
    // validate by type and value
    validate(type, value) {
      if (type === 'email') {
        this.email.valid = !!this.isEmail(value)
      }
    },
    // check for valid email adress
    isEmail(value) {
      return this.emailRegExp.test(value)
    },
    // check or uncheck all
    checkAll(event) {
      this.selection.features = event.target.checked ? this.features : []
    },
  },
}
</script>
