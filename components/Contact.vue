<template>
  <div id="contact" class="contact section">
    <h2>Contact</h2>

    <div class="contact-form">
      <form
        action="https://formsubmit.co/theo.moy4no@gmail.com"
        method="POST"
        name="emailForm"
      >
        <label for="contactName" required>Nom :</label>
        <input type="text" name="contactName" />
        <label for="contactEmail" required>Email :</label>
        <input type="email" name="contactEmail" />
        <label for="contactMessage" required>Message :</label>
        <textarea name="contactMessage" cols="30" rows="10"></textarea>
        <button type="submit">Envoyer</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Contact',

  data() {
    return {}
  },

  methods: {},
}
</script>
