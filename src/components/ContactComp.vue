<script></script>
<template>
  <section id="contact-a" class="text-center py-3">
    <div class="container">
      <h2 class="section-title">Contact Me</h2>
      <div class="bottom-line"></div>
      <p class="lead">Here is how you can reach me</p>
      <form name="contact" netlify method="POST" netlify-honeypot="bot-field" data-netlify="true">
        <div class="text-fields">
          <input
            type="hidden"
            name="subject"
            data-remove-prefix
            value="DRNSoftware Website Form Submission (%{submissionId})"
          />
          <input type="hidden" name="form-name" value="ask-question" />
          <!-- Honeypot field -->
          <div style="display: none">
            <label>
              Don’t fill this out if you're human:
              <input name="bot-field" />
            </label>
          </div>
          <input type="text" class="text-input name-input" placeholder="Name" name="name" />
          <input
            type="text"
            class="text-input subject-input"
            placeholder="Subject"
            name="subject"
          />
          <input
            type="email"
            class="text-input email-input"
            placeholder="Email Address"
            name="email"
            required
          />
          <input
            type="text"
            class="text-input phone-input"
            placeholder="Phone Number"
            name="phone"
          />
          <textarea
            class="text-input message-input"
            placeholder="Enter Message"
            name="message"
            required
          ></textarea>
        </div>
        <button type="submit" class="btn-dark">Submit</button>
      </form>
    </div>
  </section>

  <!-- Section B: Contact Info -->
  <section id="contact-b" class="py-2 bg-dark">
    <div class="container">
      <div class="contact-info">
        <p><i class="fas fa-envelope fa-2x"></i>Email: dylannel02@gmail.com</p>
      </div>
    </div>
  </section>

  <!-- Section C: TagLine -->
  <section id="contact-c" class="bg-main py-4">
    <div class="container">
      <h1>Let's Start your next Projects!</h1>
    </div>
  </section>
</template>
<style lang="scss">
@import '@/assets/_shared.scss';
</style>
